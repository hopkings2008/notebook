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
requestRoute=>operation: route request
handler=>operation: imageManifestDispatcher, tagsDispatcher, blobDispatcher, blobUploadDispatcher

st->newapp->route->driver->httpserver->app.ServeHttp->dispatch->authorized->accessController
accessController->requestRoute
requestRoute->handler
```





