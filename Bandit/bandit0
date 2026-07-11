# Bandit Level 0 → Level 1

## Goal | Amaç

**EN:** Connect to the Bandit server using SSH and find the password for Level 1.

**TR:** SSH kullanarak Bandit sunucusuna bağlanmak ve Level 1'in şifresini bulmak.

---

## Connection | Bağlantı

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

### Explanation (EN)

- **ssh** → Secure Shell. It is used to connect to a remote Linux server securely.
- **bandit0** → The username used to log into the server.
- **@** → Separates the username from the server address.
- **bandit.labs.overthewire.org** → The hostname of the Bandit server.
- **-p 2220** → Specifies the port number. SSH normally uses port **22**, but Bandit uses **2220**, so we have to specify it.

### Açıklama (TR)

- **ssh** → Uzak bir Linux sunucusuna güvenli şekilde bağlanmamızı sağlayan komuttur.
- **bandit0** → Sunucuya giriş yapmak için kullanılan kullanıcı adıdır.
- **@** → Kullanıcı adı ile sunucu adresini birbirinden ayırır.
- **bandit.labs.overthewire.org** → Bağlanacağımız Bandit sunucusunun adresidir.
- **-p** → Bağlanılacak portu belirtmek için kullanılır.
- **2220** → Bandit'in kullandığı SSH portudur. Normalde SSH varsayılan olarak 22 numaralı portu kullanır ancak burada 2220 kullanıldığı için bunu özellikle belirtmemiz gerekiyor.

---

After running the command, the server asked for the password.

Komutu çalıştırdıktan sonra sunucu benden bir şifre istedi. İlk level için OverTheWire sitesinde verilen başlangıç şifresini girdim ve sisteme giriş yaptım.

---

## Looking Around | Dosyaları Kontrol Etme

```bash
ls -l
```

### Explanation (EN)

- **ls** lists the files and directories in the current location.
- **-l** displays them in a long format, including permissions, owner, size and modification date.

### Açıklama (TR)

- **ls** bulunduğumuz dizindeki dosya ve klasörleri listeler.
- **-l** parametresi ise bunları daha ayrıntılı gösterir. Dosya izinleri, sahibi, boyutu ve oluşturulma tarihi gibi bilgiler de görüntülenir.

The output showed a file named:

```
readme
```

---

## Reading the File | Dosyayı Okuma

```bash
cat readme
```

### Explanation (EN)

- **cat** prints the contents of a file directly in the terminal.

### Açıklama (TR)

- **cat** komutu bir dosyanın içeriğini terminal ekranına yazdırmak için kullanılır.

The file contained the password for **Bandit Level 1**.

Dosyanın içinde Bandit Level 1'e giriş yapmak için gerekli olan şifre bulunuyordu.

---

## Commands Used

| Command | Description |
|----------|-------------|
| `ssh` | Connect to a remote server securely. |
| `ls -l` | List files with detailed information. |
| `cat` | Display the contents of a file. |

---

## What I Learned

- How to connect to a remote Linux machine using SSH.
- How to specify a custom SSH port.
- How to list files in the current directory.
- How to read a file from the terminal.
