# public

A collection of my public SSH and GPG keys.

I mostly use this to easily delegate access to new nodes, or provide my
information to those who need it.

# Location, location, location

The files in this repository are available publicly through this repository, or
at to the following locations:

| URL                      | File                                         |
| ------------------------ | -------------------------------------------- |
| sudoforge.com/gpg        | gpg/39E702F59F8159569584E41934EAB0EAB9A964BB |
| sudoforge.com/ssh        | ssh/AEABCFDC9C45B55C1018F82DFCE484D0DF41463D |

My OpenPGP key is also available at the various public keyservers and pools.

## OpenPGP public key - Usage

Read below for common actions that utilize my public encryption key.

### Importing my public key to your keyring

```
gpg --recv-keys 39E702F59F8159569584E41934EAB0EAB9A964BB
```

_Note: You may find that you need to use a keyserver in order to receive my
pubkey. You can do this by adding the parameter `--keyserver <path>` before the
`--recv-keys` parameter._

### Comparing my GPG public key to one in your keyring

```
diff <(gpg --export --armor 39E702F59F8159569584E41934EAB0EAB9A964B) <(curl -Ls sudoforge.com/gpg)
```

### Encrypting a file before sending it to me

To encrypt a file before sending it to me, simply execute the following:

```
gpg --encrypt --recipient 39E702F59F8159569584E41934EAB0EAB9A964BB <path>
```

### Encrypting a message before sending it to me

Maybe you don't have a file; maybe you just want to encrypt `stdout`. To do
that, pipe the contents of whatever you are encrypting to `gpg` like so:

```
echo "hello world!" | gpg --encrypt --armor --recipient 39E702F59F8159569584E41934EAB0EAB9A964BB
```

The encrypted message will be output to `stdout`. You can then do with it what
you will, such as:

* Copying it your system clipboard: `... | xclip -selection c` (or any other
  clipboard program)
* Writing it to a file: `... > <filename>`
* Viewing it in `stdout` _and_ writing it to a file: `... | tee <filename>`

## SSH public key - Usage

Read below for common actions utilizing my public SSH key(s).

### Granting my key access to your machine(s)

Adding my public key to your machine(s) will allow anyone with my private key
AND its passphrase to connect to your machine(s) over SSH, provided those
machine(s) have an SSH server running and a port open (to the public internet
or range of IP addresses).

My private key and passphrase are kept as securely as possible, and rotated
frequently.

```
curl -Ls sudoforge.com/ssh >> ~/.ssh/authorized_keys
```

### Revoking my key's access to your machine(s)

Simply remove the entry from `~/.ssh/authorized_keys` on each of the machines
it was previously copied to.
