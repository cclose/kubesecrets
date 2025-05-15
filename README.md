# kubesecrets

🔐 A lightweight CLI utility for decoding and patching Kubernetes secrets.

`kubesecrets` wraps `kubectl` to streamline the most common operations you perform with secrets — including base64 decoding and inline patching — while supporting flexible key lookups and safe editing patterns.

---

## ✨ Features

* 🔍 **Decode** secrets cleanly by key or dump them all
* 🛠️ **Patch** existing keys with new values (stdin, prompt, or CLI arg)
* 🧩 Optional fallback strategies via environment variables
* 🔐 Supports `--kubeconfig` for working with multiple clusters
* ✅ Dry-run mode for safety
* 💡 Append mode (`--append`) for creating new keys

---

## 📦 Installation

### 🧪 Manual (local testing)

```bash
git clone https://github.com/cclose/kubesecrets.git
cd kubesecrets
chmod +x kubesecrets
./kubesecrets --help
```

### 🍺 Via Homebrew (recommended)

If you're using the public tap repo for Homebrew:

```bash
brew tap cclose/tap
brew install cclose/tap/kubesecrets
```

---

## 🔧 Usage

### Get a secret (auto-decodes base64 values)

```bash
kubesecrets get -n mynamespace -s mysecret
```

Or fetch a specific key:

```bash
kubesecrets get -s dockerhub-auth -k password
```

### Patch a secret key

```bash
kubesecrets patch -s dockerhub-auth -k password -u 'hunter2'
```

Prompt for value:

```bash
kubesecrets patch -k password -p
```

Read from stdin:

```bash
echo -n 'hunter2' | kubesecrets patch -k password -i
```

Add a new key (only if it doesn't already exist):

```bash
kubesecrets patch -k new-token -u 'foobar' --append
```

---

## 🧪 Test Requirements

* `kubectl` (connected to your cluster)
* `jq`
* `base64`

---

## 🌱 Environment Variables

These can be set to simplify repetitive operations:

* `KUBESECRETS_DEFAULT_SECRET_NAME`
  Use this if `-s` is not passed

* `KUBESECRETS_NAMESPACE_SECRET_FALLBACK=true`
  Tries using a secret named after the namespace

* `KUBESECRETS_NAMESPACE_SECRET_SUFFIX=_conn_info`
  Used with fallback to try `mynamespace_conn_info` if fallback is enabled

---

## 🔧 Dev Notes

This tool is written entirely in Bash for portability. Tested on macOS and Linux. Feel free to open an issue or PR for enhancements.

---