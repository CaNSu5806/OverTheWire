# Bandit Level 4 → Level 5

## Goal | Amaç

**EN:** Find the password for Bandit Level 5.

**TR:** Bandit Level 5 için gerekli şifreyi bulmak.

---

## Identifying the File Type | Dosya Türlerini Belirleme

```bash
file ./*
```

### Explanation (EN)

The current directory contains multiple files with similar names, and only one of them is a human-readable ASCII text file. The `file` command was used to identify the type of each file without opening them.

### Açıklama (TR)

Bulunduğumuz dizinde benzer isimlere sahip birden fazla dosya bulunuyordu. Bunlardan yalnızca biri okunabilir bir **ASCII text** dosyasıydı. Hangi dosyanın doğru olduğunu belirlemek için `file` komutu kullanıldı.

The output identified the correct file as an **ASCII text** file.

---

## Reading the Correct File | Doğru Dosyayı Okuma

```bash
cat ./-file07
```

> **Note:** Replace `-file07` with the actual ASCII text file shown in your output.

### Explanation (EN)

After identifying the correct file, `cat` was used to display its contents.

### Açıklama (TR)

Doğru dosya belirlendikten sonra içeriğini görüntülemek için `cat` komutu kullanıldı.

The file contained the password for **Bandit Level 5**.

Dosyanın içinde **Bandit Level 5** için gerekli şifre bulunuyordu.

---

## Commands Used

| Command | Description |
|---------|-------------|
| `file ./*` | Identify the type of every file in the current directory. |
| `cat` | Display the contents of a file. |

---

## What I Learned

- How to identify file types using the `file` command.
- How to distinguish human-readable ASCII files from binary files.
- How to inspect multiple files efficiently without opening each one.
