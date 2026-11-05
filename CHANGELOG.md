# ActiveState security releases (filelock 3.1.0 line)

ActiveState maintains the filelock 3.1.0 line, the last release that supports
Python 2.7 (3.2.x and later are Python 3 only), on the `3.1.0.x` branch.

## 3.1.0.post2

| CVE | Advisory | Status |
| --- | --- | --- |
| [CVE-2026-112909](https://nvd.nist.gov/vuln/detail/CVE-2026-112909) | [GHSA-69hj-f68j-2879](https://github.com/advisories/GHSA-69hj-f68j-2879) | **Patched.** `UnixFileLock` (and `WindowsFileLock`) opened the lock file with `O_TRUNC`, emptying any regular file another local user renamed or hard-linked onto the lock path. The lock file is now opened without `O_TRUNC` and locked as found (backport of upstream 4.2.1, tox-dev/filelock#835). The advisory's `fchmod` half does not apply: 3.1.0 has no `mode` parameter. |
| [CVE-2026-22701](https://nvd.nist.gov/vuln/detail/CVE-2026-22701) | [GHSA-qmgc-5h2g-mvrw](https://github.com/advisories/GHSA-qmgc-5h2g-mvrw) | Not affected (unchanged since 3.1.0+security.1): 3.1.0 has no writability pre-check before the `SoftFileLock` open, which uses `O_CREAT \| O_EXCL`. |
| [CVE-2025-68146](https://nvd.nist.gov/vuln/detail/CVE-2025-68146) | [GHSA-w853-jp5j-5j7f](https://github.com/advisories/GHSA-w853-jp5j-5j7f) | Patched in 3.1.0+security.1. |

The version scheme changes from `+security.N` to the PEP 440 post-release
`.postN`; `3.1.0.post2` follows `3.1.0+security.1`.

## 3.1.0+security.1

| CVE | Advisory | Status |
| --- | --- | --- |
| [CVE-2025-68146](https://nvd.nist.gov/vuln/detail/CVE-2025-68146) | [GHSA-w853-jp5j-5j7f](https://github.com/advisories/GHSA-w853-jp5j-5j7f) | **Patched.** `O_NOFOLLOW` on the Unix and soft lock opens; reparse points refused on Windows (backport of upstream 3.20.1). |
| [CVE-2026-22701](https://nvd.nist.gov/vuln/detail/CVE-2026-22701) | [GHSA-qmgc-5h2g-mvrw](https://github.com/advisories/GHSA-qmgc-5h2g-mvrw) | Not affected: the vulnerable `SoftFileLock` check-then-open race does not exist in 3.1.0. |
