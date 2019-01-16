# GPG CHEATSHEET
## Generar keypair
```
$ gpg --gen-key
$ gpg --list-secret-keys
```

## Importar llaves privadas
```
$ gpg --allow-secret-key-import --import "mi llave key.txt"
```

## Importar llaves publicas
```
$ gpg --import "Alice's public key.txt"
```
## Listar keys
$ gpg --list-keys

## Exportar llaves
publica:
```
$ gpg -ao publickey.asc --export alice@rlab.be
```

privada:
```
$ gpg -ao privatekey.asc --export-secret-keys alice@rlab.be
```
-a : armored file
-o : con nombre

## Borrar llaves
$gpg --delete-secret-key <username>
$gpg --delete-key <username>
$ gpg -ao certificate.asc --gen-revoke <keyID>

## Encriptar un archivo para otra persona(alice -> bob)
```
alice@alice::~$ gpg --output doc.gpg --encrypt --recipient blake@cyb.org doc
```

```
bob@bob:~$ gpg --output doc --decrypt doc.gpg
```
## Encriptar un archivo para uno mismo
 ciframos un archivo simetricamente, nos va a pedir un passphrase, elijamos uno largo que podamos acordarnos [xkcd]

```
$ gpg -o secreto.gpg -c original.txt
$ gpg -d secreto.gpg
```

o si lo quieren guardar en un documento

```
$ gpg -d secreto.gpg > archivo.txtx
```

Enviar y bajar llaves de keyservers

```
$gpg --keyserver serverurl --send-keys <keyID>
$gpg --keyserver serverurl --recv-key <keyID>
```

