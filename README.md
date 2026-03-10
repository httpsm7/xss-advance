<div align="center">

<img src="https://img.shields.io/badge/XSS-Advanced%20Payloads-red?style=for-the-badge&logo=javascript&logoColor=white"/>
<img src="https://img.shields.io/badge/Payloads-367%2B-critical?style=for-the-badge"/>
<img src="https://img.shields.io/badge/License-Unlicense-blue?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Python-3.x-yellow?style=for-the-badge&logo=python"/>
<img src="https://img.shields.io/badge/Burp%20Suite-Ready-orange?style=for-the-badge"/>

# 💀 xss-advance

### Advanced XSS Payload Collection for Security Research & Penetration Testing

> A structured, Burp Suite–ready database of 367+ unique Cross-Site Scripting (XSS) payloads,  
> categorized by attack vector for efficient use in real-world web application security assessments.

</div>

---

## 📌 Overview

**xss-advance** is a professional-grade XSS payload repository designed for:

- Web Application Penetration Testers
- Bug Bounty Hunters
- Security Researchers
- CTF Players

All payloads are clean, deduplicated, and formatted for **direct use** in Burp Suite Intruder, custom scripts, or manual testing — no preprocessing needed.

---

## 📂 Repository Structure

```
xss-advance/
│
├── payloads/
│   └── xss_payloads.py          # Python module — import & use programmatically
│
├── burp/
│   ├── burp_all_payloads.txt    # All 367+ payloads — Burp Intruder ready
│   └── categories/
│       ├── classic.txt          # Classic reflected XSS
│       ├── event_handler.txt    # Event handler based (onerror, onload, etc.)
│       ├── dom.txt              # DOM-based XSS
│       ├── attribute.txt        # HTML attribute injection
│       ├── css.txt              # CSS / style based XSS
│       ├── filter_bypass.txt    # WAF & filter bypass techniques
│       ├── polyglot.txt         # Multi-context polyglot payloads
│       ├── svg_xml.txt          # SVG / XML / MathML vectors
│       ├── url.txt              # URL / redirect based XSS
│       ├── template.txt         # Template injection (Angular, Vue, React, SSTI)
│       ├── mutation.txt         # Mutation XSS (mXSS)
│       ├── encoding.txt         # Encoding & obfuscation
│       └── advanced.txt         # Modern JS, DOM APIs, async, Proxy, etc.
│
├── LICENSE
└── README.md
```

---

## 📊 Payload Categories

| Category | Count | Description |
|---|---|---|
| `classic` | 26 | Standard `<script>` based reflected XSS |
| `event_handler` | 70 | onerror, onload, onfocus, onclick, etc. |
| `dom` | 35 | DOM sink exploitation (innerHTML, eval, etc.) |
| `attribute` | 25 | Breaking out of HTML attributes |
| `css` | 12 | CSS expression / style injection |
| `filter_bypass` | 44 | WAF evasion, encoding tricks, null bytes |
| `polyglot` | 15 | Work across multiple injection contexts |
| `svg_xml` | 14 | SVG, XML, MathML specific vectors |
| `url` | 24 | javascript://, data:, vbscript:// URIs |
| `template` | 21 | AngularJS, Vue, React, Jinja2, Thymeleaf SSTI |
| `mutation` | 24 | mXSS via parser inconsistencies |
| `encoding` | 18 | HTML entities, base64, unicode, hex |
| `advanced` | 68 | Proxy, Atomics, postMessage, ServiceWorker, etc. |
| **Total** | **367+** | **Fully deduplicated** |

---

## ⚡ Usage

### 1. Burp Suite Intruder

```
Intruder → Positions → mark your injection point §value§
Payloads → Payload type: Simple list
         → Load → burp/burp_all_payloads.txt
```

For targeted testing, load a specific category file from `burp/categories/`.

---

### 2. Python — Programmatic Use

```python
from payloads.xss_payloads import ALL_PAYLOADS, PAYLOAD_CATEGORIES

# All payloads
for payload in ALL_PAYLOADS:
    print(payload)

# Specific category
for payload in PAYLOAD_CATEGORIES['filter_bypass']:
    print(payload)
```

---

### 3. cURL / Shell Loop

```bash
# Test a single endpoint with all payloads
while IFS= read -r payload; do
    curl -s -G "https://target.com/search" \
        --data-urlencode "q=$payload" | grep -q "alert(1)" && \
        echo "[VULN] $payload"
done < burp/burp_all_payloads.txt
```

---

### 4. With ffuf

```bash
ffuf -w burp/burp_all_payloads.txt \
     -u "https://target.com/page?q=FUZZ" \
     -mr "alert(1)"
```

---

## 🛡️ Tested Against

- Reflected XSS in URL params, headers, body
- Stored XSS via form inputs and API endpoints
- DOM XSS via `innerHTML`, `document.write`, `eval`
- WAF-protected targets (Cloudflare, ModSecurity, AWS WAF)
- Template injection in Angular, Vue, React, Jinja2

---

## ⚠️ Legal Disclaimer

> This repository is intended **strictly for authorized security testing, research, and educational purposes only.**
>
> Use of these payloads against systems **without explicit written permission** is illegal and unethical.  
> The author holds **no responsibility** for any misuse or damage caused by this material.
>
> Always obtain proper authorization before testing any system.

---

## 📜 License

This project is released under the **Unlicense** — free for any use, with no conditions.  
See [LICENSE](./LICENSE) for details.

---

<div align="center">

Made for the security community 🔐  
**Star ⭐ the repo if it helped your research**

</div>
