# What happens when I type a URL and press Enter

## 1. DNS lookup

The browser reads the URL and goes through DNS (the Domain Name System). DNS acts like a phone book, but instead of matching names with phone numbers, it matches domains with IP addresses.

It first looks for the nearest cache (saved data): first the browser, then the operating system, then the router, and lastly the ISP's DNS server. If none of those has a match, the resolver works up the chain: the root servers, then the `.com` servers, then the site's own DNS server. Once it gets an answer, it caches it for next time.

## 2. TCP connection

Now that we have the IP, the browser connects to it, typically on port 443 for HTTPS. TCP opens the connection with a 3-way handshake. Once it's established, data is sent in numbered packets, and if one is lost, it gets resent.

## 3. TLS handshake (HTTPS only)

If it's HTTPS, the server sends its certificate to prove it's legit. The browser checks that it's signed by a Certificate Authority and that it matches the domain, and then both sides agree on encryption keys. If that doesn't work, you get a warning like "Your connection is not private."

## 4. HTTP request

The browser sends the HTTP request, a short text message made of three parts: the method (like GET), the path, and the headers.

## 5. The server does the work

The server receives the request and its application code runs. It checks the request, maybe the rate limit and login, may read from a database, and then builds the response.

## 6. HTTP response

The response starts with the HTTP version and the status code (2xx, 3xx, 4xx, 5xx). Next come the headers, which give info about the response, such as the content type, the length, caching, rate limits and security. Then the body, which is HTML for a website or JSON for an API.

## 7. The browser builds the page

Finally the browser builds the page we see. It reads the HTML and builds the structure. Each image, CSS file and JavaScript file is its own request, so the connection gets reused and the DNS answer is already cached. Based on `max-age` and the `etag`, cached files may be reused or replaced. Once that's all done, the JavaScript runs, the CSS is applied, and the page shows on screen.