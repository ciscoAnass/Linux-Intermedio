# BASIC

- Paquetes para instalar
> sudo apt install cups
> sudo apt install cups-pdf


# ANadir una nueva impreosra con comandos

root@debian:~# lpadmin -p HANOI -E \ 
> -v cups-pdf:/ \ 
> -P /root/Brother-HL-1470N-Postscript-Brother.ppd  

 
