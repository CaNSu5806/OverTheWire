# Bandit Level 5 → Level 6

## Goal | Amaç

**EN:** Find the password for Bandit Level 6.

**TR:** Bandit Level 6 için gerekli şifreyi bulmak.

---

## Challenge Hints | Verilen İpuçları

The challenge provided the following hints about the password file:

Challenge, şifreyi içeren dosya hakkında aşağıdaki ipuçlarını verdi:

- **Human-readable**
- **1033 bytes in size**
- **Not executable**
- **Located somewhere under the `inhere` directory**

---

## Searching for the File | Dosyayı Arama

```bash
find . -type f -size 1033c ! -executable
```

### Explanation (EN)

The `find` command was used to search for files matching the given hints.

- `find .` → Start searching from the current directory.
- `-type f` → Search only for regular files.
- `-size 1033c` → Match files that are exactly **1033 bytes** (`c` stands for bytes).
- `! -executable` → Exclude executable files, since the challenge specifies that the target file is **not executable**.

The challenge also mentioned that the file was **human-readable**. After `find` returned the matching file, this was verified by opening it with `cat`. Since the file contained plain text, it satisfied the final hint.

### Açıklama (TR)

Verilen ipuçlarına uyan dosyayı bulmak için `find` komutu kullanıldı.

- `find .` → Aramayı mevcut dizinden başlatır.
- `-type f` → Sadece normal dosyaları arar.
- `-size 1033c` → Boyutu tam olarak **1033 byte** olan dosyaları filtreler (`c`, byte anlamına gelir).
- `! -executable` → Çalıştırılabilir dosyaları hariç tutar. Çünkü ipuçlarında hedef dosyanın **çalıştırılabilir olmadığı** belirtilmiştir.

Challenge ayrıca dosyanın **human-readable (okunabilir metin)** olduğunu söylüyordu. `find` komutu uygun dosyayı bulduktan sonra bu bilgi `cat` komutu ile doğrulandı. Dosya düz metin içerdiği için son ipucunu da karşılıyordu.

---

## Reading the File | Dosyayı Okuma

```bash
cat <filename>
```

The file contained the password for **Bandit Level 6**.

Dosyanın içinde **Bandit Level 6** için gerekli şifre bulunuyordu.

---

## Commands Used

| Command | Description |
|---------|-------------|
| `find . -type f -size 1033c ! -executable` | Search for a non-executable file that is exactly 1033 bytes. |
| `cat` | Display the contents of the file. |

---

## What I Learned

- How to search for files using multiple conditions with `find`.
- How to filter files by type, size, and executable permission.
- How to use challenge hints to narrow down search results efficiently.
