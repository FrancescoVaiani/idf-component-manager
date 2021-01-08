# IDF Component Management

Component manager for ESP IDF

## Use with idf.py

To use component manager with `idf.py` install `idf-component-manager` python package to idf's virtual environment. Then `idf-component.yml` manifests will be processed automatically when CMake is running.

## Use without IDF

Some features, like uploading a component to the service are available without IDF. It's useful for CI pipelines where IDF may not be available.

The component manager may be executed as a python module, for example:

```
python -m idf_component_manager create-remote-component --namespace espressif --name test
```

## Writing a project manifest

Example of project manifest:

```yaml
version: "2.3.1" # Project or component version (optional)
targets: # List of supported targets (optional)
    - esp32
description: Test project # Project description (optional)
url: https://github.com/espressif/esp-idf # Original repository (optional)
dependencies:
    # Required IDF version
    idf:
        version: ">=4.1"
    # For components maintained by Espressif:
    component:
        version: "~1.0.0"
    # For 3rd party components :
    username/component:
        version: "~1.0.0"
    # For components hosted on non-official web service:
    company_user/component:
        version: "~1.0.0"
        service_url: "https://componentservice.company.com"
    # For components in git repository:
    test_component:
        path: test_component
        git: ssh://git@gitlab.com/user/components.git
    # For components in local folder:
    some_local_component:
        path: ../../projects/component
```
