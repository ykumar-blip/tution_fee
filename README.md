%macro print_text 2
    mov ecx, %1
    mov edx, %2
    call print_proc
%endmacro

section .data


    title db 10, "===== STUDENT INFO =====", 10
    title_len equ $-title

    course_title db 10, "===== COURSES AND SCHEDULE =====", 10
    course_title_len equ $-course_title

    tuition_title db 10, "===== TUITION FEE CALCULATOR =====", 10
    tuition_title_len equ $-tuition_title

    info_title db 10, "===== STUDENT INFORMATION =====", 10
    info_title_len equ $-info_title

    compute_title db 10, "===== TUITION FEE COMPUTATION =====", 10
    compute_title_len equ $-compute_title


    p_status db "Enter Enrollment Status: "
    p_status_len equ $-p_status

    p_number db "Enter Student Number: "
    p_number_len equ $-p_number

    p_name db "Enter Student Name: "
    p_name_len equ $-p_name

    p_program db "Enter Program: "
    p_program_len equ $-p_program


    c1 db "CCS0021  Information Management (LEC) | 2 units | T | 16:00-18:40 | Online",10
    c1_len equ $-c1

    c2 db "CCS0021L Information Management (LAB) | 1 unit  | F | 16:00-18:50 | Online",10
    c2_len equ $-c2

    c3 db "CS0001   Discrete Structures 1 | 3 units | S/W | 15:00-16:50 | E710",10
    c3_len equ $-c3

    c4 db "CS0003   Computer Systems & Architecture | 2 units | F | 10:00-12:40 | Online",10
    c4_len equ $-c4

    c5 db "CS0003L  Computer Systems & Architecture (LAB) | 1 unit | TH | 10:00-12:50 | E610",10
    c5_len equ $-c5

    c6 db "CS0016   Network and Communications 2A | 3 units | T/TH | 13:00-14:50 | Online/F1101",10
    c6_len equ $-c6

    c7 db "CS0070   Object Oriented Programming | 2 units | F | 13:00-15:40 | Online",10
    c7_len equ $-c7

    c8 db "CS0070L  Object Oriented Programming (LAB) | 1 unit | M | 13:00-15:00 | E609",10
    c8_len equ $-c8

    c9 db "CS0081   Introduction to Cybersecurity | 3 units | F/T | 07:00-08:50 | Online",10
    c9_len equ $-c9

    c10 db "GED0073  GE Elective 2 | 3 units | M/TH | 17:00-18:50 | F809",10
    c10_len equ $-c10

    schedule_end db "Total Units: 21",10
    schedule_end_len equ $-schedule_end


    p1 db "Enter Tuition Fee: P"
    p1_len equ $-p1

    p2 db "Enter Miscellaneous Fee: P"
    p2_len equ $-p2

    p3 db "Enter International Student Fee: P"
    p3_len equ $-p3

    p4 db "Enter ID Validation Fee: P"
    p4_len equ $-p4

    p5 db "Enter Total Laboratory Fees: P"
    p5_len equ $-p5

    p6 db "Enter Specialized Network Fee: P"
    p6_len equ $-p6


    label_status db "Enrollment Status: "
    label_status_len equ $-label_status

    label_number db "Student Number: "
    label_number_len equ $-label_number

    label_name db "Student Name: "
    label_name_len equ $-label_name

    label_program db "Program: "
    label_program_len equ $-label_program


    o1 db "Tuition Fee: P"
    o1_len equ $-o1

    o2 db "Miscellaneous Fee: P"
    o2_len equ $-o2

    o3 db "International Student Fee: P"
    o3_len equ $-o3

    o4 db "ID Validation Fee: P"
    o4_len equ $-o4

    o5 db "Laboratory Fees: P"
    o5_len equ $-o5

    o6 db "Specialized Network Fee: P"
    o6_len equ $-o6

    total_msg db "Total Assessment: P"
    total_len equ $-total_msg

    down_msg db "Down Payment (40%): P"
    down_len equ $-down_msg

    mid_msg db "Midterm Payment (30%): P"
    mid_len equ $-mid_msg

    final_msg db "Final Payment (30%): P"
    final_len equ $-final_msg

    newline db 10
    dot db "."

section .bss

; Student information buffers
    status_buf resb 64
    number_text resb 64
    name_buf resb 64
    program_buf resb 64

    status_len resd 1
    number_len resd 1
    name_len resd 1
    program_len resd 1

; Numeric input and display buffers
    input_buf resb 32
    number_buf resb 12
    fraction_buf resb 2

; Fee variables
    tuition resd 1
    misc_fee resd 1
    international_fee resd 1
    id_fee resd 1
    lab_fee resd 1
    network_fee resd 1
    total resd 1

    whole_part resd 1
    fraction_part resd 1

section .text
    global _start

