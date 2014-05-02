---
layout: post
title:  Mocking Angularjs promises in unit tests 
tagline: or how to configure connect-modrewrite
date:   2014-05-02 10:00:00
categories: angularjs
---

Its easy to mock a service method that returns Promise. 
Whats not easy is to remember to call ```scope.$digest();``` in order to cause promises to check if they are fulfilled:

```js
describe("Test controller with mocked service", function(){
    var rootScope, scope, controller, serviceMock;
  
    beforeEach(inject(function($rootScope, $controller, $q) {
        rootScope = $rootScope;
        scope = $rootScope.$new();
        controller = $controller;
        
        mockKeyTagsService = {
            serviceMock: function(){
                // mock promise
                var deferred = $q.defer();
                deferred.resolve('foo');
                return deferred.promise;
            }            
        }
    }));  
  
    it('should call service and set result in the scope', function(){
    
    });

});

```
