# DNS Walkthrough

DNS (Domain Name System) is the system that translates a human-readable website address into the network address needed to reach the correct server. Instead of remembering an IP address, a visitor can type a name such as `ikramkhan-gif1.github.io` and DNS helps find where that site is hosted.

When someone enters a website address, the browser first needs the IP address associated with the hostname. It can use information already stored in the browser or operating-system cache. If the answer is not cached, the request goes to a DNS resolver, normally operated by the user's internet provider or another DNS service. The resolver looks for the answer and, when necessary, queries the DNS hierarchy.

A resolver can contact a root nameserver, which points it toward the appropriate top-level-domain nameserver, such as the nameserver responsible for `.com` or another top-level domain. The resolver then asks the authoritative nameserver for the domain. The authoritative nameserver is the source that holds the domain's DNS records and returns the relevant answer. The resolver caches that answer for the record's configured TTL (time to live) and sends it back to the user's device.

DNS records contain different types of information. An **A record** maps a hostname directly to an IPv4 address. An **AAAA record** maps a hostname to an IPv6 address. A **CNAME record** creates an alias from one hostname to another hostname. For example, a subdomain can use a CNAME to point to a hosting provider's hostname. The resolver follows that hostname and ultimately obtains the address needed to connect to the service. A CNAME is therefore a hostname-to-hostname relationship, not simply a direct IP address.

After the browser receives the necessary network address, it connects to the hosting service. For an HTTPS website, the browser also establishes a secure TLS connection and verifies the site's certificate. The browser then sends the HTTP request for the page, the host returns the HTML and other assets such as CSS and images, and the browser renders the website.

In short, the path is roughly: **browser → DNS resolver → nameserver hierarchy → authoritative nameserver → DNS response → hosting server → HTTPS response → browser renders the site**. Understanding this process makes it easier to troubleshoot a future custom-domain setup instead of treating DNS as a black box.