_start:



    print_text title, title_len

    print_text p_status, p_status_len
    mov ecx, status_buf
    mov edx, 63
    call input_string_proc
    mov [status_len], eax

    print_text p_number, p_number_len
    mov ecx, number_text
    mov edx, 63
    call input_string_proc
    mov [number_len], eax

    print_text p_name, p_name_len
    mov ecx, name_buf
    mov edx, 63
    call input_string_proc
    mov [name_len], eax

    print_text p_program, p_program_len
    mov ecx, program_buf
    mov edx, 63
    call input_string_proc
    mov [program_len], eax



    print_text course_title, course_title_len

    print_text c1, c1_len
    print_text c2, c2_len
    print_text c3, c3_len
    print_text c4, c4_len
    print_text c5, c5_len
    print_text c6, c6_len
    print_text c7, c7_len
    print_text c8, c8_len
    print_text c9, c9_len
    print_text c10, c10_len
    print_text schedule_end, schedule_end_len



    print_text tuition_title, tuition_title_len

    print_text p1, p1_len
    call input_proc
    mov [tuition], eax

    print_text p2, p2_len
    call input_proc
    mov [misc_fee], eax

    print_text p3, p3_len
    call input_proc
    mov [international_fee], eax

    print_text p4, p4_len
    call input_proc
    mov [id_fee], eax

    print_text p5, p5_len
    call input_proc
    mov [lab_fee], eax

    print_text p6, p6_len
    call input_proc
    mov [network_fee], eax



    print_text info_title, info_title_len

    print_text label_status, label_status_len
    mov ecx, status_buf
    mov edx, [status_len]
    call print_proc
    call print_newline

    print_text label_number, label_number_len
    mov ecx, number_text
    mov edx, [number_len]
    call print_proc
    call print_newline

    print_text label_name, label_name_len
    mov ecx, name_buf
    mov edx, [name_len]
    call print_proc
    call print_newline

    print_text label_program, label_program_len
    mov ecx, program_buf
    mov edx, [program_len]
    call print_proc
    call print_newline



    print_text compute_title, compute_title_len

    print_text o1, o1_len
    mov eax, [tuition]
    call print_num
    call print_newline

    print_text o2, o2_len
    mov eax, [misc_fee]
    call print_num
    call print_newline

    print_text o3, o3_len
    mov eax, [international_fee]
    call print_num
    call print_newline

    print_text o4, o4_len
    mov eax, [id_fee]
    call print_num
    call print_newline

    print_text o5, o5_len
    mov eax, [lab_fee]
    call print_num
    call print_newline

    print_text o6, o6_len
    mov eax, [network_fee]
    call print_num
    call print_newline

    mov eax, [tuition]
    add eax, [misc_fee]
    add eax, [international_fee]
    add eax, [id_fee]
    add eax, [lab_fee]
    add eax, [network_fee]
    mov [total], eax

    print_text total_msg, total_len
    mov eax, [total]
    call print_num
    call print_newline



    print_text down_msg, down_len
    mov eax, [total]
    imul eax, 40
    call print_money
    call print_newline

    print_text mid_msg, mid_len
    mov eax, [total]
    imul eax, 30
    call print_money
    call print_newline

    print_text final_msg, final_len
    mov eax, [total]
    imul eax, 30
    call print_money
    call print_newline

;

    mov eax, 1
    xor ebx, ebx
    int 0x80



print_proc:
    push ebx
    mov eax, 4
    mov ebx, 1
    int 0x80
    pop ebx
    ret



input_string_proc:
    push ebx
    push esi

    mov esi, ecx

    mov eax, 3
    mov ebx, 0
    int 0x80

    test eax, eax
    jle .empty

    mov ecx, eax
    dec ecx

    cmp byte [esi + ecx], 10
    jne .no_newline

    mov byte [esi + ecx], 0
    mov eax, ecx
    jmp .input_done

.no_newline:
    mov byte [esi + eax], 0
    jmp .input_done

.empty:
    xor eax, eax

.input_done:
    pop esi
    pop ebx
    ret



input_proc:
    push ebx
    push ecx
    push edx
    push esi

    mov eax, 3
    mov ebx, 0
    mov ecx, input_buf
    mov edx, 32
    int 0x80

    xor eax, eax
    mov esi, input_buf

.parse:
    movzx edx, byte [esi]

    cmp dl, 10
    je .done
    cmp dl, 13
    je .done
    cmp dl, '0'
    jb .done
    cmp dl, '9'
    ja .done

    imul eax, eax, 10
    sub edx, '0'
    add eax, edx

    inc esi
    jmp .parse

.done:
    pop esi
    pop edx
    pop ecx
    pop ebx
    ret



print_num:
    push ebx
    push ecx
    push edx
    push edi

    mov edi, number_buf + 11
    mov byte [edi], 0
    mov ebx, 10

    test eax, eax
    jnz .convert

    dec edi
    mov byte [edi], '0'
    jmp .output

.convert:
    xor edx, edx
    div ebx

    add dl, '0'
    dec edi
    mov [edi], dl

    test eax, eax
    jnz .convert

.output:
    mov ecx, edi
    mov edx, number_buf + 11
    sub edx, edi
    call print_proc

    pop edi
    pop edx
    pop ecx
    pop ebx
    ret



print_money:
    push ebx
    push ecx
    push edx

    xor edx, edx
    mov ebx, 100
    div ebx

    mov [whole_part], eax
    mov [fraction_part], edx

    mov eax, [whole_part]
    call print_num

    mov eax, [fraction_part]
    xor edx, edx
    mov ebx, 10
    div ebx

    add al, '0'
    mov [fraction_buf], al

    add dl, '0'
    mov [fraction_buf + 1], dl

    print_text dot, 1
    print_text fraction_buf, 2

    pop edx
    pop ecx
    pop ebx
    ret


print_newline:
    print_text newline, 1
    ret
