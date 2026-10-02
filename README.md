# ⚡ Jocolo Obfuscator v11 - BVM Edition

> Python Obfuscator Next-Gen với 5 lớp mã hoá, BVM engine, và gradient smoky theme.

```
   _____ __  __  ____  _  ____   __
  / ____|  \/  |/ __ \| |/ /\ \ / /
 | (___ | \  / | |  | | ' /  \ V /
  \___ \| |\/| | |  | |  <    > <
  ____) | |  | | |__| | . \  / . \
 |_____/|_|  |_|\____/|_|\_\/_/ \_\
```

---

## 📖 Giới thiệu

**Jocolo Obfuscator** là công cụ bảo vệ source code Python thông qua nhiều lớp mã hoá, biến đổi AST, và sinh mã rác. Được thiết kế để:

- 🔒 **Bảo vệ code** khỏi decompiler thông dụng (`uncompyle6`, `decompyle3`, `pycdc`)
- ⚡ **Mã hoá 5 lớp** với AES-256-GCM + ChaCha20 + XorShift + ByteShuffle + HKDF-SHA256
- 🎨 **Smoky gradient theme** cho CLI đẹp mắt
- 🌍 **Cross-platform**: Windows CMD / PowerShell / Termux / Linux / macOS
- 📦 **Single file**: chỉ cần 1 file Python, không dependencies

---

## ✨ Tính năng

### 🔐 Mã hoá 5 lớp

| Lớp | Thuật toán | Chi tiết |
|-----|-----------|---------|
| 1 | **AES-256-GCM** | Authenticated encryption với tag verification |
| 2 | **ChaCha20** | Stream cipher 20 rounds |
| 3 | **XorShift** | Pseudo-random byte stream |
| 4 | **ByteShuffle** | Deterministic permutation |
| 5 | **HKDF-SHA256** | Key derivation từ master key |

### 🛡️ Biến đổi AST

- **Rename Identifiers**: Đổi tên biến/hàm thành chuỗi ký tự dễ nhầm (`_Ill1lI0OIlI1OlI`)
- **String Encryption**: Mã hoá string constant thành biểu thức XOR/RC4 runtime
- **Integer Obfuscation**: MBA (Mixed Boolean-Arithmetic) cho integer constant
- **Control Flow Flattening**: Chuyển code thành state machine
- **Junk Injection**: Chèn 18 hàm rác + opaque predicates

### 🎯 Loader Runtime

- Tự động decode payload khi chạy
- Không chứa anti-debug gây false-positive
- Chạy được mọi nơi không cần config

---

## 📦 Cài đặt

### Yêu cầu

- **Python 3.8+** (khuyến nghị 3.10 hoặc 3.11)
- Windows / Linux / macOS / Termux

### Cách 1: Clone trực tiếp

```bash
git clone https://github.com/okneweacc-del/jocolo-obfuscator.git
cd jocolo-obfuscator
python jocolo_v11.py
```

### Cách 2: Download file

```bash
curl -O https://raw.githubusercontent.com/okneweacc-del/jocolo-obfuscator/main/jocolo_v11.py
python jocolo_v11.py
```

### Termux

```bash
pkg install python
git clone https://github.com/okneweacc-del/jocolo-obfuscator.git
cd jocolo-obfuscator
python jocolo_v11.py
```

---

## 🚀 Sử dụng

### Cơ bản

```bash
python jocolo_v11.py
```

Tool sẽ hỏi:

```
  ⚡ Nhap file can obfuscate ⚡

  ➤ File input (.py): testnha.py
  ➤ Output mac dinh: testnha_obf.py
  ➤ Nhap output (Enter = mac dinh): [Enter]

  ⏳ Dang obfuscate...

  ✓ Hoan tat! -> testnha_obf.py
  ➤ Kich thuoc goc : 547 bytes
  ➤ Kich thuoc moi : 76842 bytes
  ➤ He so phinh    : 140.48x
```

### Chạy file đã obf

```bash
python testnha_obf.py
```

Output phải **giống hệt** file gốc.

---

## 📊 So sánh

| Tính năng | Jocolo v11 | PyArmor | Nuitka |
|-----------|:----------:|:-------:|:------:|
| Single file | ✅ | ❌ | ❌ |
| Không cần cài đặt | ✅ | ❌ | ❌ |
| AES-256-GCM | ✅ | ❌ | ❌ |
| ChaCha20 | ✅ | ❌ | ❌ |
| Control Flow Flatten | ✅ | ✅ | ✅ |
| String Encryption | ✅ | ✅ | ✅ |
| Cross-version | ⚠️ | ✅ | ✅ |
| Cross-platform | ✅ | ✅ | ✅ |
| Miễn phí | ✅ | ⚠️ | ✅ |

---

## 🧪 Ví dụ

### Input (`testnha.py`)

```python
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)

def main():
    name = "TrungKien"
    print("Xin chào", name)
    fib = [fibonacci(i) for i in range(10)]
    print("Fibonacci:", fib)

if __name__ == "__main__":
    main()
```

