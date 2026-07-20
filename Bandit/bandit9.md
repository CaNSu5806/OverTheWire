# Bandit Level 9 → Level 10

## Goal | Amaç

**EN:** Find the password for Level 10 inside `data.txt`. The password is stored in one of the **human-readable strings** and is preceded by several `=` characters.

**TR:** `data.txt` dosyasının içinde bulunan Level 10 şifresini bulmak. İpucuna göre şifre, **insan tarafından okunabilir (human-readable)** bir metin olarak saklanmış ve öncesinde birkaç tane `=` karakteri bulunuyor.

---

## Understanding the Hint | İpucunu Anlamak

The hint says:

> *The password is in the file `data.txt` and is one of the few human-readable strings, preceded by several '=' characters.*

İpucunda dosyanın içinde çok fazla veri olduğu, ancak bunların arasındaki sadece birkaç kısmın okunabilir metin olduğu söyleniyor. Ayrıca şifreden hemen önce birkaç tane `=` karakteri bulunduğu belirtiliyor. Bu yüzden önce okunabilir metinleri çıkarmak, ardından içinde `=` geçen satırları filtrelemek en mantıklı yöntem oldu.

---

## Finding the Password | Şifreyi Bulma

```bash
strings data.txt | grep "=="
```

### Explanation (EN)

#### `strings`

The `strings` command extracts printable, human-readable text from a file. It is especially useful when a file contains binary or unreadable data.

#### `grep`

`grep` searches for lines that match a specific pattern.

#### `"=="`

Here I searched for lines containing `==` because the hint mentioned that the password is preceded by several `=` characters.

#### `|` (Pipe)

The pipe (`|`) sends the output of the first command directly to the second command.

In this case:

- `strings` extracts all readable text.
- `grep "=="` filters those results and only shows the lines containing `==`.

---

### Açıklama (TR)

#### `strings`

`strings` komutu, bir dosyanın içindeki okunabilir metinleri ekrana çıkarmak için kullanılır. Özellikle binary dosyalar veya anlamsız karakterler içeren dosyalarda işe yarar. Bu levelde de dosyanın büyük kısmı okunamayan verilerden oluştuğu için önce okunabilir kısımları çıkarmamız gerekiyordu.

#### `grep`

`grep` komutu belirttiğimiz ifadeyi içeren satırları bulur ve sadece onları gösterir.

#### `"=="`

İpucunda şifreden önce birkaç tane `=` karakteri olduğu söylendiği için `==` ifadesini arattım. Böylece gereksiz satırlar elenmiş oldu.

#### `|` (Pipe)

`|` (pipe), ilk komutun çıktısını ikinci komuta aktarır.

Bu komutta:

- `strings`, okunabilir metinleri çıkardı.
- `grep "=="` ise sadece içinde `==` geçen satırları gösterdi.

Bu sayede şifrenin bulunduğu satıra kolayca ulaştım.

---

## Commands Used

| Command | Description |
|---------|-------------|
| `strings` | Extracts human-readable text from a file. |
| `grep` | Searches for lines matching a pattern. |
| `|` | Sends the output of one command to another command. |

---

## What I Learned

- How to extract readable text from binary-looking files using `strings`.
- How to filter command output with `grep`.
- How to combine multiple commands using a pipe (`|`).
- How to use the given hint to narrow down the search instead of checking the entire file manually.
