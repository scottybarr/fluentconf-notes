#### Writing RESTful APIs
### Resources
* Consider them as nouns, not verbs
* Collection Resource
    - Use plural names
* Instance Resource (what we called Detail Resource)

### CRUD
* PUT can be used for creation also when the id is specified by the client
* PUT is idempotent
* POST should return a canonical URL Location on create
* POST can be used to update on an instance/detail resource.
* POST not idempotent

### Versioning
* Can be URL based `api.eventmobi.com/v1`
* Could use media-type e.g. `application/foo+json;application&v=2`
* Only change versions when you have a breaking change (not backwards compatible)

### CamelCase on property output!
* Chances are your API consumers will be using JS!

### createdAt/updatedAt
* Use this metadata! Return an ISO-8601 datetime string using UTC.

### Allow resource extensions
* e.g. `/applications/a1b2c3.json`
* e.g. `/applications/a1b2c3.csv`

### Linking
Can be used for pagination
```
namespace: {
    meta: {
        href: '/v1/blah',
        hypermedia: 'application/json', // application/ion+json
        rel: ['collection']
    }
}
```

### Reducing bandwidth
* Allow a fields query string param to only return certain fields

### HTTP Caching
* Query string paramaters affect caching as they are seen as completely different resources from one without a query string.

### Searching
* Filter Search: The 'q' query string parameter. e.g. `/accounts/?q=some+value` (filters an entire collection)
* Attribute Search: `/accounts/?surname=Joe&email=joe@joe.com`
* Starts with: `?email=joe*`
* Ends with: `?email=*company.com`
* Contains: `?email=*foo*`
* Range query: `/accounts?createdAt=[2014-09-01,2014-09-15]`

### Async Requests
* Headers
```
Status 204 Accepted
Location: /emails/s234td67
```
* Body:
```
{
    status: "queued"
}
```

### Batch Creation
Bypasses caching entirely
POST /accounts
```
{
    items: [
        {... account 1 ...},
        {... account 2 ...},
        ...
    ]
}
```

### Error handling
```
{
    status: 409,
    code: 40924, // Custom API specific error code
    property: 'name', '' The offending property
    message: 'A directory named ...',
    developerMessage: '...', // more info for developers.
    moreInfo: 'http://domain.com/api/docs/code/40924'
}
```

### Security
* Use existing protocol - Use oauth2 and SSL together! Everything should be sent securely over the wire.
* Stormpath have written their own security standard. If you don't work with finance, military then oauth2+SSL is *probably sufficient*

### 401 vs 403
* 401 You need valid credentials
* 403 Sorry, you're not allowed

### IDs
* Use UUIDs!
* Avoid sequential numbers as they are susceptible from a security perspective (contention, fusking)

### Override methods
* Helpful for legacy clients that don't support all HTTP methods
* `POST /accounts/x7y8z9?_method=DELETE`

### ETags
* Response: `Etag: 686875f6544e87`
* Later Request: `If-None-Match: 686875f6544e87`
* Later Response: `304 Not Modified`

### Maintenance
* Use HTTP Redirects
* Create abstraction layer/endpoints when migrating
* Use well defined custom media-types.
