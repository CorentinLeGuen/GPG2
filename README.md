Utilisation de GnuGPG
===

# Introduction

Ma clé publique se trouve dans le fichier CorentinKey.asc

L'empreinte de ma clé est : 1C83 4D5C 4B5B 3687 E09C  8E9D C641 E0A6 B892 7795

# Création d'une clé

```sh
gpg2 --full-gen-key
```

Puis choisir une bi-clé DSA (D) pour la signature et une bi-clé ElGamal pour le chiffrement.
Choisir au minimum une taille de clé de 3072 pour une recommandation d'au delà 2030.

Les clés sont stockées sous ~/.gnupg. Pour visualiser les clés enregistrées, il faut faire:

```sh
gpg2 --list-keys
```

pour les clés publiques et 

```sh
gpg2 --list-secret-keys
```

pour les clés privées.

# Édition d'une clé

Pour éditer une clé

```sh
gpg2 --edit-key [info_clé]
```

où info clé est l'identifiant permettant de distribuer la clé sans ambiguïté.

Ensuite, il est possible d'utiliser la commande:

```
showpref
```

pour afficher les informations de la clé et

```
check
```

pour vérifier la clé

pour vérifier l'empreinte de la clé et ainsi s'assurer de la bonne conformité de la clé:

```
fpr
```

en cas d'ultime confiance, il est possible de signer la clé pour ainsi assurer à d'autres utilisateurs que la clé est valide et n'est pas une fasse clé:

```
sign
```

pour faire confiance à la clé:

```
trust
```

ensuite il est recommandé de donner une niveau de sûreté. Si vous connaissez la personne et que vous êtes sur de la conformité de la clé, utilisé 4. 5 est uniquement dans le cas où on possède la clé privée.

puis pour quitter l'édition de la clé:

```
save
```

# Signatures d'une clé

Pour afficher toutes les signatures de toutes les clés du trousseau:

```sh
gpg2 --check-sigs
```

# Révocation de clé

Pour révoquer la clé en cas de faille ou de doute, il est préférable de générer un certificat de révocation puis de le stocker sur un autre support que celui où se trouve la clé privée.

```sh
gpg2 --output revok_cle.asc --gen-revoke [info-cle]
```

# Import de clé

Pour importer une clé, il faut utiliser la commande suivante:

```sh
gpg2 --import cle.asc
```

# Export de clé

Pour exporter une clé :

```sh
gpg2 --output macle.asc --armor --export [info-cle]
```

# Chiffrer et signer un message

Pour chiffrer un message:

```sh
gpg2 --encrypt --armor --recipient [info-cle] [document_clair]
```

Cette commande donne un document [document_chiffre].asc

Pour signer un document chiffré :

```sh
gpg2 --armor --output [document_signe].sig --sign [document_chiffre].asc
```

# Déchiffrer un message

Pour déchiffrer un message, on utilise simplement la commande:

```sh
gpg2 [document_chiffre]
```

Si le document est signé, il indiquera (si on connait la signature, après avoir importé la clé publique de la source) qui est le signataire et fournira un message à déchiffrer. Il faudra retapper la même commande pour déchiffrer le message.

# Ma clé publique

Vous pouvez m'envoyer un message à leguen.corentin@mail.com

avec ma clé publique:

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v2

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
=Gsfw
-----END PGP PUBLIC KEY BLOCK-----
