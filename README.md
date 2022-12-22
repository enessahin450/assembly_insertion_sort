# assembly_insertion_sort
<br>Assembly dili ile dizideki elemanları küçükten büyüğe doğru sıralamak.
<br>
<br>org 100h
<br>mov bx,0200h &emsp;&emsp;&emsp;&emsp;&emsp;   ;dizi adresi
<br>
<br>mov byte ptr [bx],55h    &emsp;&emsp;   ;dizideki elemanlar
<br>mov byte ptr [bx+1],62h
<br>mov byte ptr [bx+2],57h
<br>mov byte ptr [bx+3],33h
<br>mov byte ptr [bx+4],31h
<br>mov byte ptr [bx+5],29h
<br>mov byte ptr [bx+6],23h
<br>mov byte ptr [bx+7],44h
<br>mov byte ptr [bx+8],42h
<br>mov byte ptr [bx+9],39h
<br>
<br>mov si,0200h    &emsp;&emsp;       ;verilmis dizi icin si registeri 0200h adrese ata.
<br>mov di,0400h    &#160;&#160;&#160;&#160;&#160;&#160;      ;siralanmis dizi icin di registeri 0400h adrese ata.
<br>
<br>alg_loop:
<br>mov cl,[si]  &emsp;&emsp;          ;si registeri cl'ye kopyala.
<br>mov ch,0     &emsp;&emsp;          ;ch'i sifirla.
<br>mov bx,di    &emsp;&emsp;          ;di registerini bx registerina ata.
<br>dec bx       &emsp;&emsp;&emsp;           ;bx registerini bir azalt
<br>
<br>kaydirmaloop:
<br>cmp cl,[bx]    &emsp;&emsp;        ;bx ve cl registerlarini karsilastir
<br>jae skip       &emsp;&emsp;&emsp;        ;cl bx'den buyuk veya esitse skipe atla.cl bx'den kucukse devam et.
<br>
<br>mov ax,[bx]    &emsp;&emsp;&emsp;         ;bx'i ax'e kopyala.
<br>mov [bx+1],ax  &emsp;&emsp;        ;ax registeri bx+1 registerina ata.
<br> &emsp;
<br>dec bx          &emsp;&emsp;&emsp; &emsp; &emsp; &emsp;        ;bx'i bir azalt.
<br>jmp kaydirmaloop &emsp;&emsp;      ;kaydirma loop dongusune don ve adimlari tekrarla.
<br> &emsp;
<br>skip: &emsp;
<br>mov [bx+1],cl   &emsp;&emsp;       ;cl registeri bx+1'e kopyala.
<br>inc si          &emsp;&emsp;&emsp; &emsp; &emsp;        ;si registeri bir artir.
<br>inc di          &emsp;&emsp;&emsp; &emsp;&emsp;         ;di registeri bir artir.
<br>cmp di,040ah    &emsp;&emsp;       ;di registeri 4010 degerine geldiginde donguden cik.
<br>jb alg_loop     &emsp;&emsp;&emsp;        ;eger di=4010 degilse alg_loop dongusune tekrar don.
<br> &emsp;
<br>mov bx,0200h    &emsp;&emsp;       ;burdan sonraki adimlar ise 4000'da olusan dizimizi yine eski adresine yani 0200'e kopyalariz.
<br>mov cx,0ah     
<br>mov di,0400h
<br>kopyala:
<br>mov ax,[di]
<br>mov [bx],ax
<br>inc bx
<br>inc di
<br>loop kopyala
