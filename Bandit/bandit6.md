# Bandit Level 6 → Level 7

## Goal | Amaç

**EN:** Find the password for Bandit Level 7.

**TR:** Bandit Level 7 için gerekli şifreyi bulmak.

---

## Challenge Hints | Verilen İpuçları

The challenge provided the following information about the password file:

Challenge, şifreyi içeren dosya hakkında aşağıdaki bilgileri verdi:

- **Owned by user `bandit7`**
- **Owned by group `bandit6`**
- **33 bytes in size**

---

## Searching the Entire System | Tüm Sistemde Arama

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

### Explanation (EN)

The `find` command searches the entire filesystem and filters files using the information provided by the challenge.

- `find /` → Start searching from the root directory (`/`), meaning the entire filesystem.
- `-type f` → Search only for regular files.
- `-user bandit7` → Match files owned by the user `bandit7`.
- `-group bandit6` → Match files whose group owner is `bandit6`.
- `-size 33c` → Match files that are exactly **33 bytes** in size (`c` stands for bytes).

While searching the entire filesystem, `find` tries to enter directories that the current user is not allowed to access. This results in many **"Permission denied"** messages.

To hide these expected error messages, the command ends with:

```bash
2>/dev/null
```

---

## Understanding `2>/dev/null` | `2>/dev/null` Ne İşe Yarar?

### Explanation (EN)

Linux programs can produce different types of output.

- **0 (stdin)** → Standard Input
- **1 (stdout)** → Standard Output (normal output)
- **2 (stderr)** → Standard Error (error messages)

When `find` encounters a directory without permission, it writes the error to **stderr (2)** instead of the normal output.

```bash
2>/dev/null
```

means:

- `2` → Redirect the **standard error** stream.
- `>` → Redirect the output to another location.
- `/dev/null` → A special device that discards everything written to it.

As a result, all error messages are ignored, while the actual search results are still displayed.

### Açıklama (TR)

Linux'ta çalışan her programın farklı çıktı kanalları vardır.

- **0 (stdin)** → Standart giriş
- **1 (stdout)** → Standart çıktı (normal sonuçlar)
- **2 (stderr)** → Hata çıktısı

`find` komutu erişim izni olmayan dizinlere girmeye çalıştığında oluşan **"Permission denied"** mesajlarını **stderr (2)** kanalına yazar.

```bash
2>/dev/null
```

ifadesi şu anlama gelir:

- `2` → Hata çıktısını (**stderr**) seçer.
- `>` → Bu çıktıyı başka bir yere yönlendirir.
- `/dev/null` → Kendisine gönderilen her şeyi yok sayan özel bir Linux aygıtıdır.

Böylece ekranda gereksiz **Permission denied** mesajları görünmez, sadece gerçekten aradığımız dosyanın yolu görüntülenir.

---

## Reading the File | Dosyayı Okuma

```bash
cat <filename>
```

The file contained the password for **Bandit Level 7**.

Dosyanın içinde **Bandit Level 7** için gerekli şifre bulunuyordu.

---

## Commands Used

| Command | Description |
|---------|-------------|
| `find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null` | Search the entire filesystem using multiple filters while hiding permission errors. |
| `cat` | Display the contents of the file. |

---

## What I Learned

- How to search files using multiple filters with `find`.
- How to filter files by owner, group, and size.
- Why **Permission denied** messages appear during system-wide searches.
- How Linux separates normal output (`stdout`) from error output (`stderr`).
- How `2>/dev/null` hides error messages without affecting the actual search results.
