# Trino Function Access Control for Built-in Functions

This repository contains a custom distribution of Trino 476 with support for applying access control to built-in functions.

By default, Trino does not perform access control checks on built-in functions. These functions are considered always executable. This project introduces an optional configuration flag that enables enforcement of access control for built-in functions using the existing file-based access control framework.

---

## 🔍 Background

Several discussions in the Trino community have highlighted interest in making built-in functions controllable via access policies:

* [[Issue #19912](https://github.com/trinodb/trino/issues/19912)
* [[Issue #24435](https://github.com/trinodb/trino/issues/24435)
* [[Issue #23278](https://github.com/trinodb/trino/issues/23278)

This patch offers an implementation that addresses these requests by extending Trino's access control checks to include built-in functions, in a configurable and backward-compatible way.

---

## ✅ What This Patch Does

* Introduces a configuration flag:

  ```
  function-access-control.enabled=true
  ```

* When enabled, any built-in function will be subject to access control evaluation.

* Uses Trino’s existing access control mechanism — no changes needed to the access control file format.

* Fully backward-compatible. If the config is not set, default behavior remains unchanged.

---

## 🧪 Tested With

* Trino version: 476
* File-based access control

---

## 🛠 Build Instructions

To build this version of Trino:

```bash
git clone https://github.com/lordicecream/trino-function-access-control.git
cd trino-function-access-control
mvn clean install -DskipTests
```

You can use the resulting `trino-server-476.jar` to run Trino with built-in function access control enabled.

---

## 📆 Docker Image(Optional)

kunalnegi/trino:476-amd64

---

## 📄 License

This repository follows the [[Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0)](https://www.apache.org/licenses/LICENSE-2.0), consistent with upstream Trino.

---

## 🙋‍♂️ Questions or Feedback?

This is an independent effort and is not officially maintained by the Trino project. If you find it useful or have suggestions, feel free to open an issue or discussion in this repository.
