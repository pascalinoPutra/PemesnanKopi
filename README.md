.MODEL SMALL
.CODE

ORG 100h

START:
    JMP OrderCoffee
    kotak1  DB  "==========================================================",10d,13d,'$'
    Header1 DB  "|                    WELCOME TO COFFEE SHOP               ","|",10d,13d,'$'
    Header2 DB  "|                      DELEVASI COFFEE                   "," |",10d,13d,'$'
    Menu    DB  "| Menu               : Americano, Latte, Cappuccino","        |",10d,13d,'$'
    Size    DB  "| Size               : Regular, Large","                      |",10d,13d,'$'
    Sugar   DB  "| Sugar Level        : No sugar, Less sugar, Regular sugar"," |",10d,13d,'$'
    Topping DB  "| Topping            : None, Whipped cream, Caramel drizzle","|",10d,13d,'$'
    Harga   DB  "| Harga              : Rp.15,000, Rp.20,000 , Rp.23,000 ","   |",10d,13d,'$'
    kotak2  DB  "==========================================================",10d,13d,'$'

    .DATA
    menu1 DB "Americano|Rp.15,000$",10d,13d
    menu2 DB "Latte|Rp.20,000$",10d,13d
    menu3 DB "Cappuccino|Rp.23,000$",10d,13d

    pesan DB 20 DUP("$") ; Buffer untuk menyimpan pesanan

    prompt DB "Pilih menu (1-3): $"
    outputPrompt DB 10d,13d,"Anda memesan: $"
    invalidPrompt DB 10d,13d,"Pilihan tidak valid. Silakan pilih menu (1-3): $"

    SizePrompt DB 10d,13d,"Pilih size (1-2): $"
    Size1 DB "Regular$", 10d,13d
    Size2 DB "Large$",10d,13d

    SugarPrompt DB 10d,13d,"Pilih sugar level (1-3): $"
    Sugar1 DB "No sugar$",10d,13d 
    Sugar2 DB "Less sugar$",10d,13d
    Sugar3 DB "Regular sugar$",10d,13d

    ToppingPrompt DB 10d,13d,"Pilih topping (1-3): $"
    Topping1 DB "None$",10d,13d 
    Topping2 DB "Whipped cream$",10d,13d 
    Topping3 DB "Caramel drizzle$",10d,13d 


OrderCoffee:

    MOV AH,09H
    LEA DX,kotak1
    INT 21h

    LEA DX,Header1
    INT 21h

    LEA DX,Header2
    INT 21h

    LEA DX,Menu
    INT 21h

    LEA DX,Size
    INT 21h

    LEA DX,Sugar
    INT 21h

    LEA DX,Topping
    INT 21h

    LEA DX,Harga
    INT 21h

    LEA DX,kotak2
    INT 21h


MAIN PROC
; ??(size) ?? ?? 
MOV AH, 09h
LEA DX, prompt
INT 21h ; Menampilkan prompt untuk memilih menu  
 
input:
MOV AH, 01h
INT 21h ; Membaca input dari keyboard

CMP AL, '1'
JE menu1_selected 
CMP AL, '2'
JE menu2_selected
CMP AL, '3'
JE menu3_selected

; Jika pilihan tidak valid, tampilkan pesan kesalahan
MOV AH, 09h
LEA DX, invalidPrompt
INT 21h
JMP input

menu1_selected:
MOV AH, 09h
LEA DX, outputPrompt
INT 21h

; Menampilkan menu yang dipilih
MOV AH, 09h
LEA DX, menu1
INT 21h

JMP input_size

menu2_selected:
MOV AH, 09h
LEA DX, outputPrompt
INT 21h

; Menampilkan menu yang dipilih
MOV AH, 09h
LEA DX, menu2
INT 21h

JMP input_size

menu3_selected:
MOV AH, 09h
LEA DX, outputPrompt
INT 21h

; Menampilkan menu yang dipilih
MOV AH, 09h
LEA DX, menu3
INT 21h
   
JMP input_size

input_size:  

MOV AH, 09h
LEA DX, SizePrompt
INT 21h

MOV AH, 01h
INT 21h

CMP AL, '1'
JE size1_selected
CMP AL, '2'
JE size2_selected

; ???? ?? ??? ?? ?? ??? ?? ? ?? ?? ??
MOV AH, 09h
LEA DX, invalidPrompt
INT 21h
JMP input_size

size1_selected:
MOV AH, 09h
LEA DX, outputPrompt
INT 21h

; ??? ??(size) ??
MOV AH, 09h
LEA DX, Size1
INT 21h

JMP input_sugar

size2_selected:
MOV AH, 09h
LEA DX, outputPrompt
INT 21h

; ??? ??(size) ??
MOV AH, 09h
LEA DX, Size2
INT 21h

JMP input_sugar


; ??(sugar) ?? ??
input_sugar:
MOV AH, 09h
LEA DX, SugarPrompt
INT 21h

input_sugar_level:
MOV AH, 01h
INT 21h

CMP AL, '1'
JE sugar1_selected
CMP AL, '2'
JE sugar2_selected
CMP AL, '3'
JE sugar3_selected

; ???? ?? ??? ?? ?? ??? ?? ? ?? ?? ??
MOV AH, 09h
LEA DX, invalidPrompt
INT 21h
JMP input_sugar_level

sugar1_selected:
MOV AH, 09h
LEA DX, outputPrompt
INT 21h

; ??? ??(sugar) ??
MOV AH, 09h
LEA DX, Sugar1
INT 21h

JMP input_topping

sugar2_selected:
MOV AH, 09h
LEA DX, outputPrompt
INT 21h

; ??? ??(sugar) ??
MOV AH, 09h
LEA DX, Sugar2
INT 21h

JMP input_topping

sugar3_selected:
MOV AH, 09h
LEA DX, outputPrompt
INT 21h

; ??? ??(sugar) ??
MOV AH, 09h
LEA DX, Sugar3
INT 21h

JMP input_topping


; ??(topping) ?? ??
input_topping:
MOV AH, 09h
LEA DX, ToppingPrompt
INT 21h

input_topping_option:
MOV AH, 01h
INT 21h

CMP AL, '1'
JE topping1_selected
CMP AL, '2'
JE topping2_selected
CMP AL, '3'
JE topping3_selected

; ???? ?? ??? ?? ?? ??? ?? ? ?? ?? ??
MOV AH, 09h
LEA DX, invalidPrompt
INT 21h
JMP input_topping_option

topping1_selected:
MOV AH, 09h
LEA DX, outputPrompt
INT 21h

; ??? ??(topping) ??
MOV AH, 09h
LEA DX, Topping1
INT 21h

JMP exit

topping2_selected:
MOV AH, 09h
LEA DX, outputPrompt
INT 21h

; ??? ??(topping) ??
MOV AH, 09h
LEA DX, Topping2
INT 21h

JMP exit

topping3_selected:
MOV AH, 09h
LEA DX, outputPrompt
INT 21h

; ??? ??(topping) ??
MOV AH, 09h
LEA DX, Topping3
INT 21h

exit:
    INT 20h  
    

MAIN ENDP
END MAIN

    

END START

