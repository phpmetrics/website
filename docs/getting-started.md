# Quick Start

## Installation

Choose your favorite method:

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
    curl -L "https://github.com/phpmetrics/PhpMetrics/blob/master/releases/phpmetrics.phar?raw=true" -o phpmetrics.phar
    chmod +x phpmetrics.phar && mv phpmetrics.phar /usr/local/bin/phpmetrics
    ```

=== "Apt (Debian, Ubuntu...)"

    ```bash
    curl -L "https://github.com/phpmetrics/PhpMetrics/blob/master/releases/phpmetrics.deb?raw=true" -o phpmetrics.deb
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
## Usage

Run PHPMetrics with the following command:

```bash
php ./vendor/bin/phpmetrics --report-html=myreport <folder-to-analyze>
```

You'll get a CLI output with summary of analysis, and detailled report in `myreport/index.html` file.

## Configuration

You can use a configuration file to use advanced features (like continuous integration, searches and more).

Create a `config.yml` file in the root of your project (you can also use JSON or INI files if you want).

```yaml
---
includes:
    - "src"
report:
    html: "/tmp/report/"
    json: "/tmp/report.json"
    violations: "/tmp/violations.xml"
plugins:
    git:
        binary: git
```

## Continuous integration

You can search for patterns in your code, with the `searches` configuration. Enable the `failIfFound` flag to fail your build if a pattern is found.

For example, if you want to fail if a Repository uses a Service, or if you have to complexe code:

```yaml
...
searches:
    Repository which uses Service:
        type: class
        instanceOf:
            - App\MyRepository
        nameMatches: ".*Repository.*"
        usesClasses:
            - ".*Service"
        failIfFound: true
        
    Class with too complex code:
        type: class
        ccn: ">=10"
        failIfFound: true
```

## Groups of code

Sometimes you want to analyze a group of code (for example your controllers). 

You can do this with the `groups` configuration.

```yaml
...
groups:

  - name: Component
    match: "!component!i"
    
  - name: Controller
    match: "!controller!i"
```
