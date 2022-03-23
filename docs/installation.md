=== "Composer"

    ```bash
    composer global require 'phpmetrics/phpmetrics'
    ```

    Please note that the ~/.composer/vendor/bin directory must be in your $PATH. For example in your ~/.bash_profile (or ~/.bashrc), add :

    ```bash
    export PATH=~/.composer/vendor/bin:$PATH
    ```

=== "Docker"

    ```bash
    docker run --rm --volume `pwd`:/project herloct/phpmetrics [<options>]
    ```

=== "Phar"

    ```bash
    curl https://github.com/phpmetrics/PhpMetrics/releases/download/v2.7.3/phpmetrics.phar
    chmod +x phpmetrics.phar && mv phpmetrics.phar /usr/local/bin/phpmetrics
    ```

=== "Apt (Debian, Ubuntu...)"

    ```bash
    curl https://github.com/phpmetrics/PhpMetrics/releases/download/v2.7.4/phpmetrics.deb
    dpkg -i phpmetrics.deb
    ```

=== "Brew (OSX)"

    ```bash
    brew install phpmetrics
    ```

=== "PhpArch"

    ```bash
    yaourt install phpmetrics
    ```
