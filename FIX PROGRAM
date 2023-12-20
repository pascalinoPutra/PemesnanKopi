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
    menu1 DB "Americano|Rp.15,000$", 0
    menu2 DB "Latte|Rp.20,000$", 0
    menu3 DB "Cappuccino|Rp.23,000$", 0
    
    pesan DB 20 DUP("$") ; Buffer untuk menyimpan pesanan
    
    prompt DB "Pilih menu (1-3): $"
    outputPrompt DB 10d,13d,"Anda memesan: $"
    invalidPrompt DB 10d,13d,"Pilihan tidak valid. Silakan pilih menu (1-3): $"    
    

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
    MOV AX, @DATA
    MOV DS, AX

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

    JMP exit

menu2_selected:
    MOV AH, 09h
    LEA DX, outputPrompt
    INT 21h

    ; Menampilkan menu yang dipilih
    MOV AH, 09h
    LEA DX, menu2
    INT 21h

    JMP exit

menu3_selected:
    MOV AH, 09h
    LEA DX, outputPrompt
    INT 21h

    ; Menampilkan menu yang dipilih
    MOV AH, 09h
    LEA DX, menu3
    INT 21h

exit:
    INT 20h

MAIN ENDP
END MAIN

    

END START
