section .data
    welcome_msg db 'Selamat datang di Pemesanan Kopi!', 0
    menu_msg db 'Pilih jenis kopi (1. Kopi Hitam, 2. Kopi Susu): ', 0
    thanks_msg db 'Terima kasih atas pesanan Anda. Selamat menikmati kopi!', 0
    invalid_msg db 'Pilihan tidak valid. Silakan pilih 1 atau 2.', 0

section .bss
    choice resb 2 ; Buffer untuk menyimpan pilihan pengguna

section .text
    global _start

_start:
    ; Menampilkan pesan selamat datang
    mov eax, 4
    mov ebx, 1
    mov ecx, welcome_msg
    mov edx, 30
    int 0x80

    ; Menampilkan menu pilihan kopi
    mov eax, 4
    mov ebx, 1
    mov ecx, menu_msg
    mov edx, 46
    int 0x80

    ; Membaca pilihan pengguna
    mov eax, 3
    mov ebx, 0
    mov ecx, choice
    mov edx, 2
    int 0x80

    ; Mengonversi pilihan ke bilangan bulat
    mov eax, [choice]
    sub eax, '0'

    ; Memeriksa pilihan dan menampilkan pesan sesuai
    cmp eax, 1
    je black_coffee
    cmp eax, 2
    je milk_coffee
    jmp invalid_choice

black_coffee:
    ; Menampilkan pesan untuk kopi hitam
    mov eax, 4
    mov ebx, 1
    mov ecx, thanks_msg
    mov edx, 46
    int 0x80
    jmp exit_program

milk_coffee:
    ; Menampilkan pesan untuk kopi susu
    mov eax, 4
    mov ebx, 1
    mov ecx, thanks_msg
    mov edx, 46
    int 0x80
    jmp exit_program

invalid_choice:
    ; Menampilkan pesan kesalahan untuk pilihan tidak valid
    mov eax, 4
    mov ebx, 1
    mov ecx, invalid_msg
    mov edx, 46
    int 0x80

exit_program:
    ; Keluar dari program
    mov eax, 1
    xor ebx, ebx
    int 0x80
