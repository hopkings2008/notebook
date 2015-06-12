# notebook
this is a notebook for my dailywork

```flow
st=>start: DockerDaemon(send request to registry)
end=>end: end
newapp=>operation: handlers.NewApp(http main server handler)
route=>operation: App.register(regiter route handler)
driver=>operation: factory.Create(create correspondent storage driver)
httpserver=>operation: http.Server.Serve(start main loop for incoming request)
app.ServeHttp=>operation: app.ServeHttp
dispatch=>operation: app.dispatch(dispatch the client request to handler)
authorized=>operation: app.authorized
accessController=>operation: app.accessController.Authorized(authorize the client)
requestRoute=>condition: route request
manifestDispatcher=>operation: imageManifestDispatcher
tagsDispatcher=>operation: tagsDispatcher

st->newapp->route->driver->httpserver->app.ServeHttp->dispatch->authorized->accessController
accessController->requestRoute
requestRoute(yes)->manifestDispatcher
requestRoute(no)->tagsDispatcher
```

 blobDispatcher, blobUploadDispatcher
