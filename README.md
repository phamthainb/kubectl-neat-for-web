# 🧹 kubectl-neat-for-web

A simple web-based version of [`kubectl-neat`](https://github.com/itaysk/kubectl-neat) that cleans up verbose Kubernetes YAML/JSON outputs — right in your browser.

> ✅ No install.  
> ✅ No data upload.  
> ✅ 100% client-side.  
> ✅ Multi-document YAML (`---`) supported.

screenshot: ![Screenshot](https://raw.githubusercontent.com/phamthainb/kubectl-neat-for-web/master/image.png)

---

## 🚀 Try It Now

👉 [Open in browser](https://phamthainb.github.io/kubectl-neat-for-web)

---

## 🛠 Features

- ✂️ Removes noisy fields like:
  - `status`
  - `metadata.managedFields`
  - `metadata.creationTimestamp`
  - `resourceVersion`, `uid`, etc.
- 📎 Supports multi-document YAML (`---`)
- 📄 Paste content or upload `.yaml` / `.yml` files (single or multiple)
- 📁 Upload entire folders containing YAML files
- ⚡ Instant preview in browser
- 🛡 No backend or network dependency — fully static HTML

