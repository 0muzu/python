def encrypt(text, shift):
    result = ""
    for char in text:
        if char.isalpha():
            # Böyük və ya kiçik hərf üçün fərqli əsas
            start = ord('A') if char.isupper() else ord('a')
            result += chr((ord(char) - start + shift) % 26 + start)
        else:
            result += char
    return result

def decrypt(cipher, shift):
    return encrypt(cipher, -shift)

mode = input("Şifrələmə (e) və ya deşifrələmə (d) seçin: ")
text = input("Mətni daxil edin: ")
shift = int(input("Şift dəyəri (məsələn, 3): "))

if mode == "e":
    print("Şifrələnmiş mətn:", encrypt(text, shift))
elif mode == "d":
    print("Açılmış mətn:", decrypt(text, shift))
else:
    print("Yanlış seçim!")
