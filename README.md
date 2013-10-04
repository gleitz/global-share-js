# global-share-js

## ShareJS as a Service

ShareJS is great for synchronizing bits of data across the web. global-share-js is the code powering `http://gleitzman.com/apps/globalshare/channel`, an open channel for sharing data.

Client Usage
-----

First load the client libraries

    <script src="http://raw.github.com/gleitz/global-share-js/master/static/bcsocket.js"></script>
    <script src="http://raw.github.com/gleitz/global-share-js/master/static/share.js"></script>
    <script src="http://raw.github.com/gleitz/global-share-js/master/static/textarea.js"></script>

Then add a textarea to the page and synchronize it with sharejs

    <textarea id="shared"></textarea>
    <script>
        var elem = document.getElementById("shared");
        // connect to the server
        var connection = sharejs.open('YOUR_CHANNEL_NAME', 'text', 'http://gleitzman.com/apps/globalshare/channel', function(error, doc) {
            if (error) {
                console.log("ERROR:", error);
            } else {
                // attach the ShareJS document to the textarea
                doc.attach_textarea(elem);
            }
        });
    </script>

Setting Up Your Own Server
-----

    git clone https://github.com/gleitz/global-share-js.git
    cd global-share-js
    npm update
    node lib/index.js

Then connect to [http://localhost:9003](http://localhost:9003).

Authors
------

-  Benjamin Gleitzman ([@gleitz](http://github.com/gleitz))


Notes
-----

-  Anyone can view/clobber the data you put in the channel.
-  Uses [ShareJS](https://github.com/share/ShareJS).
