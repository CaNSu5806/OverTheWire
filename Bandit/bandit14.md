# Bandit Level 14 → Level 15

## English

### Goal

Obtain the password for **Bandit Level 15** by submitting the current level's password to a service running on **localhost** at port **30000**.

---

### Challenge Hint

The challenge states that a daemon is listening on **TCP port 30000** on the local machine. By connecting to this service and sending the password for **Bandit14**, the service will return the password for **Bandit15**.

---

### Retrieving the Current Password

First, I displayed the password for **Bandit14**.

```bash
cat /etc/bandit_pass/bandit14
```

I copied the password because it would be required for the next step.

---

### Connecting to the Service

The service is running on the same machine, so I connected to it using **Netcat (nc)**.

```bash
nc localhost 30000
```

### Explanation

- **nc (Netcat)** → A networking utility used to create TCP or UDP connections.
- **localhost** → Refers to the current machine (IP address `127.0.0.1`).
- **30000** → The TCP port where the challenge service is listening.

After the connection was established, the terminal waited for input.

---

### Sending the Password

I pasted the password obtained from the previous step and pressed **Enter**.

If the password was correct, the server responded with:

```text
Correct!
<Bandit15 Password>
```

The second line is the password required to log in to **Bandit Level 15**.

---

### Commands Used

| Command | Description |
|---------|-------------|
| `cat` | Display the contents of a file. |
| `nc` | Connect to a TCP or UDP service. |

---

### What I Learned

- How to use **Netcat** to communicate with a TCP service.
- The meaning of **localhost** (`127.0.0.1`).
- How to send data to a service running on a specific TCP port.
- That services can validate input and return different responses based on the received data.

---

# Türkçe

## Amaç

**Bandit14** şifresini kullanarak **localhost** üzerindeki **30000** numaralı portta çalışan servise bağlanmak ve **Bandit Level 15** şifresini elde etmek.

---

## Verilen İpucu

Challenge'da, yerel makinede (**localhost**) **30000** numaralı TCP portunda çalışan bir servis olduğu belirtilmektedir. Bu servise **Bandit14** şifresi gönderildiğinde, servis doğruysa **Bandit15** şifresini döndürmektedir.

---

## Mevcut Seviyenin Şifresini Alma

Öncelikle **Bandit14** kullanıcısının şifresini görüntüledim.

```bash
cat /etc/bandit_pass/bandit14
```

Elde ettiğim şifreyi bir sonraki adımda kullanmak üzere kopyaladım.

---

## Servise Bağlanma

Servis aynı makine üzerinde çalıştığı için **Netcat (nc)** komutunu kullanarak bağlantı kurdum.

```bash
nc localhost 30000
```

### Açıklama

- **nc (Netcat)** → TCP veya UDP bağlantıları kurmaya yarayan bir ağ aracıdır.
- **localhost** → İçinde bulunduğumuz makineyi ifade eder (`127.0.0.1`).
- **30000** → Challenge servisinin dinlediği TCP port numarasıdır.

Bağlantı kurulduktan sonra terminal kullanıcıdan veri girmesini bekledi.

---

## Şifreyi Gönderme

Bir önceki adımda elde ettiğim **Bandit14** şifresini yapıştırıp **Enter** tuşuna bastım.

Şifre doğru olduğunda sunucu aşağıdaki cevabı verdi:

```text
Correct!
<Bandit15 Şifresi>
```

İkinci satırda görünen değer, **Bandit Level 15** için kullanılacak şifredir.

---

## Kullanılan Komutlar

| Komut | Açıklama |
|--------|----------|
| `cat` | Dosyanın içeriğini görüntüler. |
| `nc` | TCP veya UDP bağlantısı kurar. |

---

## Ne Öğrendim

- **Netcat (nc)** ile bir TCP servisine nasıl bağlanılacağını.
- **localhost** kavramının mevcut makineyi (`127.0.0.1`) ifade ettiğini.
- Belirli bir TCP portuna veri göndererek servislerle iletişim kurmayı.
- Bir servisin gönderilen veriyi doğrulayıp buna göre cevap döndürebileceğini.
