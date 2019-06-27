# Criando a "Jaula"

Vamos criar um ambiente para trabalhar de forma isolada, tudo que for feito
nele não vai afetar o sistema operacianal principal. Esse ambiente é chamado
de "Jaula".

Para criar a "jaula" instale primeiro o debootstrap:

```
apt-get install debootstrap
```

Vamos usar o debootstrap para criar um sistema básico Debian a partir do zero.
Neste caso, vamos criar um sistema Sid(unstable) montado na raiz do
sistema(`/` diretório root) chamado `jaula-sid`.

```
debootstrap sid /jaula-sid http://ftp.br.debian.org/debian
```

Para entrar na "jaula" que acabamos de criar, use o `chroot` que vai trocar o
nosso diretório raíz(root) para o da "jaula"

```
 chroot /jaula-sid
```

Agora temos que montar um dispositivo `proc` para que ela funcione
corretamente:

```
mount proc /proc -t proc
```

## Personalizando o .bashrc
