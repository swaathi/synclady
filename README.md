# Synclady
Syncs local file changes to a server over RSync via SSH

* [Dependencies](#dependencies)
* [Compiling & Configuring](#compiling--configuring)
* [Running Synclady](#running-synclady)
* [Functions](#functions)
* [YAML Configuration](#yaml-config)
* [Logs](#logs)
* [License](#license)

### Requirements
Make sure you have added your local public key to the servers `~/.ssh/authorized_keys`.
Else SSH will wait for password to be entered by user.

### Dependencies
* Python 2.7 (Developed and Tested)

### Installing
1. Clone/Download this Repo
2. Run `python setup.py install`
3. Copy the [default YAML file](#yaml-config) to `~` (users home directory).

### Running Synclady
From Terminal, run
```synclady sync```

This will start a file listener on the local source directory and push changes to
the server source directory.

### Functions
* `synclady sync`: Watches over local path defined in source in [YAML configuration file](#yaml-config)
* `synclady pull`: Replaces local directory with server contents (use only once
  when you starting the application for the first time)
* `synclady resync`: Pushes all changes which were made when local system was
  offline and pulls new server contents

### YAML configuration
This YAML is automatically created in the `~` (users home directory) directory.
It holds all the configuration attributes for Synclady.

#### Attributes
* `source`: Local path to be watched, and server path to be synced with
* `endpoints`: Hash of each file/folder action which should ping to an API endpoint

#### Default File
```
  source:
    local: /Users/username/data/
    server: /uploads/username/
    ip: sample@192.168.1.1
  endpoints:
    file_create: "http://192.168.1.1/api/files/create"
    file_destroy: "http://192.168.1.1/api/files/destroy"
    folder_destroy: "http://192.168.1.1/api/folders/destroy"
```

### Logs
All Synclady logs are maintained at `/tmp/synclady.log`

### Coming up
1. Pulling servers contents periodically to local directory
2. Pushing files and folders which were deleted when local was offline to server

License
--------

    Copyright 2016 Skcript.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

About
-----

![Skcript](http://www.skcript.com/static/skcript_norm.png)

Synclady is maintained and funded by Skcript. The names and logos for
Skcript are properties of Skcript.

We love open source, and we have been doing quite a bit of contributions to the community. Take a look at them [here][skcriptoss]. Also, encourage people around us to get involved in community [operations][community]. [Join us][hiring], if you'd like to see the world change from our HQ.

[skcriptoss]: http://skcript.github.io/
[community]: http://www.skcript.com/community?utm_source=github
[hiring]: http://www.skcript.com/careers?utm_source=github
