# learning-fetch-api
this is MDN's exercise for "fetching data from the server" article.
Let's walk through a couple of examples of the Fetch API.
Fetching text content

For this example, we'll request data out of a few different text files and use them to populate a content area.

This series of files will act as our fake database; in a real application, we'd be more likely to use a server-side language like PHP, Python, or Node to request our data from a database. Here, however, we want to keep it simple and concentrate on the client-side part of this.

There's quite a lot to unpack in here.

First, the entry point to the Fetch API is a global function called fetch(), that takes the URL as a parameter (it takes another optional parameter for custom settings, but we're not using that here).

Next, fetch() is an asynchronous API which returns a Promise. If you don't know what that is, read the module on asynchronous JavaScript, and in particular the article on promises, then come back here. You'll find that article also talks about the fetch() API!

So because fetch() returns a promise, we pass a function into the then() method of the returned promise. This method will be called when the HTTP request has received a response from the server. In the handler, we check that the request succeeded, and throw an error if it didn't. Otherwise, we call response.text(), to get the response body as text.

It turns out that response.text() is also asynchronous, so we return the promise it returns, and pass a function into the then() method of this new promise. This function will be called when the response text is ready, and inside it we will update our <pre> block with the text.

Finally, we chain a catch() handler at the end, to catch any errors thrown in either of the asynchronous functions we called or their handlers.

One problem with the example as it stands is that it won't show any of the poem when it first loads. To fix this, add the following two lines at the bottom of your code (just above the closing </script> tag) to load verse 1 by default, and make sure the <select> element always shows the correct value.
  
Serving your example from a server

Modern browsers will not run HTTP requests if you just run the example from a local file. This is because of security restrictions (for more on web security, read Website security).

To get around this, we need to test the example by running it through a local web server. To find out how to do this, read our guide to setting up a local testing server.  
