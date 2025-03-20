# Tutorial Pemrograman Lanjut
## Nayla Farah Nida - 2306213426

### Module 6

<details>
<summary>Reflection: Commit 1</summary>


The ```handle_connection``` method reads and prints the HTTP request headers from a TCP connection.

**1. Wraps the TCPStream in BufReader**

```BufReader::new(&stream)```: Creates a buffered reader to efficiently read lines from the connection.

**2. Reads the HTTP request line by line**

```.lines()```: Reads the incoming data line by line.

```.map(|result| result.unwrap())```: Extracts the actual string from the Result<String, io::Error>, if no errors occur.

```.take_while(|line| !line.is_empty())```: Reads lines until it encounters an empty line ("").

**3. Stores the request in a ```Vec<String>```**

***4. Prints the HTTP request**

Output:

``` Rust
Request: [
    "GET / HTTP/1.1",
    "Host: 127.0.0.1:7878",
    "Connection: keep-alive",
    "Cache-Control: max-age=0",
    "sec-ch-ua: \"Chromium\";v=\"134\", \"Not:A-Brand\";v=\"24\", \"Google Chrome\";v=\"134\"",
    "sec-ch-ua-mobile: ?0",
    "sec-ch-ua-platform: \"Windows\"",
    "Upgrade-Insecure-Requests: 1",
    "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36",
    "Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7",
    "Sec-Fetch-Site: cross-site",
    "Sec-Fetch-Mode: navigate",
    "Sec-Fetch-User: ?1",
    "Sec-Fetch-Dest: document",
    "Accept-Encoding: gzip, deflate, br, zstd",
    "Accept-Language: en-US,en;q=0.9,id-ID;q=0.8,id;q=0.7,ms;q=0.6,it;q=0.5",
    "Cookie: csrftoken=qnUz3g0Vm17XcQEPWpnPXAZkf20LmLbS",
]
```

</details>

<details>
    <summary>Reflection: Commit 2</summary>
    ![Commit 2 screen capture](/assets/images/commit2.png) 
</details>

<details>
    <summary>Reflection: Commit 3</summary>
    ![Commit 3 screen capture](/assets/images/commit3.png) 

    ```handle_connection``` reads the first line of the HTTP request to determine the requested resource. If the request is ```GET / HTTP/1.1```, it responds with the contents of ```hello.html``` and a 200 OK status. Otherwise, it serves ```404.html``` with a 404 NOT FOUND status. I have done some refactoring to reduce code duplication.
</details>