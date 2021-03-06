+++

# THIS DOCUMENT IS AUTOMATICALLY GENERATED. PLEASE DO NOT EDIT

title = "Rancher"
description = "Trigger a Rancher deployment."
user = "drone-plugins"
repo = "drone-rancher"
image = "plugins/drone-rancher"
tags = ["rancher", "docker"]
categories = "deploy"
draft = false
date = 2015-12-15T06:53:26Z
menu = ""
weight = 1

+++

Use the rancher plugin to upgrade a service in [rancher](http://rancher.com).

The following parameters are used to configure this plugin:

- `url` - url to your rancher server, including protocol and port
- `access_key` - rancher api access key
- `secret_key` - rancher api secret key
- `service` - name of rancher service to act on
- `docker_image` - new image to assign to service, including tag (`drone/drone:latest`)
- `start_first` - start the new container before stopping the old one, defaults to `true`

The following is a sample Rancher configuration in your `.drone.yml` file:

```yaml
deploy:
  rancher:
    url: https://example.rancher.com
    access_key: 1234567abcdefg
    secret_key: abcdefg1234567
    service: drone/drone
    docker_image: drone/drone:latest
```

Note that if your `service` is part of a stack, you should use the notation `stackname/servicename` as this will make sure that the found service is part of the correct stack. If no stack is specified, this plugin will update the first service with a matching name which may not be what you want.
