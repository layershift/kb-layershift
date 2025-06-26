---
title: 'Programing and scripting languages '
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'Web Scripting Explained, Plesk Proxy Mode and web scripting, LiteSpeed and web scripting'
metadata:
    description: 'Web Scripting Explained, Plesk Proxy Mode and web scripting, LiteSpeed and web scripting'
    'og:url': 'https://www.layershift.com/kb/managed-vps/plesk/programing-and-scripting-languages'
    'og:type': website
    'og:title': 'Programing and scripting languages | Layershift KB'
    'og:description': 'Web Scripting Explained, Plesk Proxy Mode and web scripting, LiteSpeed and web scripting'
    'og:image': 'https://www.layershift.com/kb/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2025-06-26T16:16:11+01:00'
    'article:modified_time': '2025-06-26T16:16:11+01:00'
    'article:author': Layershift
media_order: 'hosting and dns hosting.png,web scripting .png'
menu: 'Programing and scripting'
---

![hosting%20and%20dns%20hosting](hosting%20and%20dns%20hosting.png "hosting%20and%20dns%20hosting")

![web%20scripting%20](web%20scripting%20.png "web%20scripting%20")

* **FastCGI** is a high-performance interface between web servers and applications, commonly used to run dynamic content. Unlike traditional CGI, FastCGI keeps the application processes alive between requests, which significantly improves performance and reduces server load.

* **CGI** (Common Gateway Interface) is one of the earliest methods for generating dynamic web content. Each request spawns a new process, which makes it less efficient than FastCGI, but it's still used for simple scripts or legacy applications that don’t require high performance.

* **SSI** (Server Side Includes) allows web servers to dynamically include content (such as headers, footers, or timestamps) into HTML pages before serving them. It's lightweight and useful for basic content templating, but limited in functionality compared to other scripting methods.

* **Custom error documents** enable website owners to define their own error pages (e.g., 404 Not Found or 500 Internal Server Error), offering a more user-friendly experience and allowing for consistent branding even when an error occurs.
 
 
 ## Web Scripting Configuration in Apache Virtual Hosts 

This section outlines what changes are made to the Apache virtual host configuration when enabling each **Web Scripting** option in Plesk.

---

### FastCGI

When **FastCGI** is enabled, the following block is added:

```apache
<IfModule mod_fcgid.c>
    <Files ~ (\.fcgi$)>
        SetHandler fcgid-script
        Options +ExecCGI
    </Files>
</IfModule>
```

#### What it does:
- Enables execution of `.fcgi` scripts.
- Applies the `fcgid-script` handler via `mod_fcgid`.
- Activates `ExecCGI` to allow CGI-style execution.


---

### CGI (Common Gateway Interface)

When **CGI** is enabled, two key changes occur:

**1. ScriptAlias is added:**
```apache
ScriptAlias "/cgi-bin/" "/var/www/vhosts/example.com/httpdocs/cgi-bin/"
```

**2. Document-Root `Options` directive is updated:**
```apache
Options -Includes +ExecCGI
```

#### What it does:
- Maps the `/cgi-bin/` URL path to the physical directory containing CGI scripts.
- Enables CGI script execution with `+ExecCGI`.

---

### SSI (Server Side Includes)

When **SSI** is enabled, the document-root `Options` directive is updated to:

```apache
Options +Includes -ExecCGI
```

#### What it does:
- Enables parsing of SSI directives like `<!--#include ... -->` inside `.shtml` or `.html` files.

---

### Perl

When **Perl** scripting is enabled, the following block is added:

```apache
<IfModule mod_perl.c>
    <Files ~ (\.pl$)>
        SetHandler perl-script
        PerlHandler ModPerl::Registry
        Options +ExecCGI
        allow from all
        PerlSendHeader On
    </Files>
</IfModule>
```

#### What it does:
- Enables `.pl` Perl scripts to be executed via `mod_perl`.
- Wraps scripts in `ModPerl::Registry` for persistent execution (performance boost).
- Ensures proper HTTP header handling with `PerlSendHeader On`.
- Allows public access to Perl script output via `allow from all`.

---

## Proxy Mode and scripting in Plesk

You can find the **Proxy Mode** toggle under:

**Domain > Hosting & DNS > Apache & nginx Settings**

### What Happens When Proxy Mode is Enabled

- NGINX acts as a reverse proxy, serving static files and forwarding everything to Apache.
- Apache processes:
  - PHP via FastCGI/PHP-FPM
  - CGI scripts
  - Perl
  - SSI
- Apache `.htaccess` rules are applied.

### What Happens When Proxy Mode is Disabled

- Apache is completely **disabled** for that domain.
- NGINX becomes the **only active web server**.
- NGINX uses **PHP-FPM only** for PHP processing.
- CGI, Perl, and SSI do **not work** as these depend on Apache which is no longer used.
- Apache `.htaccess` rules are ignored (NGINX doesn’t process .htaccess files).
- All scripting functionality tied to Apache configuration is **non-functional**.

---

## LiteSpeed and scripting in Plesk

If you have the **LiteSpeed Extension** for Plesk installed, LiteSpeed replaces Nginx + Apache as the main web server. This change affects how scripts are processed.

### Key Points:

- **LiteSpeed supports Apache configurations**, including `.htaccess` files.
- **PHP must be run via FastCGI** — LiteSpeed does **not** support PHP-FPM on Plesk.
- LiteSpeed provides better performance under load, lower memory usage, and built-in caching.
- To use LiteSpeed, you need a separate license. You can request a LiteSpeed free trial and a LiteSpeed license via a support ticket.

