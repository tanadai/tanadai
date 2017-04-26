# LEVEL2:Programmers Assemble
以下のアセンブリ言語のソースコードを読み,XXXXXXXになにが当てはまるのかを推測する問題.
````
.global main

main:
    mov $XXXXXXX, %eax    	//%eax=XXXXXXX
    mov $0, %ebx			//%ebx=0x0
    mov $0x8, %ecx			//%ecx=0x8
loop:
    test %eax, %eax			//if(%eax==0)
    jz fin					//goto fin
    add %ecx, %ebx			//%ebx=%ebx+%ecx
    dec %eax				//%eax--
    jmp loop
fin:
    cmp $0xf5f8, %ebx		//if(%ebx==0xf5f8)
    je good					//goto good
    mov $0, %eax			//%eax=0
    jmp end					//goto end
good:
    mov $1, %eax			//%eax=1
end:
    ret

````
注意点としてはこのコードはGAS文法で書かれているものであり, addなどの結果は第２引数に格納される.
loopが繰り返されるたびに%eaxがデクリメントされていることからループカウンタだと考えられる.
%ebx, %ecxには0, 8が格納されているためループのたびに8を加算する. ループから抜けると加算結果が0xf5f8(10進数で62968)と比較されるため8で割った0x1ebf(10進数で7871)回繰り返せば良い.
よって0x1ebfがflagとなる.
