***
сгенерировать связку новых ключей
```bash
gpg --full-gen-key
```
настройка конфига для gpg ~/.gnupg/gpg.conf
```nano
keyid-format 0xlong
throw-keyids
no-emit-version
no-comments
```
основные команды
```bash
gpg -k # вывод публичного ключа
gpg -K # вывод приватного ключа
gpg -e -a -r yourkeyid filename # шифрование файла
gpg -d -o -r  filename filename.asc
# -e - encript
# -a - сохранять в аски тексте
# -r - для указания id ключа
# -d - decript
# -o - выходной файл
gpg --export -a your@mail.com > file.gpg # экспорт публичного ключа
gpg --export-secret-key -a your@mail.com > file.gpg # экспорт приватного ключа
gpg --delete-keys your@mail.com # удаление публичных ключей
gpg --delete-secret-keys your@mail.com # удаление приватных ключей
gpg --import file.gpg
```

```bash
pass init your@email.com
pass insert Path/to/password
pass generate Path/to/password
-m # многострочный
```

***