### Output (`testnha_obf.py`)

```
'''
_obf_Jocolo
_ower_trungkien
_power_999%
_github_okneweacc-del
'''
# _Illl1lI0OIlI1OlI
# _IOl1II0l1Il1lI0O
# _IlI1lI0OIlI1OlI0
# █▓▒░▄▀▌▐█▓▒░▄▀▌▐█▓▒░▄▀▌▐█▓▒░▄▀▌▐█▓▒░▄▀▌▐█▓▒░▄▀▌▐
...
import sys as _s_, os as _o_
import base64 as _b_, zlib as _z_, marshal as _m_, struct as _st_, hashlib as _h_

__JKEY__ = "a3f8b2c1d4e5..."
__JSALT__ = "1a2b3c4d..."
__JDATA__ = "8fg#2Kl@..."

# ... 1200+ dòng loader với AES/ChaCha/XorShift inline ...
```

### Chạy

```bash
$ python testnha_obf.py
Xin chào TrungKien
Fibonacci: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

---

## 🛠️ Cấu trúc

```
jocolo-obfuscator/
├── jocolo_v11.py       # Tool chính (~1200 dòng)
├── README.md           # File này
├── LICENSE             # MIT
└── examples/
    ├── testnha.py      # Ví dụ input
    └── testnha_obf.py  # Ví dụ output
```

---

## 🔧 Tùy chỉnh

### Tăng độ phình

Sửa trong hàm `obfuscate()`:

```python
out, o, n = obfuscate(inp, outp, 60)  # 60 = noise_count
```

### Bật/tắt tính năng

Sửa trong `obfuscate()`:

```python
# Tắt string encryption
# tree = enc.visit(tree)  # comment dòng này

# Tắt int obfuscation
# tree = IntObfuscator().visit(tree)

# Tắt junk
# for jf in make_junk_funcs(count=18):
#     tree.body.insert(pos, jf)

# Tắt control flow flatten
# tree = flatten_control_flow(tree)
```

---

## ⚠️ Lưu ý quan trọng

### 🚨 Bytecode version lock

Jocolo v11 dùng **`marshal.dumps(compile(...))`** để serialize payload. Điều này có nghĩa:

- ✅ Obf bằng Python 3.10 → chạy được trên Python 3.10
- ❌ Obf bằng Python 3.10 → **KHÔNG chạy** trên Python 3.11

**Giải pháp**: Obfuscate lại trên máy đích, hoặc dùng cùng version.

### 🚨 Không dùng cho mục đích xấu

Tool này được thiết kế để **bảo vệ source code hợp pháp**. Không dùng để:

- Che giấu malware
- Bypass antivirus
- Vi phạm bản quyền phần mềm

### 🚨 Không bảo vệ 100%

Obfuscator chỉ **tăng độ khó** cho việc reverse engineering. Không có biện pháp nào là tuyệt đối:

- Attacker giỏi vẫn có thể dump code từ memory
- Dùng `sys.settrace()` để hook trước khi exec
- Patch `marshal.loads` để intercept payload

Nếu cần bảo vệ cao cấp hơn → dùng **PyArmor** hoặc **Cython**.

---

## 🐛 Known Issues

| Issue | Workaround |
|-------|-----------|
| File output chạy không có output | Đảm bảo Python version giống nhau |
| SyntaxError khi chạy file obf | Chạy `python -c "import ast; ast.parse(open('file_obf.py').read())"` để debug |
| UnicodeEncodeError trên Windows CMD | Chạy `chcp 65001` trước |
| Màu không hiển thị trên CMD cũ | Chạy `reg add HKCU\Console /v VirtualTerminalLevel /t REG_DWORD /d 1 /f` |

---

## 🤝 Đóng góp

Pull request được hoan nghênh! Cho các thay đổi lớn, vui lòng mở issue trước.

```bash
git clone https://github.com/okneweacc-del/jocolo-obfuscator.git
cd jocolo-obfuscator
git checkout -b feature/amazing-feature
git commit -m "Add amazing feature"
git push origin feature/amazing-feature
```

---

## 📜 License

MIT License - xem file [LICENSE](LICENSE) để biết chi tiết.

---

## 👤 Author

**okneweacc-del**

- GitHub: [@okneweacc-del](https://github.com/okneweacc-del)
- Watermark: `_obf_Jocolo` / `_ower_trungkien` / `_power_999%`

---

## 🌟 Credits

- Engine inspired by **PH4SE** by KTN
- Smoky gradient theme từ file `smoky.py`
- Crypto primitives from public domain implementations

---

## 📌 Watermark

Mọi file được obfuscate bởi tool này sẽ chứa watermark ở dòng đầu:

```python
'''
_obf_Jocolo
_ower_trungkien
_power_999%
_github_okneweacc-del
'''
```

Vui lòng **không xoá watermark** khi redistribute.

---

<div align="center">

**⚡ Made with ❤️ by okneweacc-del ⚡**

⭐ Nếu thấy hữu ích, hãy star repo này! ⭐

</div>