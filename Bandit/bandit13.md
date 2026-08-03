# Bandit Level 13 → Level 14

## English

### Goal

Log in as **Bandit Level 14** using the provided SSH private key and retrieve the password for the next level.

---

### Challenge Hint

The challenge provides an **SSH private key** (`sshkey.private`) instead of a password. This key must be used to authenticate as **bandit14**.

---

### Verifying the Private Key

First, I listed the files in the home directory to verify that the private key existed.

```bash
ls -l
```

Then I checked the file type.

```bash
file sshkey.private
```

Output:

```text
sshkey.private: OpenSSH private key
```

This confirmed that the file was an OpenSSH private key that could be used for authentication.

---

### Copying the Private Key to My Local Machine

Because OverTheWire blocks SSH connections from `localhost`, I needed to connect directly from my own machine.

First, I displayed the contents of the key:

```bash
cat sshkey.private
```

Then, on my Kali Linux machine, I created a new file using the Nano text editor.

```bash
nano sshkey.private
```

I pasted the copied key into the editor.

#### Saving the File with Nano

After pasting the key:

- Press **Ctrl + O** to save the file.
- Press **Enter** to confirm the filename.
- Press **Ctrl + X** to exit Nano.

---

### Fixing File Permissions

When I first attempted to connect, SSH displayed the following warning:

```text
WARNING: UNPROTECTED PRIVATE KEY FILE!
Permissions 0644 for 'sshkey.private' are too open.
```

SSH refuses to use private keys that are accessible by other users.

To secure the key, I changed its permissions.

```bash
chmod 600 sshkey.private
```

Then I verified the new permissions.

```bash
ls -l sshkey.private
```

Expected output:

```text
-rw------- 1 user user ... sshkey.private
```

Now the private key could be used safely.

---

### Logging in as Bandit14

Finally, I connected to the Bandit server using the private key.

```bash
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```

### Explanation

- **ssh** → Connects to a remote system using SSH.
- **-i sshkey.private** → Specifies the private key used for authentication.
- **-p 2220** → Connects to SSH port 2220.
- **bandit14@bandit.labs.overthewire.org** → Username and remote host.

Since the correct private key was provided, SSH authenticated automatically without asking for the Level 14 password.

---

### Retrieving the Password

After successfully logging in as **bandit14**, I displayed the password for the next level.

```bash
cat /etc/bandit_pass/bandit14
```

The output is the password required to access **Bandit Level 15**.

---

### Commands Used

| Command | Description |
|---------|-------------|
| `ls -l` | List files with detailed information. |
| `file` | Identify the type of a file. |
| `cat` | Display the contents of a file. |
| `nano` | Create or edit a text file in the terminal. |
| `chmod 600` | Restrict file permissions so only the owner can read and write. |
| `ssh -i` | Authenticate using a private SSH key instead of a password. |

---

### What I Learned

- How SSH public key authentication works.
- How to identify an OpenSSH private key.
- How to use Nano to create and edit files.
- Why private key permissions must be restricted.
- How to authenticate to a remote server using an SSH private key.

---

# Türkçe

## Amaç

Verilen **SSH private key** dosyasını kullanarak **bandit14** kullanıcısı olarak giriş yapmak ve bir sonraki seviyenin şifresini elde etmek.

---

## Verilen İpucu

Bu seviyede parola yerine **`sshkey.private`** adlı bir **SSH private key** verilmiştir. Bu anahtar kullanılarak **bandit14** kullanıcısına giriş yapılması beklenmektedir.

---

## Private Key Dosyasını Kontrol Etme

İlk olarak home dizinindeki dosyaları listeleyerek private key dosyasının bulunduğunu doğruladım.

```bash
ls -l
```

Ardından dosyanın gerçekten bir SSH anahtarı olup olmadığını kontrol ettim.

```bash
file sshkey.private
```

Çıktı:

```text
sshkey.private: OpenSSH private key
```

Bu çıktı, dosyanın bir **OpenSSH private key** olduğunu doğruladı.

---

## Private Key'i Kendi Bilgisayarıma Aktarma

OverTheWire, `localhost` üzerinden yapılan SSH bağlantılarını engellediği için bağlantıyı kendi Kali Linux makinemden gerçekleştirmem gerekiyordu.

Öncelikle anahtarın içeriğini görüntüledim.

```bash
cat sshkey.private
```

Daha sonra Kali Linux üzerinde Nano editörü ile yeni bir dosya oluşturdum.

```bash
nano sshkey.private
```

Kopyaladığım private key içeriğini bu dosyanın içerisine yapıştırdım.

### Nano ile Dosyayı Kaydetme

Dosyayı kaydetmek için:

- **Ctrl + O** tuşlarına bastım.
- Dosya adını onaylamak için **Enter** tuşuna bastım.
- Nano'dan çıkmak için **Ctrl + X** tuşlarını kullandım.

---

## Dosya İzinlerini Düzenleme

İlk bağlantı denememde SSH aşağıdaki uyarıyı verdi:

```text
WARNING: UNPROTECTED PRIVATE KEY FILE!
Permissions 0644 for 'sshkey.private' are too open.
```

SSH, güvenlik nedeniyle herkes tarafından okunabilen private key dosyalarını kullanmaz.

Bu nedenle dosyanın izinlerini aşağıdaki komutla değiştirdim.

```bash
chmod 600 sshkey.private
```

Ardından izinleri kontrol ettim.

```bash
ls -l sshkey.private
```

Beklenen çıktı:

```text
-rw------- 1 user user ... sshkey.private
```

Bu sayede private key yalnızca dosya sahibi tarafından okunabilir ve yazılabilir hale geldi.

---

## Bandit14 Kullanıcısı Olarak Giriş Yapma

Son olarak private key'i kullanarak Bandit sunucusuna bağlandım.

```bash
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```

### Açıklama

- **ssh** → Uzak bir sisteme SSH bağlantısı kurar.
- **-i sshkey.private** → Kimlik doğrulama için kullanılacak private key dosyasını belirtir.
- **-p 2220** → SSH bağlantısının 2220 portu üzerinden yapılacağını belirtir.
- **bandit14@bandit.labs.overthewire.org** → Bağlanılacak kullanıcı ve sunucu adresidir.

Doğru private key kullanıldığı için parola sorulmadan **bandit14** kullanıcısı olarak giriş yapılabildi.

---

## Sonraki Seviyenin Şifresini Alma

Giriş yaptıktan sonra bir sonraki seviyenin şifresini görüntüledim.

```bash
cat /etc/bandit_pass/bandit14
```

Komutun çıktısı, **Bandit Level 15** için kullanılacak paroladır.

---

## Kullanılan Komutlar

| Komut | Açıklama |
|--------|----------|
| `ls -l` | Dosyaları ayrıntılı şekilde listeler. |
| `file` | Dosyanın gerçek türünü belirler. |
| `cat` | Dosyanın içeriğini görüntüler. |
| `nano` | Terminal üzerinden dosya oluşturur veya düzenler. |
| `chmod 600` | Dosya izinlerini yalnızca sahibinin okuyup yazabileceği şekilde düzenler. |
| `ssh -i` | Private key kullanarak SSH bağlantısı kurar. |

---

## Ne Öğrendim

- SSH anahtar tabanlı kimlik doğrulamanın nasıl çalıştığını.
- Bir OpenSSH private key dosyasını nasıl doğrulayacağımı.
- Nano editörü ile terminal üzerinden dosya oluşturmayı ve kaydetmeyi.
- SSH private key dosyalarında doğru izinlerin neden önemli olduğunu.
- Private key kullanarak parola girmeden SSH bağlantısı kurmayı.
