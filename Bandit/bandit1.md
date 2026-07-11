# Bandit Level 1 → Level 2

## Goal | Amaç

**EN:** Find the password for Level 2, which is stored in a file called **-** located in the home directory.

**TR:** Ana dizinde bulunan ve adı **-** (tire) olan dosyanın içindeki Level 2 şifresini bulmak.

---

## Connection | Bağlantı

```
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

## Looking Around | Dosyaları Kontrol Etme

```
ls -l

```
Explanation (EN)
ls -l → Lists the files in long format. The output shows a file whose name is exactly -.

Açıklama (TR)
ls -l → Dosyaları ayrıntılı şekilde listeler. Çıktıda ismi sadece - (tire) olan bir dosya olduğunu gördük.

Checking File Type | Dosya Türünü Kontrol Etme

```
file ./-
```

Explanation (EN)
file → Determines the type of a file based on its magic bytes rather than its extension.

./- → We specify ./ before the filename to tell Linux that - is a file path, not a command argument/option.

Açıklama (TR)
**file** → Bir dosyanın uzantısına bakmaksızın, yapısını inceleyerek gerçekte ne tür bir dosya olduğunu söyler.

./- → Linux terminalinde - işareti parametrelerle karıştırılabileceği için, bunun bulunduğumuz dizindeki (./) bir dosya olduğunu bu şekilde belirtiriz.

The output confirmed it is an ASCII text file. / Çıktı, bunun bir düz metin dosyası olduğunu doğruladı.

## Reading the File | Dosyayı Okuma

```
cat ./-
```

Explanation (EN)
cat → Prints the contents of the file. Similar to the file command, we must use ./- to prevent the shell from misinterpreting the hyphen character.

Açıklama (TR)
**cat** → Dosyanın içeriğini ekrana yazdırır. Tıpkı file komutunda olduğu gibi, terminalin kafasının karışmasını önlemek için dosya adını ./- şeklinde belirterek okuma işlemini gerçekleştiririz.

The file contained the password for Bandit Level 2.
Dosyanın içinde Bandit Level 2'ye giriş yapmak için gerekli olan uzun şifre bulunuyordu.



