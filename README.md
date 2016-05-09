# WELCOME TO COLDBOX RELAX

>RELAX = RESTFul Tools For Lazy Experts!

What is Relax? ColdBox Relax is a set of RESTFul tools for lazy experts. We pride ourselves in helping you (the developer) work smarter and 
ColdBox Relax is a tool to help you document your projects faster. ColdBox Relax provides you with the necessary tools to 
automagically model, document and test your RESTFul services. One can think of ColdBox Relax as a way to describe RESTFul web services, 
test RESTFul web services, monitor RESTFul web services and document RESTFul web services–all while you relax!

##LICENSE
Apache License, Version 2.0.

##IMPORTANT LINKS
- Code: http://github.com/coldbox/coldbox-relax
- Issues: https://github.com/ColdBox/coldbox-relax/issues
- Documentation: https://github.com/ColdBox/coldbox-relax/wiki

##SYSTEM REQUIREMENTS
- Lucee 4.5+
- Railo 4+
- ColdFusion 9+

INSTRUCTIONS
============

Just drop into your **modules** folder or use the box-cli to install

`box install relax`

## Settings
You will need to update the your `ColdBox.cfc` with a `relax` structure with your preferred settings for Relax.  
 
```
relax = {
    // The location of the relaxed APIs, defaults to models.resources
    APILocation = "models.resources",
    // Default API to load, name of the directory inside of resources
    defaultAPI = "myapi",
    // History stack size, the number of history items to track in the RelaxURL
    maxHistory = 10
};
```

## Modeling
You can look at the samples inside of this module under the `models/resources` directory.  To start you can copy the `Relax.cfc` into your own project folder and then start spicing up the API via the RelaxDSL methods.
