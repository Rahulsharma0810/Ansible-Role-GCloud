Ansible-Role-GCloud
===================

Role to install Gcloud on Linux Instances


The Issue ? 
-----------
Gcloud comes with outstanding deb package which could install on the go with yum or apt.

But when we try to update anything

```gcloud components update```

```
> Error: (gcloud.components.update) You cannot performe this action
because this cloud SDK installation is managed by an external packages manager. 
Please consider using a separate installation of the 
cloud SDK created through the default mechanism 
described at: https:cloud.google.com/sdk
```
After, By running this role you can install single components like kubectl, gsutil etc. 

Role Variables
--------------
```
# Base URL From SDK Archive will be downloaded.
gcloud_archive_url: "https://dl.google.com/dl/cloudsdk/channels/rapid/downloads"
# Example: google-cloud-sdk-114.0.0-darwin-x86_64.tar.gz. If present, the archive will be downloaded.
# See https://cloud.google.com/sdk/ to find the archive name you need.
gcloud_archive_name: "google-cloud-sdk-180.0.1-linux-x86_64.tar.gz"

# Path where the downloaded archive can be temporarily placed
gcloud_tmp_path: '/tmp/install_gcloud'

# When downloading the archive, always download the archive, even if it already exists in the temp path.
gcloud_force_download: yes

# Path on target node where the unarchived files should land.
gcloud_install_path: "/usr/bin/gcloud"

gcloud_usage_reporting: no        # Enable usage reporting?
gcloud_profile_path: ''           # Path to the user profile login script. Optional.
gcloud_command_completion: yes    # Enable bash style command completion in the login script?
gcloud_update_path: yes           # Update the PATH when when modifying user's login script.
gcloud_override_components: []    # Override the components that would be installed by default, and install these instead.

# Additional components to install by default. Will either be added to the default install
# list, or to the override-components (if provided)
#Example: [kubectl]
gcloud_additional_components: []
gcloud_debug: yes

gcloud_set_as_default: yes
gcloud_config_only: no

```
Default English US English is set.


Example Playbook
----------------

    - hosts: YOUR-HOST-OR-GROUP
      roles:
    	- Ansible-Role-Gcloud

License
-------

MIT

Author Information
------------------

###Rahul Sharma

[Github](https://github.com/Rahulsharma0810)

[Facebook](https://www.facebook.com/rahulsharma0810)