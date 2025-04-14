# 🛠 Contributing to astarconf

Thank you for considering contributing to **astarconf**!

This project aims to be a secure, flexible, and minimal tool for encrypted config loading.
Your ideas, bug reports, and code are welcome.

---

## 📥 How to Contribute

### 1. Fork the Repository

```bash
git clone https://github.com/astaraiki/astarconf.git
cd astarconf
```

### 2. Install Dependencies

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

Or if using poetry:

```bash
poetry install
```

### 3. Make Changes

Edit the Python code in `astarconf.py` or tests. Follow [PEP8](https://peps.python.org/pep-0008/).

### 4. Add Tests (Optional but Recommended)

```bash
pytest tests/
```

### 5. Create a Pull Request

Push your branch and create a PR against `main`.

---

## 📦 CLI Manual

Run the command-line tool locally:

```bash
python astarconf.py --help
```

---

## 🧪 Testing

We use `pytest`. Make sure any new functionality is covered by tests.

---

## 💡 Suggestions

If you're unsure how to implement something or want feedback early, feel free to open an issue with a `[Proposal]` tag.

---

## 📄 License

All contributions are under the [MIT License](LICENSE).
