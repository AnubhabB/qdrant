
<p align="center">
  <img height="100" src="https://github.com/qdrant/qdrant/blob/master/docs/logo.svg?raw=true" alt="Qdrant">
</p>

<p align="center">
    <b>Vector Similarity Search Engine with extended filtering support</b>
</p>

<p align=center>
    <a href="https://slack.jina.ai"><img src="https://github.com/qdrant/qdrant/workflows/Tests/badge.svg"></a>
    <a href="https://qdrant.github.io/qdrant/redoc/index.html"><img src="https://img.shields.io/badge/Docs-OpenAPI%203.0-success"></a>
    <a href="https://github.com/qdrant/qdrant/blob/master/LICENSE"><img src="https://img.shields.io/badge/License-Apache%202.0-success"></a>
    <a href="https://t.me/joinchat/sIuUArGQRp9kMTUy"><img src="https://img.shields.io/badge/Telegram-Qdrant-blue.svg?logo=telegram" alt="Telegram"></a>
</p>

Qdrant (read: _quadrant_ ) is a vector similarity search engine.
It provides a production-ready service with a convenient API to store, search, and manage points - vectors with an additional payload.
Qdrant is tailored to extended filtering support.  It makes it useful for all sorts of neural-network or semantic-based matching, faceted search, and other applications. 

Qdrant is written in Rust :crab:, which makes it reliable even under high load.

With Qdrant, embeddings or neural network encoders can be turned into full-fledged applications for matching, searching, recommending, and much more!

## Demo Projects

### Semantic Text Search :mag:

The neural search uses semantic embeddings instead of keywords and works best with short texts.
With Qdrant and a pre-trained neural network, you can build and deploy semantic neural search on your data in minutes.
[Try it online!](https://demo.qdrant.tech/)

### Similar Image Search - Food Discovery :pizza:

There are multiple ways to discover things, text search is not the only one.
In the case of food, people rely more on appearance than description and ingredients.
So why not let people choose their next lunch by its appearance, even if they don’t know the name of the dish?
[Check it out!](https://food-discovery.qdrant.tech/)

<details>
<summary> More solutions </summary>

<table>
    <tr>
        <td>
            <img src="https://qdrant.tech/content/images/text_search.png">
        </td>
        <td>
            <img src="https://qdrant.tech/content/images/image_search.png">
        </td>
        <td>
            <img src="https://qdrant.tech/content/images/recommendations.png">
        </td>
    </tr>
    <tr>
        <td>
            Semantic Text Search
        </td>
        <td>
            Similar Image Search
        </td>
        <td>
            Recommendations
        </td>
    </tr>
</table>

<table align="center">
    <tr>
        <td>
            <img src="https://qdrant.tech/content/images/chat_bots.png">
        </td>
        <td>
            <img src="https://qdrant.tech/content/images/matching_engines.png">
        </td>
    </tr>
    <tr>
        <td>
            Chat Bots
        </td>
        <td>
            Matching Engines
        </td>
    </tr>
</table>

</details>

## API

Online OpenAPI 3.0 documentation is available [here](https://qdrant.github.io/qdrant/redoc/index.html).
OpenAPI makes it easy to generate client for virtually any framework or programing language.

You can also download raw OpenAPI [definitions](openapi/openapi.yaml).

## Features

### Filtering

Qdrant supports key-value payload associated with vectors. Not only stores payload but also allows filter results based on payload values.
It allows any combinations of `should`, `must` and `must_not` conditions, but unlike ElasticSearch post-filtering, Qdrant guarantees all relevant vectors are retrieved.

### Rich data types

Vector payload supports a large variety of data types and query conditions, including string matching, numerical ranges, geo-locations, and more.
Payload filtering conditions allow you to build almost any custom business logic that should work on top of similarity matching.

### Query planning and payload indexes

Using the information about the stored key-value data, `query planner` decides on the best way to execute the query.
For example, if the search space limited by filters is small, it is more efficient to use a full brute force than an index.

### SIMD Hardware Acceleration

With the `BLAS` library, Qdrant can take advantage of modern CPU architectures. 
It allows you to search even faster on modern hardware.

### Write-ahead logging

Once service confirmed an update - it won't lose data even in case of power shut down. 
All operations are stored in the update journal and the latest database state could be easily reconstructed at any moment.

### Stand-alone

Qdrant does not rely on any external database or orchestration controller, which makes it very easy to configure.

## Usage

### Docker :whale:

Build your own from source

```bash
docker build . --tag=qdrant
```

Or use latest pre-built image from [DockerHub](https://hub.docker.com/r/generall/qdrant)

```bash
docker pull generall/qdrant
```

To run container use command:

```bash
docker run -p 6333:6333 \
    -v $(pwd)/path/to/data:/qdrant/storage \
    -v $(pwd)/path/to/custom_config.yaml:/qdrant/config/production.yaml \
    qdrant
```

* `/qdrant/storage` - is a place where Qdrant persists all your data. 
Make sure to mount it as a volume, otherwise docker will drop it with the container. 
* `/qdrant/config/production.yaml` - is the file with engine configuration. You can override any value from the [reference config](config/config.yaml) 

Now Qdrant should be accessible at [localhost:6333](http://localhost:6333/)

## Docs :notebook:

* The best place to start is [Quick Start Guide](QUICK_START.md)
* Use the [OpenAPI specification](https://qdrant.github.io/qdrant/redoc/index.html) as a reference
* Follow our [Step-by-Step Tutorial](https://qdrant.tech/articles/neural-search-tutorial/) to create your first neural network project with Qdrant

## Contacts

* Join our [Telegram group](https://t.me/joinchat/sIuUArGQRp9kMTUy)
* Follow us on [Twitter](https://twitter.com/qdrant_engine)
* Subscribe to our [Newsletters](https://tech.us1.list-manage.com/subscribe/post?u=69617d79374ac6280dd2230b2&amp;id=acb2b876fc)
* Write us an email [info@qdrant.tech](mailto:info@qdrant.tech)

## License

Qdrant is licensed under the Apache License, Version 2.0. View a copy of the [License file](LICENSE).

