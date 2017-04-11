## Swagger SDK - Leverage Hypermedia Discovery in your RESTful Services

The ColdBox SwaggerSDK is a dependency of the Relax module and is available to allow you to provided consumers of your API with information on paths, methods, expectations and available parameters.

Hypermedia design patterns, usually provided within the content of `OPTIONS` requests to your endpoint, allow you to provide autodiscovery and consumption assistance on-the-fly.

For convenience, built-in methods are available within Relax to simplify the loading and parsing of your existing API documentation.

An example, leveraging an `OPTIONS` request for an endpoint (and using the Base REST handler), might look like:

```
public function petOptions( event, rc, prc ){
    
    petOptions = getInstance( "APIService@relax" ).loadAPI( 'petstore' );
    prc.response.setData( petOptions.paths );
    prc.response.setStatusCode( STATUS.SUCCESS );

}
```

This will serve the `paths` node of the `petstore` API as a JSON response to an options request:



