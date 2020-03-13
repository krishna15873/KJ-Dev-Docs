# Authentication

All requests are authenticated with plain url based authentication via a querystring, ?key={authentication-key}

_Authentication key_ will be sent via email and can be reset on request. Please make sure the _Auth Key_ is not packaged inside any publicly available pages or distributables like an apk.

NOTE: All requests are to be made on **https**
## API Endpoints

**1) Base API Endpoint**: domain.com/api/rss?key={key}
<br>

Base API endpoint will return latest news items in JSON format. e.g.:
<pre>
[
    {        
        id: ""
        title: ""        
        coverImage: ""
        summary: "",
        datePublished: ""
        url: ""
        category: ""
    },
    ...
]
</pre>

This returns [Top 20] News Items ordered by Published Date.
<br>

**id** : is the unique identifier of the news item and is unique for its specific domain.

**CoverImage** : can be resized via a url by passing querystring parameters. e.g: /media/image-name.jpg?height={height}&width={width}&format={webp}

We support webp for image compression and highly recommend to resize images for better network/bandwidth performance.


**URL** : can be used to share the news on an app.

**2) Categories Endpoint**: domain.com/api/categories?key={key}

This endpoint returns list of categories/sections.
<pre>
[
    {
        id:"",  // category id
        category:"", // category name
        news:[
                {
                    id: ""
                    title: ""        
                    coverImage: ""
                    summary: "",
                    datePublished: ""
                    url: ""
                },
                ...
            ]
    },
    ...
]
</pre>

**3) Article Endpoint**: domain.com/api/story/{id}?key={key}
<br>
_id_ is the unique id of article 
<br>
_key_ is the auth key

This endpoint returns a web page which is to be displayed inside a **WebView** widget inside an App.

-----

## Caching

We highly recommend the API consumers to cache data where ever possible. We have set an ideal caching time to 15 minutes at day-time and 2 hours at night-time due to the nature of our publishing pattern.
