# 📘 Astarconf – Secure Config Loader

**Astarconf** is a Python library for loading configuration from YAML, JSON, `.env`, or dict, with optional encryption for sensitive fields.

---

## 🚀 Features

- 🔐 Encrypt/decrypt `user`, `password`, or custom fields
- 🔌 Load config from `.yaml`, `.json`, `.env`, or Python `dict`
- 🧑‍💻 Access values via `.key` or `["key"]`
- 🧰 Command-line tool for managing secrets
- 🔄 Export config as dict or JSON

---

## 🧱 Class: `Astarconf`

```python
Astarconf(source, nested_as_attr=False, hybrid_mode=True)
```

**Parameters:**
- `source`: str | dict — path to `.yaml`, `.json`, `.env`, or a Python dict
- `nested_as_attr`: bool — if True, nested dicts become attribute-accessible
- `hybrid_mode`: bool — enables both key and attr access to nested data

**Example:**

```python
conf = Astarconf("config.yaml")
print(conf.database.user)
print(conf["database"]["user"])
```

---

## 🔐 Encryption CLI

```bash
astarconf.py -g ~/.astarconf/secret.key     # generate secret
astarconf.py -c config.yaml                 # encrypt fields (default - user, passowrd)
astarconf.py -c config.yaml token api_key   # encrypt defaults fields and mentioned
astarconf.py -d config.yaml                 # decrypt config (in same file)
astarconf.py -d config.yaml -o output.yaml  # decrypt config, write to output file
astarconf.py -o output.yaml -f              # overwrite output if exist
```

---

## 📦 Utility Functions

### `find_secret_key()`
Searches known paths for an existing encryption key. Path for search: 
environment variable $ASTARCONF_SECRET
~/.astarconf/secret.key
/etc/astarconf/secret.key
any of "astarconf.key", "astarconf_secret.key", "secret.key" in $PATH


### `generate_secret_key(to_path)`
Generates a new Fernet key and saves it.

### `delete_secret_key(path)`
Deletes a saved secret key.

### `encrypt_yaml_fields(yaml_path, key, field_names)`
Encrypts specific fields recursively in a YAML file.

### `decrypt_yaml_fields(yaml_path, key, output_path=None, force=False)`
Decrypts encrypted fields in YAML and optionally saves output.

### `is_encrypted(value)`
Returns `True` if the string is Fernet-encrypted.

---

## 🧠 `AttrNamespace` Class

Used internally to represent nested configuration objects.

```python
conf.database.host         # attribute access
conf["database"]["host"]   # key access
conf.to_dict()             # export as dict
conf.to_json(indent=2)     # export as JSON
```

---

## 📄 License

MIT
