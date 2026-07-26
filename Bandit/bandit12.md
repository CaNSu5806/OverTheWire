# Bandit Level 12 → Level 13

## 🇬🇧 English

### Goal

Find the password for **Bandit Level 13**.

---

### Challenge Hint

The challenge states that the password is stored in `data.txt`, which is a **hexdump of a file** that has been **repeatedly compressed**.

---

### Preparing the Workspace

Since multiple files would be extracted during the process, I first created a temporary working directory.

```bash
mktemp -d
cd /tmp/<temporary_directory>
cp ~/data.txt .
```

This keeps the home directory clean and prevents unnecessary temporary files from accumulating.

---

### Restoring the Original File

Although the file was named `data.txt`, it actually contained a hexadecimal dump of another file.

To restore the original binary file, I used:

```bash
xxd -r data.txt > data
```

### Explanation

- **xxd** → Creates or reverses hexadecimal dumps.
- **-r** → Reverses a hexadecimal dump back into its original binary form.
- **> data** → Saves the recovered binary data into a file named `data`.

---

### Identifying Each Layer

After restoring the binary file, I repeatedly checked its type using:

```bash
file data
```

The `file` command identifies a file based on its contents rather than its extension.

Depending on the reported file type, I renamed the file with the correct extension and extracted it using the appropriate tool.

Examples:

```bash
mv data data.gz
gzip -d data.gz
```

```bash
mv data data.bz2
bzip2 -d data.bz2
```

```bash
mv data data.tar
tar -xf data.tar
```

This process was repeated several times because each extracted file contained another compressed file, similar to a **Matryoshka doll**.

Eventually, the final text file containing the password was revealed.

---

### Commands Used

| Command | Description |
|---------|-------------|
| `mktemp -d` | Create a temporary directory. |
| `cd` | Change the current directory. |
| `cp` | Copy a file. |
| `xxd -r` | Convert a hexadecimal dump back into binary data. |
| `file` | Identify the file type. |
| `mv` | Rename a file. |
| `gzip -d` | Extract a gzip-compressed file. |
| `bzip2 -d` | Extract a bzip2-compressed file. |
| `tar -xf` | Extract a tar archive. |

---

### What I Learned

- How to work safely in a temporary directory.
- How to restore binary data from a hexadecimal dump.
- How to identify unknown file types using the `file` command.
- Why file extensions do not always reflect the actual file type.
- How to extract nested compressed files by repeatedly identifying and decompressing each layer.

---

# 🇹🇷 Türkçe

## Amaç

**Bandit Level 13** için gerekli şifreyi bulmak.

---

## Verilen İpucu

Challenge'da şifrenin, **bir dosyanın hexadecimal (hex dump) çıktısını** içeren ve **birden fazla kez sıkıştırılmış** `data.txt` dosyasında bulunduğu belirtiliyordu.

---

## Çalışma Ortamını Hazırlama

Çözüm sırasında birçok dosya oluşturulacağı için öncelikle geçici bir çalışma dizini oluşturdum.

```bash
mktemp -d
cd /tmp/<gecici_dizin>
cp ~/data.txt .
```

Bu sayede home dizinim gereksiz dosyalarla dolmadı ve tüm işlemleri güvenli bir çalışma alanında gerçekleştirebildim.

---

## Orijinal Dosyayı Geri Getirme

Dosyanın adı `data.txt` olmasına rağmen aslında bir dosyanın **hex dump** çıktısını içeriyordu.

Orijinal binary dosyayı geri oluşturmak için şu komutu kullandım:

```bash
xxd -r data.txt > data
```

### Açıklama

- **xxd** → Hexadecimal dump oluşturmak veya tersine çevirmek için kullanılır.
- **-r** → Hex dump verisini tekrar orijinal binary formata dönüştürür.
- **> data** → Oluşturulan binary veriyi `data` adlı yeni dosyaya kaydeder.

---

## Katmanları Açma

Binary dosya oluşturulduktan sonra her aşamada dosyanın türünü öğrenmek için şu komutu kullandım:

```bash
file data
```

`file` komutu, dosya uzantısına değil dosyanın içeriğine bakarak gerçek dosya türünü belirler.

Komutun sonucuna göre dosyayı uygun uzantıyla yeniden adlandırıp doğru araçla açtım.

Örneğin:

```bash
mv data data.gz
gzip -d data.gz
```

```bash
mv data data.bz2
bzip2 -d data.bz2
```

```bash
mv data data.tar
tar -xf data.tar
```

Bu işlemleri birkaç kez tekrarladım çünkü her açılan dosyanın içinde başka bir sıkıştırılmış dosya bulunuyordu. Dosyalar adeta **Matruşka bebekleri** gibi birbirinin içine yerleştirilmişti.

En sonunda şifreyi içeren düz metin dosyasına ulaştım.

---

## Kullanılan Komutlar

| Komut | Açıklama |
|--------|----------|
| `mktemp -d` | Geçici bir dizin oluşturur. |
| `cd` | Dizin değiştirir. |
| `cp` | Dosya kopyalar. |
| `xxd -r` | Hex dump verisini tekrar binary formata dönüştürür. |
| `file` | Dosyanın gerçek türünü belirler. |
| `mv` | Dosyanın adını veya uzantısını değiştirir. |
| `gzip -d` | Gzip ile sıkıştırılmış dosyayı açar. |
| `bzip2 -d` | Bzip2 ile sıkıştırılmış dosyayı açar. |
| `tar -xf` | Tar arşivini çıkarır. |

---

## Ne Öğrendim

- Geçici çalışma dizini oluşturmayı.
- Hex dump verisini tekrar binary formata dönüştürmeyi.
- `file` komutuyla dosyanın gerçek türünü belirlemeyi.
- Dosya uzantısının her zaman gerçek dosya türünü göstermediğini.
- İç içe geçmiş sıkıştırılmış dosyaları sistematik olarak açmayı.
