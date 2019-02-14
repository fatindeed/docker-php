# PHP with Xdebug (for IDE debugging)

[![](https://images.microbadger.com/badges/image/fatindeed/php:xdebug5.svg)](https://microbadger.com/images/fatindeed/php:xdebug5 "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/fatindeed/php:xdebug5.svg)](https://microbadger.com/images/fatindeed/php:xdebug5 "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/commit/fatindeed/php:xdebug5.svg)](https://microbadger.com/images/fatindeed/php:xdebug5 "Get your own commit badge on microbadger.com")

## VS Code Debugging

1.  [PHP Debug](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug) extension is required.

2.  Docker environment is also required.

3.  Create or update `.vscode/launch.json` in your project, add following configurations:

    ```json
    {
        "version": "0.2.0",
        "configurations": [
            {
                "name": "Launch with Docker",
                "type": "php",
                "request": "launch",
                "program": "${file}",
                "runtimeExecutable": "docker",
                "runtimeArgs": [
                    "run",
                    "--rm",
                    "--env",
                    "XDEBUG_CONFIG=remote_host=host.docker.internal xdebug.idekey=VSCODE",
                    "--env",
                    "TIMEZONE=Asia/Shanghai",
                    "-v",
                    "/path/to/workspace_root:/home/www-data",
                    "fatindeed/php:xdebug5",
                    "php",
                    "-f",
                    "${relativeFile}",
                    "--"
                ],
                "pathMappings": {
                    "/home/www-data": "${workspaceRoot}",
                },
                "port": 9000
            }
        ]
    }
    ```

    **MOST IMPORTANT: Network configuration**

    - `remote_host` value should be configured correctly.
    - If you are using **Docker Desktop for Windows/Mac**, `host.docker.internal` works in most cases.
    - If you are using **Docker Toolbox**, `192.168.99.1` works in most cases.
    - If all above dosen't work, try your host ip address which run **VS Code**. For example: `192.168.x.x`, `10.x.x.x`.
    - After that, make sure your firewall allow inbound traffic on port 9000 (If you haven't change it).

    **MOST IMPORTANT: Volume configuration**

    - `/home/www-data` can not be changed.
    - `/path/to/workspace_root` should be configured correctly.
    - Make sure `/path/to/workspace_root` is valid for Docker volume mounts, or you may reconfigure Share Folders.

    **Other configuration**

    - `TIMEZONE` value should be configured correctly.

4.  Now you may get debug working.
