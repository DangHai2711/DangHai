<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>nhap xuat so thap phan</h1>
  <p>  .model small</p>
.stack 100h <br>
.data <br>
 th1 db 'nhap so thap phan:$'<br>
 th2 db 10,13,'so thap phan vua nhap la:$'<br>
 x dw ? <br>
 y dw ? <br>
.code <br>
main proc <br>
    mov ax,@data <br>
    mov ds,ax <br>
    
    ;nhapso <br>
    mov ah,9 <br>
    lea dx,th1 <br>
    int 21h <br>
    
    call nhapso <br>
    
    ;hien thi <br>
    mov ah,9 <br>
    lea dx,th2 <br>
    int 21h  <br>
    call print  <br>
    
    mov ah,4 <br>
    int 21h  <br>
main endp <br>
;nhap so <br>
nhapso proc <br>
    mov x,0 <br>
    mov y,0 <br>
    mov bx,10 <br>
        nhap: <br>
        mov ah,1 <br>
        int 21h <br>
        cmp al,13 <br>
        je nhapxong <br>
        sub al,30h <br>
        xor ah,ah <br>
        mov y,ax <br>
        mov ax,x <br>
        mul bx <br>
        add ax,y <br>
        mov x,ax <br>
        jmp nhap <br>
        
        nhapxong: <br>
        ret <br>
nhapso endp <br>
print proc <br>
    mov ax,x <br>
    mov bx,10 <br>
    mov cx,0 <br>
    
    chia: <br>
    mov dx,0  <br>
    div bx <br>
    push dx <br>
    inc cx <br>
    cmp ax,0 <br>
    je hienthi <br>
    jmp chia <br>
    
    hienthi: <br>
    pop dx
    add dl,30h <br>
    mov ah,2 <br>
    int 21h <br>
    dec cx <br>
    jne hienthi <br>
    ret <br>
    
print endp <br>

</body>
</html>
