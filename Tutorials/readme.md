# Tutorials


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>fetch</title>
</head>
<body>
    <div>
        <h1>fetch demo</h1>
        <img src="" alt="img" title="img" />
    </div>
    <script>
        let myImage = document.querySelector('img');
        let myHeaders = new Headers();
        // myHeaders.append('Content-Type', 'image/jpeg');
        myHeaders.append('Content-Type', 'image/png');
        // https://cdn.xgqfrms.xyz/json/cats.json
        // https://cdn.xgqfrms.xyz/logo/icon.png
        let myInit = {
            method: 'GET',
            headers: myHeaders,
            mode: 'cors',
            cache: 'default'
        };
        // mode: 'cors',
        // Access-Control-Allow-Origin
        /*
        fetch.html:1 Fetch API cannot load https://cdn.xgqfrms.xyz/logo/icon.png. Response to preflight request doesn't pass access control check: No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'http://localhost:3000' is therefore not allowed access. The response had HTTP status code 403. If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled
        */

        // let myRequest = new Request('https://cdn.xgqfrms.xyz/logo/icon.png');
        function blobToString(b) {
            var u, x;
            u = URL.createObjectURL(b);
            x = new XMLHttpRequest();
            x.open('GET', u, false); // although sync, you're not fetching over internet
            x.send();
            URL.revokeObjectURL(u);
            return x.responseText;
        }
    var b = new Blob(['hello world']);
    blobToString(b); // "hello world"
    var img = new Blob(["https://cdn.xgqfrms.xyz/logo/icon.png"]);
    let newImg = blobToString(img);
    console.log(newImg);
        // blob to string
        // http://stackoverflow.com/a/23024613
        let myRequest = new Request('icon.png');

        fetch(myRequest,myInit).then(
            function(response) {
                // alert("OK");
                console.log("OK");
                console.log(response);
                // console.log(response.blob());
                // response.blob()
                return response.blob();
            }
        ).then(
            function(blob) {
                console.log(blob);
                let cdnURL = "https://cdn.xgqfrms.xyz/";
                console.log(blob);
                let objectURL = URL.createObjectURL(blob);
                console.log(objectURL);
                let newobjectURL = `${cdnURL}${blob}`
                console.log(newobjectURL);
                myImage.src = objectURL;
                // myImage.src = newImg;
                console.log(newImg);
                console.log(myImage.src);
            }
        );
    </script>
</body>
</html>


```

```sh
$ browser-sync start --server --files "./*.*"

```


https://gist.github.com/xgqfrms-GitHub/68af127cb3ec33587ee5bffe9810fb1b


