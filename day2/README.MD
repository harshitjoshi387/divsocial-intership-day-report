---

# DNS Lookup using nslookup

Command Used

```bash
nslookup github.com
```

Output

```
Server:  reliance.reliance
Address: 2405:201:6844:8be::c0a8:1d01

Non-authoritative answer:

Name: github.com
Address: 20.207.73.82
```

### Screenshot

![nslookup](screenshots/nslookup.png)

### Explanation

The `nslookup` command is used to find the IP address associated with a domain name.

- **DNS Server:** reliance.reliance
- **Domain Name:** github.com
- **Resolved IP Address:** 20.207.73.82

When we type `github.com` into a browser, the browser cannot communicate using the domain name directly. It first asks the DNS server to translate the domain name into an IP address. After receiving the IP address, the browser establishes a connection with GitHub's server and begins downloading the webpage resources.

---

# Browser Loading Flow

```
User enters github.com
        │
        ▼
DNS Lookup (nslookup)
        │
        ▼
IP Address Found (20.207.73.82)
        │
        ▼
TCP Connection
        │
        ▼
TLS Handshake (HTTPS)
        │
        ▼
HTTP Request
        │
        ▼
Server Response
        │
        ▼
Browser Downloads HTML
        │
        ▼
Downloads CSS
        │
        ▼
Downloads JavaScript
        │
        ▼
Downloads Images & Icons
        │
        ▼
Page Rendered
```

---

# Key Learnings

- Learned how DNS converts a domain name into an IP address.
- Understood the purpose of the Network tab in Chrome DevTools.
- Observed different types of network requests.
- Learned the importance of HTTP status codes.
- Understood the difference between Request Headers and Response Headers.
- Learned how browsers load resources such as HTML, CSS, JavaScript, images, and favicons.