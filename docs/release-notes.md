<style>
    .md-typeset h2 {
        font-weight: bold;
    }
</style>

{% include "./.opsman_filename_change_note.md" %}

!!! warning "Azure Updating to 2.5"
     Ops Manager will be removing the necessity to provide availability zones for azure.
     If your `director.yml`(see [`staged-director-config`][staged-director-config])
     has a block like the following in the networks section:
     ```yaml
        availability_zone_names:
        - "null"
     ```
     your deployment will have the following error:
     ```json
     {"errors":["Availability zones cannot find availability zone with name null"]}
     ```
     To fix this error, please remove the `availability_zone_names` section from your azure config, or re-run
     [`staged-director-config`][staged-director-config] to update your `director.yml`.

## v5.0.15
March 9, 2021

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.19.23 |
    | azure-cli | 2.20.0 |
    | bbr-cli | [1.9.1](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.9.1) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.9.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.9.0) |
    | gcloud-cli | 330.0.0 |
    | govc-cli | v0.24.0 |
    | om | 6516c1a327f7bb7ede88c857e5b4d0d58f27f5bc-2021-01-26T10:53:54-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-5.0.15" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4738-1](https://ubuntu.com/security/notices/USN-4738-1). The CVEs are related to vulnerabilities with `libssl` and related libraries.
- CVE update to container image. Resolves [USN-4754-1](https://ubuntu.com/security/notices/USN-4754-1). The CVEs are related to vulnerabilities with `python` and related libraries.


## v5.0.14
February 25, 2021

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.19.7 |
    | azure-cli | 2.19.1 |
    | bbr-cli | [1.9.1](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.9.1) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.9.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.9.0) |
    | gcloud-cli | 327.0.0 |
    | govc-cli | v0.24.0 |
    | om | 6516c1a327f7bb7ede88c857e5b4d0d58f27f5bc-2021-01-26T10:53:54-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-5.0.14" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4719-1](https://ubuntu.com/security/notices/USN-4719-1).


## v5.0.13
January 15, 2021

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.215 |
    | azure-cli | 2.17.1 |
    | bbr-cli | [1.9.1](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.9.1) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.9.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.9.0) |
    | gcloud-cli | 323.0.0 |
    | govc-cli | v0.24.0 |
    | om | 39fd21c57e46588e76bb07826a2d8809e29382e9-2021-01-12T08:23:20-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.19" target="_blank">Download</a>

### Bug Fixes
- Use [`pip` documented](https://pip.pypa.io/en/stable/installing/) method for installing it on the container image
- With new GCP practices, defining a [`hostname`](https://cloud.google.com/compute/docs/instances/custom-hostname-vm) on the VM can be required.
  When creating an Ops Manager VM on GCP, the attribute can be set via the configuration file.
  
    ```yaml
    ---
      opsman-configuration:
        gcp:
          boot_disk_size: 100
          custom_cpu: 4
          custom_memory: 16
          gcp_service_account: ((service_account_key))
          project: ((project))
          public_ip: ((ops_manager_public_ip))
          region: ((region))
          ssh_public_key: ((ops_manager_ssh_public_key))
          tags: ((ops_manager_tags))
          vm_name: ((environment_name))-ops-manager-vm
          vpc_subnet: ((management_subnet_name))
          zone: ((availability_zones.0))
          hostname: testing.some.domain
    ```

## v5.0.12
January 5, 2021

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.208 |
    | azure-cli | 2.17.1 |
    | bbr-cli | [1.9.0](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.9.0) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.9.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.9.0) |
    | gcloud-cli | 321.0.0 |
    | govc-cli | v0.24.0 |
    | om | dc7ecb856d9d6e8a5538512922e688bd337ab246-2021-01-04T09:19:13-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |


### Bug Fixes
- CVE update to container image. Resolves [USN-4672-1](https://ubuntu.com/security/notices/USN-4672-1).
  The CVEs are related to vulnerabilities with `unzip` and related libraries.
- CVE update to container image. Resolves [USN-4667-1](https://ubuntu.com/security/notices/USN-4667-1).
  The CVEs are related to vulnerabilities with `apt` and related libraries.
- CVE update to container image. Resolves [USN-4665-1](https://ubuntu.com/security/notices/USN-4665-1).
  The CVEs are related to vulnerabilities with `curl` and related libraries.
- CVE update to container image. Resolves [USN-4662-1](https://ubuntu.com/security/notices/USN-4662-1).
  The CVEs are related to vulnerabilities with `libssl` and related libraries.
- CVE update to container image. Resolves [USN-4677-1](https://ubuntu.com/security/notices/USN-4677-1).
  The CVEs are related to vulnerabilities with `p11` and related libraries.


## v5.0.11

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.189 |
    | azure-cli | 2.15.1 |
    | bbr-cli | [1.8.1](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.8.1) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | gcloud-cli | 319.0.0 |
    | govc-cli | 0.23.0 |
    | om | acfd93675b65c8ca8a7f584cd53796d09e5fc88b-2020-12-03T07:19:52-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

### Features
- [`configure-opsman`][configure-opsman] task can now configure the UAA token expirations and timeouts.
   
   ```yaml
   tokens-expiration:
     access_token_expiration: 10
     refresh_token_expiration: 10
     session_idle_timeout: 10
   ```

### Bug Fixes
- [`update-runtime-config`][update-runtime-config] task has the `releases` input as optional.
  When looking for `releases`, if the input wasn't there then the task would fail.
  A check has been added to ensure the input is there.
- With long-running tasks (using `om` commands),
  sometimes the authentication token would expire.
  If possible the token will be refreshed.
  This should help with HTTP retries.
- CVE update to container image. Resolves [USN-4608-1](https://ubuntu.com/security/notices/USN-4608-1).
  The CVEs are related to vulnerabilities with `ca-certificates` and related libraries.
- CVE update to container image. Resolves [USN-4635-1](https://ubuntu.com/security/notices/USN-4635-1).
  The CVEs are related to vulnerabilities with `krb5` and related libraries.

## v5.0.10
November 24, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.184 |
    | azure-cli | 2.15.1 |
    | bbr-cli | [1.8.1](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.8.1) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | gcloud-cli | 319.0.0 |
    | govc-cli | 0.23.0 |
    | om | 3a7d703bacb004220450d5984b01a5ea6ebe5087-2020-11-23T14:34:44-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

### Bug Fixes
- Fixes an issue where `stemcell-heavy` in `download-product` had a regression with boolean values.

## v5.0.9
November 19, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.180 |
    | azure-cli | 2.15.0 |
    | bbr-cli | [1.8.1](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.8.1) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | gcloud-cli | 319.0.0 |
    | govc-cli | 0.23.0 |
    | om | d424cdfe525f3d9ec4f7b6995c160d7b80c4a6f1-2020-11-18T09:51:49-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-5.0.9" target="_blank">Download</a>

### Bug Fixes
- The `backup` scripts did not have the correct command line options to compress the tarball.
  It is still a valid tarball, just not compressed.
  This has been fixed by changing `tar -cvf` to `tar -zcvf`.
- [`prepare-tasks-with-secrets`][prepare-tasks-with-secrets] could not be used with other tasks.
  For example, if you had written custom tasks.
  The `TASK_PATH` was added, so custom paths of tasks could be prepared, too.
- [`stage-configure-apply`][stage-configure-apply] was missing the ability to configure errands.
  We've added the `ERRAND_CONFIG_FILE` parameter.
- [`stage-configure-apply`][stage-configure-apply] was using the incorrect path relative to the input.
  It was using `config` instead of `assign-stemcell-config`.

## v5.0.7
October 23, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.163 |
    | azure-cli | 2.13.0 |
    | bbr-cli | 1.8.0 |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | gcloud-cli | 315.0.0 |
    | govc-cli | 0.23.0 |
    | om | [6.4.2](https://github.com/pivotal-cf/om/releases/tag/6.4.2) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-5.0.7" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4581-1](https://usn.ubuntu.com/4581-1/).
  The CVEs are related to vulnerabilities with `python3.6` and related libraries.
  This affects the all IAAS container images only.
- CVE update to container image. Resolves [USN-4601-1](https://usn.ubuntu.com/4601-1/).
  The CVEs are related to vulnerabilities with `python3-pip` and related libraries.
  This affects the all IAAS container images only.

### Known Issues
- When using the task [`backup-tkgi`][backup-tkgi] behind a proxy
  the values for `no_proxy` can affect the ssh (though jumpbox) tunneling.
  When the task invokes the `bbr` CLI, an environment variable (`BOSH_ALL_PROXY`) has been set,
  this environment variable tries to honor the `no_proxy` settings.
  The task's usage of the ssh tunnel requires the `no_proxy` to not be set.

    If you experience an error, such as an SSH connection refused or connection timeout,
    try setting the `no_proxy: ""` as `params` on the task.

    For example,

    ```yaml
    - task: backup-tkgi
      file: platform-automation-tasks/tasks/backup-tkgi.yml
      params:
        no_proxy: ""
    ```

## v5.0.6
October 14, 2020

!!! note "Updates to CLI versions"
    We've now updated our list of CLI versions.
    It includes the supported IAAS CLIs.

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.157 |
    | azure-cli | 2.13.0 |
    | bosh-cli | [6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | gcloud-cli | 314.0.0 |
    | govc-cli | 0.23.0 |
    | om | [6.4.1](https://github.com/pivotal-cf/om/releases/tag/6.4.1) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-5.0.6" target="_blank">Download</a>

### Bug Fixes
- Do to a release packaging issue,
  the previous patch version had issues invoking `openstack` CLI.
  This release ensures this has been fixed.
  We've also added further release testing to ensure it doesn't happen again.
- [`download-and-upload-product`][download-and-upload-product] did not upload the stemcell as expected.
  The task now properly uploads the stemcell if `stemcell-iaas`
  is provided in the config file. 

### Known Issues
- When using the task [`backup-tkgi`][backup-tkgi] behind a proxy
  the values for `no_proxy` can affect the ssh (though jumpbox) tunneling.
  When the task invokes the `bbr` CLI, an environment variable (`BOSH_ALL_PROXY`) has been set,
  this environment variable tries to honor the `no_proxy` settings.
  The task's usage of the ssh tunnel requires the `no_proxy` to not be set.
  
    If you experience an error, such as an SSH connection refused or connection timeout,
    try setting the `no_proxy: ""` as `params` on the task.
    
    For example,
    
    ```yaml
    - task: backup-tkgi
      file: platform-automation-tasks/tasks/backup-tkgi.yml
      params:
        no_proxy: ""
    ```

## v5.0.5
October 9, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.4.1](https://github.com/pivotal-cf/om/releases/tag/6.4.1) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-5.0.5" target="_blank">Download</a>

### Bug Fixes
- The "bug fixes" for collections in `om` 6.1.2+
  were causing unexpected issues in some tiles.
  The collection work has been reverted
  to its original functionality.
- [`pending-changes`][check-pending-changes] and [`stage-configure-apply`][stage-configure-apply]
  would always fail if a product is unconfigured, new, or missing a stemcell,
  regardless of whether `ALLOW_PENDING_CHANGES` was set.
  This has been fixed. `pending-changes` will only fail if `ALLOW_PENDING_CHANGES: false`.
- [`stage-product`][stage-product] and [`stage-configure-apply`][stage-configure-apply] 
  will now accept `latest` as the `product-version`
  if you are providing a `CONFIG_FILE`/`STAGE_PRODUCT_CONFIG_FILE`.
  This fixes an issue that required users to update their config file
  every time a new version was available on Ops Manager.
- [`stage-configure-apply`][stage-configure-apply] will now treat the `product` input
  as truly optional if `CONFIG_FILE` is provided. 

### Known Issues
- When using the task [`backup-tkgi`][backup-tkgi] behind a proxy
  the values for `no_proxy` can affect the ssh (though jumpbox) tunneling.
  When the task invokes the `bbr` CLI, an environment variable (`BOSH_ALL_PROXY`) has been set,
  this environment variable tries to honor the `no_proxy` settings.
  The task's usage of the ssh tunnel requires the `no_proxy` to not be set.
  
    If you experience an error, such as an SSH connection refused or connection timeout,
    try setting the `no_proxy: ""` as `params` on the task.
    
    For example,
    
    ```yaml
    - task: backup-tkgi
      file: platform-automation-tasks/tasks/backup-tkgi.yml
      params:
        no_proxy: ""
    ```

## v5.0.4
Released October 2, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.3.0](https://github.com/pivotal-cf/om/releases/tag/6.3.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-5.0.4" target="_blank">Download</a>

### Bug Fixes
- The [`download-and-upload-product`][download-and-upload-product] task did not provide the option to leave the stemcell floating.
  A new param (`FLOATING_STEMCELL`) allows floating for a stemcell to be set.
  Its default value is set to `true`.
  The expectation is to affect one product, not all products.
- The [`backup-tkgi`][backup-tkgi] task had a misnamed param.
  `$deployment_name` has been renamed to `$DEPLOYMENT_NAME` as was necessary.
- CVE update to container image. Resolves [USN-4512-1](https://usn.ubuntu.com/4512-1/).
The CVEs are related to vulnerabilities with `util-linux` and related libraries.
- CVE update to container image. Resolves [USN-4504-1](https://usn.ubuntu.com/4504-1/).
The CVEs are related to vulnerabilities with `libssl` and related libraries.

### Known Issues
- When using the task [`backup-tkgi`][backup-tkgi] behind a proxy
  the values for `no_proxy` can affect the ssh (though jumpbox) tunneling.
  When the task invokes the `bbr` CLI, an environment variable (`BOSH_ALL_PROXY`) has been set,
  this environment variable tries to honor the `no_proxy` settings.
  The task's usage of the ssh tunnel requires the `no_proxy` to not be set.
  
    If you experience an error, such as an SSH connection refused or connection timeout,
    try setting the `no_proxy: ""` as `params` on the task.
    
    For example,
    
    ```yaml
    - task: backup-tkgi
      file: platform-automation-tasks/tasks/backup-tkgi.yml
      params:
        no_proxy: ""
    ```

## v5.0.3
September 15, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.3.0](https://github.com/pivotal-cf/om/releases/tag/6.3.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-5.0.3" target="_blank">Download</a>

### Bug Fixes
- There was an issue with how `om` retrieved credentials
  within the new heuristic logic for collections updates.
  In particular, this impacted the upgrade from TAS 2.6 to 2.7,
  and caused `configure-product` to fail.
  The error message looked something like this:
  
    ```bash
    2020/09/01 06:35:54 could not execute "configure-product": failed to configure product: failed to associate guids for property ".properties.credhub_internal_provider_keys" because:
    request failed: unexpected response from /api/v0/deployed/products/cf-6bdb4038d37667f9f424/credentials/.properties.credhub_internal_provider_keys[0].key:
    HTTP/1.1 404 Not Found
    ...more HTTP headers...
    ```

### Known Issues
- When using the task [`backup-tkgi`][backup-tkgi] behind a proxy
  the values for `no_proxy` can affect the ssh (though jumpbox) tunneling.
  When the task invokes the `bbr` CLI, an environment variable (`BOSH_ALL_PROXY`) has been set,
  this environment variable tries to honor the `no_proxy` settings.
  The task's usage of the ssh tunnel requires the `no_proxy` to not be set.
  
    If you experience an error, such as an SSH connection refused or connection timeout,
    try setting the `no_proxy: ""` as `params` on the task.
    
    For example,
    
    ```yaml
    - task: backup-tkgi
      file: platform-automation-tasks/tasks/backup-tkgi.yml
      params:
        no_proxy: ""
    ```

## v5.0.2
September 9, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.2.0](https://github.com/pivotal-cf/om/releases/tag/6.2.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-5.0.2" target="_blank">Download</a>

### Bug Fixes
- Releasing the vSphere only-image, sorry about that in v5.0.1.
- Bump the CLIs for `om`, `credhub`, and `winfs-injector`.

### Known Issues
- When using the task [`backup-tkgi`][backup-tkgi] behind a proxy
  the values for `no_proxy` can affect the ssh (though jumpbox) tunneling.
  When the task invokes the `bbr` CLI, an environment variable (`BOSH_ALL_PROXY`) has been set,
  this environment variable tries to honor the `no_proxy` settings.
  The task's usage of the ssh tunnel requires the `no_proxy` to not be set.
  
    If you experience an error, such as an SSH connection refused or connection timeout,
    try setting the `no_proxy: ""` as `params` on the task.
    
    For example,
    
    ```yaml
    - task: backup-tkgi
      file: platform-automation-tasks/tasks/backup-tkgi.yml
      params:
        no_proxy: ""
    ```

## v5.0.1
Released September 4, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.1.0](https://github.com/pivotal-cf/om/releases/tag/6.1.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.18.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.18.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-5.0.1" target="_blank">Download</a>

!!! warning "Removed from Releases"
    There was a regression introduced in v5.0.1.
    It will be removed form Tanzu Network.
    Please use v5.0.2 instead.

### Bug Fixes
- tl;dr: If you have experienced the following error with the [`create-vm`][create-vm] task this is fixed.
  
    ```bash
    creating the new opsman vm
    Using gcp...
    Error: unexpected error: could not marshal image file: yaml: unmarshal errors:
      line 6: cannot unmarshal !!map into string
    ```
  
    With GCP OpsManager, the image YAML file format includes a new key.
    
    The original format of the image YAML was:
    
    ```yaml
    ---
    us: ops-manager-us/pcf-gcp-2.9.9-build.164.tar.gz
    eu: ops-manager-us/pcf-gcp-2.9.9-build.164.tar.gz
    asia: ops-manager-us/pcf-gcp-2.9.9-build.164.tar.gz
    ```
    
    The new format includes the `image` key:
    
    ```yaml
    ---
    us: ops-manager-us/pcf-gcp-2.9.10-build.177.tar.gz
    eu: ops-manager-us/pcf-gcp-2.9.10-build.177.tar.gz
    asia: ops-manager-us/pcf-gcp-2.9.10-build.177.tar.gz
    image:
     name: ops-manager-2-9-10-build-177
     project: pivotal-ops-manager-images
    ```
    
    This patch ignores this value, where previously it would've not been able to parse it.

### Known Issues
- When using the task [`backup-tkgi`][backup-tkgi] behind a proxy
  the values for `no_proxy` can affect the ssh (though jumpbox) tunneling.
  When the task invokes the `bbr` CLI, an environment variable (`BOSH_ALL_PROXY`) has been set,
  this environment variable tries to honor the `no_proxy` settings.
  The task's usage of the ssh tunnel requires the `no_proxy` to not be set.
  
    If you experience an error, such as an SSH connection refused or connection timeout,
    try setting the `no_proxy: ""` as `params` on the task.
    
    For example,
    
    ```yaml
    - task: backup-tkgi
      file: platform-automation-tasks/tasks/backup-tkgi.yml
      params:
        no_proxy: ""
    ```

## v5.0.0
Released September 2, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.2.0](https://github.com/pivotal-cf/om/releases/tag/6.2.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-5.0.0" target="_blank">Download</a>

### Breaking Changes
- Platform Automation will now require Concourse 5.0+

- There's an additional docker image for vSphere only.
  Most of our users are on vSphere,
  and excluding other IaaS-specific resources for the image greatly reduces
  file size and security surface area.
  The original image continues to work with all IaaSs, including vSphere,
  but if you use our product on vSphere,
  we recommend switching over to the new image.
  The new image is named:
  `vsphere-platform-automation-image-5.0.0.tar.gz`.
  Note that the filename starts with `vsphere-`
  and uses the alternate file extension `.tar.gz`
  instead of `.tgz`.
  This is to avoid breaking existing globs and patterns.
  See the following (API Declaration Change) for more information.

    If you're getting our image with the Pivnet resource
    as documented in the How-to guides,
    the new `get` configuration would look like this:

    ```yaml
    - get: platform-automation-image
      resource: platform-automation
      params:
        globs: ["vsphere-platform-automation-image-*.tar.gz"]
        unpack: true
    ```  

- Change to API Declaration Notice:

    As of 5.0 we are considering the patterns necessary to specify our files
    on Tanzu Network part of our API.
    Specificially, we will consider it a breaking change
    if any of the following glob patterns for the Platform Automation Toolkit image and tasks
    fail to return a single match
    when used with the `pivnet-resource` and/or `download-product` task:
    
      - `platform-automation-image-*.tgz`             # all IaaSes image
      - `vsphere-platform-automation-image-*.tar.gz`  # vSphere only image
      - `platform-automation-tasks-*.zip`             # tasks


- The deprecated `download-product-s3` task has been removed.
  For the same functionality, please use [`download-product`][download-product]
  and specify the `s3` `source`.

- The [`download-product`][download-product] task
  will no longer copy files to the existing outputs.
  Rather, these files will be written directly.
  This speeds up `download-product` in general,
  especially in systems where space IO might be a constraint.

    This change _*requires*_ Concourse 5.0+.
    If using an older version of Concourse, this task will error.

### What's New
- The [`download-and-upload-product`][download-and-upload-product] task has been added.
  This advanced task optimizes the steps of downloading and uploading a product file to an Ops Manager.
  Before downloading, Ops Manager is checked to see if the product/stemcell has been uploaded already.
  If it has, the download and upload steps are skipped.
  There are no outputs on this task.
  At the moment, this task only supports downloading from Tanzu Network (Pivotal Network).
- The [`backup-product`][backup-product] and [`backup-director`][backup-director] tasks have been added.
  These tasks use [BOSH Backup and Restore][bbr]
  to backup artifacts which can be used to restore your director and products.
  Note, there is no task to automate restoring from a backup.
  Restore cannot be guaranteed to be idempotent, and therefore cannot be safely automated.
  See the [BBR docs][bbr-restore] for information on restoring from a backup.
- The [`backup-tkgi`][backup-tkgi] task has been added.
  This task is specific to the Tanzu Kubernetes Grid Integrated Edition(TKGI) product.
  It will backup the tile _and_ the TKGI clusters.

    To persist this backup to a blobstore, the blobstore resource can match the following regexes:

    - For TKGI tile: `product_*.tgz`
    - For the TKGI clusters: `*_clusters_*.tgz`

    !!! info "PKS CLI may be Temporarily Unavailable"
        During `backup-tkgi`, the PKS CLI is disabled.
        Due to the nature of the backup, some commands may not work as expected.

- [`apply-changes`][apply-changes] now supports the optional input `ERRAND_CONFIG_FILE`.
  If provided, `apply-changes` can enable/disable an errand for a particular run.
  To retrieve the default configuration of your product's errands,
  `om staged-config` can be used.
  The expected format for this errand config is as follows:

    ```yaml
    errands:
      sample-product-1:
        run_post_deploy:
          smoke_tests: default
          push-app: false
        run_pre_delete:
          smoke_tests: true
      sample-product-2:
        run_post_deploy:
          smoke_tests: default
    ```

- [`prepare-tasks-with-secrets`][prepare-tasks-with-secrets] will now inject a params block
  if one is not already present in the task.
- [`stage-configure-apply`][stage-configure-apply] now offers the ability to optionally upload and/or assign a stemcell.
  To upload a stemcell, provide a `stemcell` input as you would for [`upload-stemcell`][upload-stemcell].
  To assign a stemcell, provide an `assign-stemcell-config` input
  (this can be the same as your normal config, but must be mapped to this name in your `pipeline.yml`).

    If you wish to upload a stemcell, there are two new (optional) `params`:<br />
    - `FLOATING_STEMCELL`:
      this is equivalent to the `FLOATING_STEMCELL` param of [`upload-stemcell`][upload-stemcell].<br />
    - `UPLOAD_STEMCELL_CONFIG_FILE`:
      this is equivalent to the `CONFIG_FILE` param of [`upload-stemcell`][upload-stemcell].<br />

    If you wish to assign a specific stemcell to the staged product,
    you need to provide the `assign-stemcell-config` input
    and define the `ASSIGN_STEMCELL_CONFIG_FILE` param.
    This param is equivalent to the `CONFIG_FILE` param of [`assign-stemcell`][assign-stemcell].

- [`run-bosh-errand`][run-bosh-errand] task has been added.
  This task runs a specified BOSH errand directly on the BOSH director
  by tunneling through the Ops Manager.
  As such, any errand run in this way does not have visibility within the Ops Manager.
  *Please note this is an advanced feature, and should be used at your own discretion.* 

### Deprecation Notices
- In future _major_ versions of Platform Automation, the [`credhub-interpolate`][credhub-interpolate] task will be removed.
  Please use the [`prepare-tasks-with-secrets`][prepare-tasks-with-secrets] task in its place.

### Known Issues
- When using the task [`backup-tkgi`][backup-tkgi] behind a proxy
  the values for `no_proxy` can affect the ssh (though jumpbox) tunneling.
  When the task invokes the `bbr` CLI, an environment variable (`BOSH_ALL_PROXY`) has been set,
  this environment variable tries to honor the `no_proxy` settings.
  The task's usage of the ssh tunnel requires the `no_proxy` to not be set.
  
    If you experience an error, such as an SSH connection refused or connection timeout,
    try setting the `no_proxy: ""` as `params` on the task.
    
    For example,
    
    ```yaml
    - task: backup-tkgi
      file: platform-automation-tasks/tasks/backup-tkgi.yml
      params:
        no_proxy: ""
    ```

## v4.4.21
March 9, 2021

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.19.23 |
    | azure-cli | 2.20.0 |
    | bbr-cli | [1.9.1](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.9.1) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.9.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.9.0) |
    | gcloud-cli | 330.0.0 |
    | govc-cli | v0.24.0 |
    | om | 6516c1a327f7bb7ede88c857e5b4d0d58f27f5bc-2021-01-26T10:53:54-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.21" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4738-1](https://ubuntu.com/security/notices/USN-4738-1). The CVEs are related to vulnerabilities with `libssl` and related libraries.
- CVE update to container image. Resolves [USN-4754-1](https://ubuntu.com/security/notices/USN-4754-1). The CVEs are related to vulnerabilities with `python` and related libraries.


## v4.4.20
February 25, 2021

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.19.7 |
    | azure-cli | 2.19.1 |
    | bbr-cli | [1.9.1](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.9.1) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.9.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.9.0) |
    | gcloud-cli | 327.0.0 |
    | govc-cli | v0.24.0 |
    | om | 6516c1a327f7bb7ede88c857e5b4d0d58f27f5bc-2021-01-26T10:53:54-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.20" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4719-1](https://ubuntu.com/security/notices/USN-4719-1).


## v4.4.19
January 15, 2021

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.215 |
    | azure-cli | 2.17.1 |
    | bbr-cli | [1.9.1](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.9.1) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.9.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.9.0) |
    | gcloud-cli | 323.0.0 |
    | govc-cli | v0.24.0 |
    | om | 39fd21c57e46588e76bb07826a2d8809e29382e9-2021-01-12T08:23:20-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.19" target="_blank">Download</a>

### Bug Fixes
- Use [`pip` documented](https://pip.pypa.io/en/stable/installing/) method for installing it on the container image


## v4.4.18
January 5, 2021

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.208 |
    | azure-cli | 2.17.1 |
    | bbr-cli | [1.9.0](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.9.0) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.9.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.9.0) |
    | gcloud-cli | 321.0.0 |
    | govc-cli | v0.24.0 |
    | om | dc7ecb856d9d6e8a5538512922e688bd337ab246-2021-01-04T09:19:13-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |


### Bug Fixes
- CVE update to container image. Resolves [USN-4672-1](https://ubuntu.com/security/notices/USN-4672-1).
  The CVEs are related to vulnerabilities with `unzip` and related libraries.
- CVE update to container image. Resolves [USN-4667-1](https://ubuntu.com/security/notices/USN-4667-1).
  The CVEs are related to vulnerabilities with `apt` and related libraries.
- CVE update to container image. Resolves [USN-4665-1](https://ubuntu.com/security/notices/USN-4665-1).
  The CVEs are related to vulnerabilities with `curl` and related libraries.
- CVE update to container image. Resolves [USN-4662-1](https://ubuntu.com/security/notices/USN-4662-1).
  The CVEs are related to vulnerabilities with `libssl` and related libraries.
- CVE update to container image. Resolves [USN-4677-1](https://ubuntu.com/security/notices/USN-4677-1).
  The CVEs are related to vulnerabilities with `p11` and related libraries.


## v4.4.17

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.189 |
    | azure-cli | 2.15.1 |
    | bbr-cli | [1.8.1](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.8.1) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | gcloud-cli | 319.0.0 |
    | govc-cli | 0.23.0 |
    | om | acfd93675b65c8ca8a7f584cd53796d09e5fc88b-2020-12-03T07:19:52-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

### Features
- [`configure-opsman`][configure-opsman] task can now configure the UAA token expirations and timeouts.

   ```yaml
   tokens-expiration:
     access_token_expiration: 10
     refresh_token_expiration: 10
     session_idle_timeout: 10
   ```

### Bug Fixes
- [`update-runtime-config`][update-runtime-config] task has the `releases` input as optional.
  When looking for `releases`, if the input wasn't there then the task would fail.
  A check has been added to ensure the input is there.
- With long-running tasks (using `om` commands),
  sometimes the authentication token would expire.
  If possible the token will be refreshed.
  This should help with HTTP retries.  
- CVE update to container image. Resolves [USN-4608-1](https://ubuntu.com/security/notices/USN-4608-1).
  The CVEs are related to vulnerabilities with `ca-certificates` and related libraries.
- CVE update to container image. Resolves [USN-4635-1](https://ubuntu.com/security/notices/USN-4635-1).
  The CVEs are related to vulnerabilities with `krb5` and related libraries.

## v4.4.16
November 24, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.184 |
    | azure-cli | 2.15.1 |
    | bbr-cli | [1.8.1](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.8.1) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | gcloud-cli | 319.0.0 |
    | govc-cli | 0.23.0 |
    | om | 3a7d703bacb004220450d5984b01a5ea6ebe5087-2020-11-23T14:34:44-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

### Bug Fixes
- Fixes an issue where `stemcell-heavy` in `download-product` had a regression with boolean values.

## v4.4.15
November 19, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.180 |
    | azure-cli | 2.15.0 |
    | bbr-cli | [1.8.1](https://github.com/cloudfoundry-incubator/bosh-backup-and-restore/releases/tag/v1.8.1) |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | gcloud-cli | 319.0.0 |
    | govc-cli | 0.23.0 |
    | om | d424cdfe525f3d9ec4f7b6995c160d7b80c4a6f1-2020-11-18T09:51:49-07:00 |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.15" target="_blank">Download</a>

### Bug Fixes
- [`prepare-tasks-with-secrets`][prepare-tasks-with-secrets] could not be used with other tasks.
  For example, if you had written custom tasks.
  The `TASK_PATH` was added, so custom paths of tasks could be prepared, too.

## v4.4.13
October 23, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.163 |
    | azure-cli | 2.13.0 |
    | bbr-cli | 1.8.0 |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | gcloud-cli | 315.0.0 |
    | govc-cli | 0.23.0 |
    | om | [6.4.2](https://github.com/pivotal-cf/om/releases/tag/6.4.2) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.13" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4581-1](https://usn.ubuntu.com/4581-1/).
  The CVEs are related to vulnerabilities with `python3.6` and related libraries.
  This affects the all IAAS container images only.
- CVE update to container image. Resolves [USN-4601-1](https://usn.ubuntu.com/4601-1/).
  The CVEs are related to vulnerabilities with `python3-pip` and related libraries.
  This affects the all IAAS container images only.

## v4.4.12
October 14, 2020

!!! note "Updates to CLI versions"
    We've now updated our list of CLI versions.
    It includes the supported IAAS CLIs.

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.157 |
    | azure-cli | 2.13.0 |
    | bosh-cli | [6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | gcloud-cli | 314.0.0 |
    | govc-cli | 0.23.0 |
    | om | [6.4.1](https://github.com/pivotal-cf/om/releases/tag/6.4.1) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.12" target="_blank">Download</a>

### Bug Fixes
- Do to a release packaging issue,
  the previous patch version had issues invoking `openstack` CLI.
  This release ensures this has been fixed.
  We've also added further release testing to ensure it doesn't happen again.



## v4.4.11
October 9, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.4.1](https://github.com/pivotal-cf/om/releases/tag/6.4.1) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.11" target="_blank">Download</a>

### Bug Fixes
- The "bug fixes" for collections in `om` 6.1.2+
  were causing unexpected issues in some tiles.
  The collection work has been reverted
  to its original functionality.
- [`pending-changes`][check-pending-changes] and [`stage-configure-apply`][stage-configure-apply]
  would always fail if a product is unconfigured, new, or missing a stemcell,
  regardless of whether `ALLOW_PENDING_CHANGES` was set.
  This has been fixed. `pending-changes` will only fail if `ALLOW_PENDING_CHANGES: false`.
- [`stage-product`][stage-product] and [`stage-configure-apply`][stage-configure-apply] 
  will now accept `latest` as the `product-version`
  if you are providing a `CONFIG_FILE`/`STAGE_PRODUCT_CONFIG_FILE`.
  This fixes an issue that required users to update their config file
  every time a new version was available on Ops Manager.
- [`stage-configure-apply`][stage-configure-apply] will now treat the `product` input
  as truly optional if `CONFIG_FILE` is provided. 

## v4.4.10
October 2, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.3.0](https://github.com/pivotal-cf/om/releases/tag/6.3.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.10" target="_blank">Download</a>

### Bug Fixes
 - CVE update to container image. Resolves [USN-4512-1](https://usn.ubuntu.com/4512-1/).
   The CVEs are related to vulnerabilities with `util-linux` and related libraries.
 - CVE update to container image. Resolves [USN-4504-1](https://usn.ubuntu.com/4504-1/).
   The CVEs are related to vulnerabilities with `libssl` and related libraries.


## v4.4.9
September 15, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.3.0](https://github.com/pivotal-cf/om/releases/tag/6.3.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.9" target="_blank">Download</a>

### Bug Fixes
- There was an issue with how `om` retrieved credentials
  within the new heuristic logic for collections updates.
  In particular, this impacted the upgrade from TAS 2.6 to 2.7,
  and caused `configure-product` to fail.
  The error message looked something like this:
  
    ```bash
    2020/09/01 06:35:54 could not execute "configure-product": failed to configure product: failed to associate guids for property ".properties.credhub_internal_provider_keys" because:
    request failed: unexpected response from /api/v0/deployed/products/cf-6bdb4038d37667f9f424/credentials/.properties.credhub_internal_provider_keys[0].key:
    HTTP/1.1 404 Not Found
    ...more HTTP headers...
    ```

## v4.4.8
September 9, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.2.0](https://github.com/pivotal-cf/om/releases/tag/6.2.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.8" target="_blank">Download</a>

### Bug Fixes
- Bump the CLIs for `om`, `credhub`, and `winfs-injector`.

## v4.4.7
Released September 4, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.1.0](https://github.com/pivotal-cf/om/releases/tag/6.1.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.18.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.18.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.7" target="_blank">Download</a>

### Bug Fixes
- tl;dr: If you have experienced the following error with the [`create-vm`][create-vm] task this is fixed.
  
    ```bash
    creating the new opsman vm
    Using gcp...
    Error: unexpected error: could not marshal image file: yaml: unmarshal errors:
      line 6: cannot unmarshal !!map into string
    ```
  
    With GCP OpsManager, the image YAML file format includes a new key.
    
    The original format of the image YAML was:
    
    ```yaml
    ---
    us: ops-manager-us/pcf-gcp-2.9.9-build.164.tar.gz
    eu: ops-manager-us/pcf-gcp-2.9.9-build.164.tar.gz
    asia: ops-manager-us/pcf-gcp-2.9.9-build.164.tar.gz
    ```
    
    The new format includes the `image` key:
    
    ```yaml
    ---
    us: ops-manager-us/pcf-gcp-2.9.10-build.177.tar.gz
    eu: ops-manager-us/pcf-gcp-2.9.10-build.177.tar.gz
    asia: ops-manager-us/pcf-gcp-2.9.10-build.177.tar.gz
    image:
     name: ops-manager-2-9-10-build-177
     project: pivotal-ops-manager-images
    ```
    
    This patch ignores this value, where previously it would've not been able to parse it.
    
- The container image has been fixed to support the `registry-image` Concourse resource
- With [`credhub-interpolate`][credhub-interpolate] task,
  users were using secrets as a way to interpolate the same Credhub value to multiple vars values.
  This allowed not having ot repeat the same value in Credhub for each var value.
  Support has been added to the [`prepare-tasks-with-secrets`][prepare-tasks-with-secrets] workflow to support secrets evaluation.
  
    For example, given a `config.yml`,
  
    ```yaml
    product-name: some
    product-properties:
      email-password: ((email-password))
      ssh-password: ((ssh-password))
    ```
  
    And given a `vars.yml`,
    
    ```yaml
    email-password: ((password))
    ssh-password: ((password))
    ```
    
    Each task will now fully evaluate the parameter `((password))` as a value from the Concourse configured secret manager.
    This fixes the issue where `((password))` would have been the actual _string_ value for
    `email-password` and `ssh-password`.

## v4.4.6
Released August 20, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.1.0](https://github.com/pivotal-cf/om/releases/tag/6.1.0) |
    | bosh-cli | [v6.3.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.3.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.18.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.18.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.6" target="_blank">Download</a>

### Bug Fixes
- `configure-product` will no longer assign a new GUID for unnamed collections.
  This means that for some tiles,
  configure-product will now avoid unnecessary changes to collections.
- `download-product` will work with supported versions of TAS Windows
  released after Friday August 20th, 2020.
  These versions do not work with older versions of Platform Automation.
  The TAS Windows tiles on Tanzu Network now include Open Source License files
  in the tile itself.
  Platform Automation needed to bump the winfs-injector version
  to ensure compatibility with this new arrangement.
- CVE updates to container image. Resolves [USN-4466-1](https://ubuntu.com/security/notices/USN-4466-1)
  The CVE is related to vulnerabilities in curl and libcurl.

## v4.4.5
Released July 30, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.1.0](https://github.com/pivotal-cf/om/releases/tag/6.1.0) |
    | bosh-cli | [v6.3.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.3.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.5" target="_blank">Download</a>

### Bug Fixes
- [`prepare-tasks-with-secrets`][prepare-tasks-with-secrets] will now inject a params block
  into the passed in task if it is missing.
- CVE update to container image. Resolves [USN-4416-1](https://usn.ubuntu.com/4416-1/).
  The CVEs are related to vulnerabilities with `libc6` and related libraries.
- CVE update to container image. Resolves [USN-4428-1](https://usn.ubuntu.com/4428-1/).
  The CVEs are related to vulnerabilities with `python2.7`, `python2.7-minimal`, `python3.5`, `python3.5-minimal` and related libraries.

## v4.4.4
Released July 10, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [5.0.0](https://github.com/pivotal-cf/om/releases/tag/5.0.0) |
    | bosh-cli | [v6.3.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.3.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.4" target="_blank">Download</a>

### Bug Fixes
- When using [`update-runtime-config`][update-runtime-config] task,
  we've added the `param` for `RELEASES_GLOB` to help limit the releases being uploaded.
  This is especially useful when using the bosh-io-release concourse resource,
  which has other files besides the `release.tgz` when it peforms a `get`.
- CVE update to container image. Resolves [USN-4402-1](https://usn.ubuntu.com/4402-1/).
  The CVEs are related to vulnerabilities with `curl` and related libraries.

## v4.4.3
Released June 16, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.8.0](https://github.com/pivotal-cf/om/releases/tag/4.8.0) |
    | bosh-cli | [6.2.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.2.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.3" target="_blank">Download</a>

### Bug Fixes
- When using [`create-vm`][create-vm], AWS did not support tagging the VM.
  This has been added to the [AWS opsman config][opsman-config]

    Tags can be added to the config file in two formats:

    ```yaml
    tags: {key: value}
    ```

    or

    ```yaml
    tags:
      - key: value
      - key2: value
    ```

- CVE update to container image. Resolves [USN-4394-1](https://usn.ubuntu.com/4394-1/).
  The CVEs are related to vulnerabilities with `libsqlite`.

## v4.4.2
Released June 9, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.8.0](https://github.com/pivotal-cf/om/releases/tag/4.8.0) |
    | bosh-cli | [6.2.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.2.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.2" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4377-1](https://usn.ubuntu.com/4377-1/).
  The CVEs are related to vulnerabilities with `ca-certificates`.

## v4.4.1
Released June 4, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.8.0](https://github.com/pivotal-cf/om/releases/tag/4.8.0) |
    | bosh-cli | [6.2.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.2.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.4.1" target="_blank">Download</a>

### What's New
- The [`stage-product`][stage-product] and [`stage-configure-apply`][stage-configure-apply] tasks
  have been updated to no longer require a `product` input.

    This change allows tiles to be staged without requiring the product file to be passed to these tasks.
    If the `product` input is not provided,
    the `CONFIG_FILE` and `STAGE_PRODUCT_CONFIG_FILE` params **are required** in their appropriate tasks.

- [`upgrade-opsman`][upgrade-opsman] now supports configuring settings
  on the Ops Manager Settings page in the UI.
  This utilizes the `configure-opsman` command from `om`,
  and runs after the upgrade command.
  Configuration can be added directly to [`opsman.yml`][inputs-outputs-configure-opsman].
  An example of all configurable properties can be found in the "Additional Settings" tab.

- [`configure-opsman`][configure-opsman] task has been added.

    This task supports configuring settings
    on the Ops Manager Settings page in the UI.

    Configuration can be added directly to [`opsman.yml`][inputs-outputs-configure-opsman].
    An example of all configurable properties can be found in the "Additional Settings" tab.

- [`download-product`][download-product] now supports
  specifying a version in the config file for the stemcell
  if the latest stemcell for the product is not desired.

    An example config for downloading a product from Tanzu Network:

    ```yaml
    # download-product.yml
    ---
    pivnet-api-token: token
    pivnet-file-glob: "*.pivotal"
    pivnet-product-slug: product-slug
    product-version: 1.2.3
    stemcell-iaas: aws
    stemcell-version: 90.90
    ```

-  The [`prepare-image`][prepare-image] task has been added.

     This task allows you to temporarily inject a CA onto the Platform Automation image
     for use in subsequent tasks within the same job.

     This updated image _does not need to be persisted_,
     and can be used directly by subsequent tasks with no other changes to `pipeline.yml`.

     The task allows proper ssl validation when using `om` commands.
     To fully take advantage of this feature, remove `skip-ssl-validation: true` from your `env.yml`.

     For an example of how this fits into a `pipeline.yml`, check out the [Ops Manager + Multiple Products pipeline][reference-pipeline]

-  The [`replicate-product`][replicate-product] task has been added.
   This task requires a downloaded product,
   and will output the replicated product for isolation segments.

     Supported products: `p-isolation-segment`, `p-windows-runtime`, `pas-windows`

- The [`update-runtime-config`][update-runtime-config] task has been added.
  *Please note this is an advanced feature, and should be used at your own discretion.*

## v4.3.21
October 23, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.163 |
    | azure-cli | 2.13.0 |
    | bbr-cli | 1.8.0 |
    | bosh-cli | [v6.4.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.1) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | gcloud-cli | 315.0.0 |
    | govc-cli | 0.23.0 |
    | om | [6.4.2](https://github.com/pivotal-cf/om/releases/tag/6.4.2) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.21" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4581-1](https://usn.ubuntu.com/4581-1/).
  The CVEs are related to vulnerabilities with `python3.6` and related libraries.
  This affects the all IAAS container images only.
- CVE update to container image. Resolves [USN-4601-1](https://usn.ubuntu.com/4601-1/).
  The CVEs are related to vulnerabilities with `python3-pip` and related libraries.
  This affects the all IAAS container images only.


## v4.3.20
October 14, 2020

!!! note "Updates to CLI versions"
    We've now updated our list of CLI versions.
    It includes the supported IAAS CLIs.

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | aws-cli | 1.18.157 |
    | azure-cli | 2.13.0 |
    | bosh-cli | [6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | gcloud-cli | 314.0.0 |
    | govc-cli | 0.23.0 |
    | om | [6.4.1](https://github.com/pivotal-cf/om/releases/tag/6.4.1) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.20" target="_blank">Download</a>

### Bug Fixes
- Do to a release packaging issue,
  the previous patch version had issues invoking `openstack` CLI.
  This release ensures this has been fixed.
  We've also added further release testing to ensure it doesn't happen again.



## v4.3.19
October 9, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.4.1](https://github.com/pivotal-cf/om/releases/tag/6.4.1) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.19" target="_blank">Download</a>

### Bug Fixes
- The "bug fixes" for collections in `om` 6.1.2+
  were causing unexpected issues in some tiles.
  The collection work has been reverted
  to its original functionality.
- [`pending-changes`][check-pending-changes] and [`stage-configure-apply`][stage-configure-apply]
  would always fail if a product is unconfigured, new, or missing a stemcell,
  regardless of whether `ALLOW_PENDING_CHANGES` was set.
  This has been fixed. `pending-changes` will only fail if `ALLOW_PENDING_CHANGES: false`.


## v4.3.18
October 2, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.3.0](https://github.com/pivotal-cf/om/releases/tag/6.3.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.18" target="_blank">Download</a>

### Bug Fixes
 - CVE update to container image. Resolves [USN-4512-1](https://usn.ubuntu.com/4512-1/).
   The CVEs are related to vulnerabilities with `util-linux` and related libraries.
 - CVE update to container image. Resolves [USN-4504-1](https://usn.ubuntu.com/4504-1/).
   The CVEs are related to vulnerabilities with `libssl` and related libraries.


## v4.3.17
September 15, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.3.0](https://github.com/pivotal-cf/om/releases/tag/6.3.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.17" target="_blank">Download</a>

### Bug Fixes
- There was an issue with how `om` retrieved credentials
  within the new heuristic logic for collections updates.
  In particular, this impacted the upgrade from TAS 2.6 to 2.7,
  and caused `configure-product` to fail.
  The error message looked something like this:
  
    ```bash
    2020/09/01 06:35:54 could not execute "configure-product": failed to configure product: failed to associate guids for property ".properties.credhub_internal_provider_keys" because:
    request failed: unexpected response from /api/v0/deployed/products/cf-6bdb4038d37667f9f424/credentials/.properties.credhub_internal_provider_keys[0].key:
    HTTP/1.1 404 Not Found
    ...more HTTP headers...
    ```

## v4.3.16
September 9, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.2.0](https://github.com/pivotal-cf/om/releases/tag/6.2.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.16" target="_blank">Download</a>

### Bug Fixes
- Bump the CLIs for `om`, `credhub`, and `winfs-injector`.

## v4.3.15
Released September 4, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.1.0](https://github.com/pivotal-cf/om/releases/tag/6.1.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.18.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.18.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.15" target="_blank">Download</a>

### Bug Fixes
- tl;dr: If you have experienced the following error with the [`create-vm`][create-vm] task this is fixed.
  
    ```bash
    creating the new opsman vm
    Using gcp...
    Error: unexpected error: could not marshal image file: yaml: unmarshal errors:
      line 6: cannot unmarshal !!map into string
    ```
  
    With GCP OpsManager, the image YAML file format includes a new key.
    
    The original format of the image YAML was:
    
    ```yaml
    ---
    us: ops-manager-us/pcf-gcp-2.9.9-build.164.tar.gz
    eu: ops-manager-us/pcf-gcp-2.9.9-build.164.tar.gz
    asia: ops-manager-us/pcf-gcp-2.9.9-build.164.tar.gz
    ```
    
    The new format includes the `image` key:
    
    ```yaml
    ---
    us: ops-manager-us/pcf-gcp-2.9.10-build.177.tar.gz
    eu: ops-manager-us/pcf-gcp-2.9.10-build.177.tar.gz
    asia: ops-manager-us/pcf-gcp-2.9.10-build.177.tar.gz
    image:
     name: ops-manager-2-9-10-build-177
     project: pivotal-ops-manager-images
    ```
    
    This patch ignores this value, where previously it would've not been able to parse it.
    
- The container image has been fixed to support the `registry-image` Concourse resource
- With [`credhub-interpolate`][credhub-interpolate] task,
  users were using secrets as a way to interpolate the same Credhub value to multiple vars values.
  This allowed not having ot repeat the same value in Credhub for each var value.
  Support has been added to the [`prepare-tasks-with-secrets`][prepare-tasks-with-secrets] workflow to support secrets evaluation.
  
    For example, given a `config.yml`,
  
    ```yaml
    product-name: some
    product-properties:
      email-password: ((email-password))
      ssh-password: ((ssh-password))
    ```
  
    And given a `vars.yml`,
    
    ```yaml
    email-password: ((password))
    ssh-password: ((password))
    ```
    
    Each task will now fully evaluate the parameter `((password))` as a value from the Concourse configured secret manager.
    This fixes the issue where `((password))` would have been the actual _string_ value for
    `email-password` and `ssh-password`.
    
## v4.3.14
Released August 20, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.1.0](https://github.com/pivotal-cf/om/releases/tag/6.1.0) |
    | bosh-cli | [v6.3.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.3.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.18.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.18.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.14" target="_blank">Download</a>

### Bug Fixes
- `configure-product` will no longer assign a new GUID for unnamed collections.
  This means that for some tiles,
  configure-product will now avoid unnecessary changes to collections.
- `download-product` will work with supported versions of TAS Windows
  released after Friday August 20th, 2020.
  These versions do not work with older versions of Platform Automation.
  The TAS Windows tiles on Tanzu Network now include Open Source License files
  in the tile itself.
  Platform Automation needed to bump the winfs-injector version
  to ensure compatibility with this new arrangement.
- CVE updates to container image. Resolves [USN-4466-1](https://ubuntu.com/security/notices/USN-4466-1)
  The CVE is related to vulnerabilities in curl and libcurl.

## v4.3.13
Released July 30, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.1.0](https://github.com/pivotal-cf/om/releases/tag/6.1.0) |
    | bosh-cli | [v6.3.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.3.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.13" target="_blank">Download</a>

### Bug Fixes
- [`prepare-tasks-with-secrets`][prepare-tasks-with-secrets] will now inject a params block
  into the passed in task if it is missing.
- CVE update to container image. Resolves [USN-4416-1](https://usn.ubuntu.com/4416-1/).
  The CVEs are related to vulnerabilities with `libc6` and related libraries.
- CVE update to container image. Resolves [USN-4428-1](https://usn.ubuntu.com/4428-1/).
  The CVEs are related to vulnerabilities with `python2.7`, `python2.7-minimal`, `python3.5`, `python3.5-minimal` and related libraries.

## v4.3.12
Released July 10, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [5.0.0](https://github.com/pivotal-cf/om/releases/tag/5.0.0) |
    | bosh-cli | [v6.3.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.3.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.12" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4402-1](https://usn.ubuntu.com/4402-1/).
  The CVEs are related to vulnerabilities with `curl` and related libraries.

## v4.3.11
Released June 15, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.8.0](https://github.com/pivotal-cf/om/releases/tag/4.8.0) |
    | bosh-cli | [6.2.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.2.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.10" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4394-1](https://usn.ubuntu.com/4394-1/).
  The CVEs are related to vulnerabilities with `libsqlite`.

## v4.3.10
Released June 8, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.8.0](https://github.com/pivotal-cf/om/releases/tag/4.8.0) |
    | bosh-cli | [6.2.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.2.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.10" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4376-1](https://usn.ubuntu.com/4376-1/).
  The CVEs are related to vulnerabilities with `libssl`.
- CVE update to container image. Resolves [USN-4377-1](https://usn.ubuntu.com/4377-1/).
  The CVEs are related to vulnerabilities with `ca-certificates`.
- vSphere 7.0 with NSX-T 3.0 experienced a bug when using `create-vm` and `upgrade-opsman`.
  If NSX-T deployed a network that was read in the vCenter as multiple port groups with the same name
  those tasks would fail, and be unable to import the Ops Manager OVA file.

    The `network` property when creating an Ops Manager VM can take two new types of identifiers for identify a network.

    1. If using port groups, the `network` property must be `switch name/port group name`.
       For example, `network: edge-cluster-w01-vc-AZ01-vds01/pas-infrastructure-az1-ls`.
    1. [MO reference](https://kb.vmware.com/s/article/1017126) can also be used.

### Experimental Features
- **EXPERIMENTAL** `config-template` now supports ops manager syslog in tiles.
  In the tile metadata, this property is turned on with the `opsmanager_syslog: true` field.
  Tiles with this property enabled will now add the section to `product.yml` 
  and create defaults in `default-vars.yml`.
- Added shorthand flag consistency to multiple commands.
  `--vars-file` shorthand is `-l` and `--var` shorthand is `-v`
- **EXPERIMENTAL** `config-template` can specify the number of collection ops files using `--size-of-collections`.
  Some use cases required that collections generate more ops-file for usage.
  The default value is still `10`.
- `config-template` has been updated to include placeholders for
  `network_name`, `singleton_availability_zone`, and `service_network_name`
  in `required-vars.yml` when appropriate.
- `config-template` Bug Fix: Required collections now parametrize correctly in `product.yml`.
  In the [om issue](https://github.com/pivotal-cf/om/issues/483)
  for `p-dataflow`, the following was _incorrectly_ returned:
  ```
  .properties.maven_repositories:
    value:
    - key: spring
      password: ((password))
      url: https://repo.spring.io/libs-release
      username: username
  ```

    `config-template` now returns the following correct subsection in `product.yml`:
    ```
    .properties.maven_repositories:
      value:
      - key: spring
        password:
          secret: ((password))
        url: https://repo.spring.io/libs-release
        username: username
    ```

    **if you have used the workaround described in the issue**
    (storing the value as a JSON object)
    you will need to update the credential in Credhub
    to not be a JSON object.
- `config-template` generated `resource-vars.yml`
  that had the potential to conflict with property names
  (spring cloud dataflow had a configurable property called `max_in_flight`
  which is also a resource config property).
  `config-template` now prepends **all** resource-vars with `resource-var-`.
  This prevents this entire class of conflicts.
  If using `config-template` to update vars/ops-files/etc,
  check your resource var names in any files vars may be drawn from.
  This resolves om issue [#484](https://github.com/pivotal-cf/om/issues/484).

## v4.3.8
Released May 20, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.6.0](https://github.com/pivotal-cf/om/releases/tag/4.6.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.8" target="_blank">Download</a>

### Bug Fixes
- _Sometimes_ vsphere `create-vm`/`delete-vm`/`upgrade-opsman` would fail with:
  `govc[stderr]: panic: send on closed channel`
  due to a bug in [govc](https://github.com/vmware/govmomi/issues/1972).

    These tasks have implemented the workaround described in the issue.
- CVE update to container image. Resolves [USN-4359-1](https://usn.ubuntu.com/4359-1/).
  The CVEs are related to vulnerabilities with `apt`.

## v4.3.6
Released April 28, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.6.0](https://github.com/pivotal-cf/om/releases/tag/4.6.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.6" target="_blank">Download</a>

### Bug Fixes
-  The `IGNORE_WARNINGS` parameter for the
   `apply-changes`, `stage-configure-apply`, and `apply-director-changes` tasks
   allows users to ignore all warnings from ignorable verifiers.
   Some verifiers continue to return warnings even when disabled,
   preventing deployment without the `IGNORE_WARNINGS: true` param set.
   If the verifiers that are preventing deployment
   are known issues based on the environment setup,
   then it is safe to use the flag.
   It is _highly recommended_ to disable verifiers before ignoring warnings.
- CVE update to container image. Resolves [USN-4329-1](https://usn.ubuntu.com/4329-1/).
  This CVE is related to vulnerabilities with `git`.
- CVE update to container image. Resolves [USN-4334-1](https://usn.ubuntu.com/4334-1/).
  This CVE is related to vulnerabilities with `git`.
- CVE update to container image. Resolves [USN-4333-1](https://usn.ubuntu.com/4333-1/).
  This CVE is related to vulnerabilities with `python`.
- Adding back the removed `ssh` Ubuntu package.

## v4.3.5
Released April 24, 2020

!!! bug "Known Issue"
    This version attempted to remove some unnecessary dependencies from the image.
    In this process, important utilities may have been removed as well.
    In particular, we know that `ssh` is missing.
    If you use this version and find any vital tools missing, please let us know.
    A forthcoming patch version will restore `ssh` and any other identified tools.

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.6.0](https://github.com/pivotal-cf/om/releases/tag/4.6.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.5" target="_blank">Download</a>

### Bug Fixes
- The `winfs-injector` has been bumped to support the new TAS Windows tile.
  When downloading a product from Pivnet, the [`download-product`][download-product] task
  uses `winfs-injector` to package the Windows rootfs in the tile.
  Newer version of TAS Windows, use a new packaging method, which requires this bump.

    If you see the following error, you need this fix.

    ```
    Checking if product needs winfs injected...+ '[' pas-windows == pas-windows ']'
    + '[' pivnet == pivnet ']'
    ++ basename downloaded-files/pas-windows-2.7.12-build.2.pivotal
    + TILE_FILENAME=pas-windows-2.7.12-build.2.pivotal
    + winfs-injector --input-tile downloaded-files/pas-windows-2.7.12-build.2.pivotal --output-tile downloaded-product/pas-windows-2.7.12-build.2.pivotal
    open /tmp/015434627/extracted-tile/embed/windowsfs-release/src/code.cloudfoundry.org/windows2016fs/2019/IMAGE_TAG: no such file or directory
    ```

## v4.3.4
Released March 25, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.6.0](https://github.com/pivotal-cf/om/releases/tag/4.6.0) |
    | bosh-cli | [6.2.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.2.1) |
    | credhub | [2.6.2](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.2) |
    | winfs-injector | [0.14.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.14.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.4" target="_blank">Download</a>

### Bug Fixes
- The [`prepare-tasks-with-secrets`][prepare-tasks-with-secrets] now correctly allows for an optional vars input.
- `configure-director` now correctly handles when you don't name your iaas_configuration `default` on vSphere.
  Previously, naming a configuration anything other than `default` would result in an extra, empty `default` configuration.
  This closes issue [#469](https://github.com/pivotal-cf/om/issues/469).
- Downloading a stemcell associated with a product will try to download the light or heavy stemcell.
  If anyone has experienced the recent issue with `download-product`
  and the AWS heavy stemcell,
  this will resolve your issue.
  Please remove any custom globbing that might've been added to circumvent this issue.
  For example, `stemcell-iaas: light*aws` should just be `stemcell-iaas: aws` now.
- Heavy stemcells could not be downloaded.
  Support has now been added.
  Define `stemcell-heavy: true` in your [`download-product` config file][download-product-config].
- CVE update to container image. Resolves [USN-4298-1](https://usn.ubuntu.com/4298-1/).
  This CVE is related to vulnerabilities with `libsqlite3`.
- CVE update to container image. Resolves [USN-4305-1](https://usn.ubuntu.com/4305-1/).
  This CVE is related to vulnerabilities with `libicu60`.

### Experimental Features
- **EXPERIMENTAL** `config-template` now includes the option to use a local product file with `--product-path`.

## v4.3.3
Released February 26, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.5.0](https://github.com/pivotal-cf/om/releases/tag/4.5.0) |
    | bosh-cli | [6.2.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.2.1) |
    | credhub | [2.6.2](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.2) |
    | winfs-injector | [0.14.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.14.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.3" target="_blank">Download</a>

### Bug Fixes
- GCP [`create-vm`][create-vm] now correctly handles an empty tags list
- All default VM names are now `ops-manager-vm` to conform with IAAS name requirements.
    - GCP did not allow for capital letters in VM names.
- CVE update to container image. Resolves [USN-4274-1](https://usn.ubuntu.com/4274-1/).
  The CVEs are related to vulnerabilities with `libxml2`.
- Bumped the following low-severity CVE packages: libsystemd0 libudev1

## v4.3.2
February 11, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.4.2](https://github.com/pivotal-cf/om/releases/tag/4.4.2) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.2](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.2) |
    | winfs-injector | [0.14.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.14.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.2" target="_blank">Download</a>

### What's New
- The [config][download-product-config] for the `download-product` task now recommends using `file-glob` instead of `pivnet-file-glob`.

### Bug Fixes
- CVE update to container image. Resolves [USN-4243-1](https://usn.ubuntu.com/4243-1/).
  The CVEs are related to vulnerabilities with `libbsd`.
- CVE update to container image. Resolves [USN-4249-1](https://usn.ubuntu.com/4249-1/).
  The CVEs are related to vulnerabilities with `e2fsprogs`.
- CVE update to container image. Resolves [USN-4233-2](https://usn.ubuntu.com/4233-2/).
  The CVEs are related to vulnerabilities with `libgnutls30`.
- CVE update to container image. Resolves [USN-4256-1](https://usn.ubuntu.com/4256-1/).
  The CVEs are related to vulnerabilities with `libsasl2-2`.
- Bumped the following low-severity CVE packages: `libcom-err2`, `libext2fs2`, `libss2`, `linux-libc-dev`

## v4.3.0
Released January 31, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.4.1](https://github.com/pivotal-cf/om/releases/tag/4.4.1) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.2](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.2) |
    | winfs-injector | [0.14.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.14.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.3.0" target="_blank">Download</a>

### What's New
- The [`revert-staged-changes`][revert-staged-changes] task has been added.
  This allows changes that weren't part of the pipeline to be undone,
  by guaranteeing a clean state before using various `configure-*` tasks.
- The `p-automator` CLI includes the ability to extract the Ops Manager VM configuration for Azure and vSphere.
  This works for Ops Managers that are already running and useful when [migrating to automation][upgrade-how-to].
- The `credhub` cli now returns a list of parameters it could not find when `--skip-missing` is enabled.
  This feature will show up in the [`credhub-interpolate`][credhub-interpolate],
  when `SKIP_MISSING: true` is set.
- The [`prepare-tasks-with-secrets`][prepare-tasks-with-secrets] task has been added.
  It replaces the [`credhub-interpolate`][credhub-interpolate] task and provides the following benefits:
    - Support for all native Concourse secrets stores including Credhub and Vault.
    - Credhub credentials are no longer required by the task so they can be completely handled by concourse.
    - Credentials are no longer written to disk which alleviates some security concerns.

    For a detailed explanation of this new task, see [Using prepare-tasks-with-secrets][prepare-tasks-with-secrets-how-to].
    To replace `credhub-interpolate` with this new task, see [Replacing credhub-interpolate with prepare-tasks-with-secrets][prepare-tasks-with-secrets-replace]. (Note: This task uses a Concourse feature that allows inputs and outputs to have the same name. This feature is only available in Concourse 5+. prepare-tasks-with-secrets does not work with Concourse 4.)

- The docker image includes the correct flavor of `nc` (`netcat-openbsd`) to be used with `bosh ssh`.
- Add the ability to recreate VMs to the [`apply-changes`][apply-changes] and [`stage-configure-apply`][stage-configure-apply] tasks.
    - If `RECREATE: true`, these commands will recreate all product VMs for their relevant product(s).
    - To recreate the BOSH director VM, make any change to the director tile, and apply-changes.
      We recommend modifying the Custom SSH Banner if this is desired.

### Bug Fixes
- The p-automator binary no longer accepts unknown flags for faster debug feedback
- CVE update to container image. Resolves [USN-4236-1](https://usn.ubuntu.com/4236-1/).
  The CVEs are related to vulnerabilities with `Libgcrypt`.
- CVE update to container image. Resolves [USN-4233-1](https://usn.ubuntu.com/4233-1/).
  The CVEs are related to vulnerabilities with `GnuTLS`.

## v4.2.20
September 15, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.3.0](https://github.com/pivotal-cf/om/releases/tag/6.3.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.20" target="_blank">Download</a>

### Bug Fixes
- There was an issue with how `om` retrieved credentials
  within the new heuristic logic for collections updates.
  In particular, this impacted the upgrade from TAS 2.6 to 2.7,
  and caused `configure-product` to fail.
  The error message looked something like this:
  
    ```bash
    2020/09/01 06:35:54 could not execute "configure-product": failed to configure product: failed to associate guids for property ".properties.credhub_internal_provider_keys" because:
    request failed: unexpected response from /api/v0/deployed/products/cf-6bdb4038d37667f9f424/credentials/.properties.credhub_internal_provider_keys[0].key:
    HTTP/1.1 404 Not Found
    ...more HTTP headers...
    ```

## v4.2.19
September 9, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.2.0](https://github.com/pivotal-cf/om/releases/tag/6.2.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.8.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.8.0) |
    | winfs-injector | [0.19.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.19.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.19" target="_blank">Download</a>

### Bug Fixes
- Bump the CLIs for `om`, `credhub`, and `winfs-injector`.

## v4.2.18
Released September 4, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.1.0](https://github.com/pivotal-cf/om/releases/tag/6.1.0) |
    | bosh-cli | [v6.4.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.4.0) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.18.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.18.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.18" target="_blank">Download</a>

### Bug Fixes
- tl;dr: If you have experienced the following error with the [`create-vm`][create-vm] task this is fixed.
  
    ```bash
    creating the new opsman vm
    Using gcp...
    Error: unexpected error: could not marshal image file: yaml: unmarshal errors:
      line 6: cannot unmarshal !!map into string
    ```
  
    With GCP OpsManager, the image YAML file format includes a new key.
    
    The original format of the image YAML was:
    
    ```yaml
    ---
    us: ops-manager-us/pcf-gcp-2.9.9-build.164.tar.gz
    eu: ops-manager-us/pcf-gcp-2.9.9-build.164.tar.gz
    asia: ops-manager-us/pcf-gcp-2.9.9-build.164.tar.gz
    ```
    
    The new format includes the `image` key:
    
    ```yaml
    ---
    us: ops-manager-us/pcf-gcp-2.9.10-build.177.tar.gz
    eu: ops-manager-us/pcf-gcp-2.9.10-build.177.tar.gz
    asia: ops-manager-us/pcf-gcp-2.9.10-build.177.tar.gz
    image:
     name: ops-manager-2-9-10-build-177
     project: pivotal-ops-manager-images
    ```
    
    This patch ignores this value, where previously it would've not been able to parse it.
    
- The container image has been fixed to support the `registry-image` Concourse resource
  
    For example, given a `config.yml`,
  
    ```yaml
    product-name: some
    product-properties:
      email-password: ((email-password))
      ssh-password: ((ssh-password))
    ```
  
    And given a `vars.yml`,
    
    ```yaml
    email-password: ((password))
    ssh-password: ((password))
    ```
    
    Each task will now fully evaluate the parameter `((password))` as a value from the Concourse configured secret manager.
    This fixes the issue where `((password))` would have been the actual _string_ value for
    `email-password` and `ssh-password`.
    
## v4.2.17
Released August 20, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.1.0](https://github.com/pivotal-cf/om/releases/tag/6.1.0) |
    | bosh-cli | [v6.3.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.3.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.18.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.18.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.17" target="_blank">Download</a>

### Bug Fixes
- `configure-product` will no longer assign a new GUID for unnamed collections.
  This means that for some tiles,
  configure-product will now avoid unnecessary changes to collections.
- `download-product` will work with supported versions of TAS Windows
  released after Friday August 20th, 2020.
  These versions do not work with older versions of Platform Automation.
  The TAS Windows tiles on Tanzu Network now include Open Source License files
  in the tile itself.
  Platform Automation needed to bump the winfs-injector version
  to ensure compatibility with this new arrangement.
- CVE updates to container image. Resolves [USN-4466-1](https://ubuntu.com/security/notices/USN-4466-1)
  The CVE is related to vulnerabilities in curl and libcurl.

## v4.2.16
Released July 30, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.1.0](https://github.com/pivotal-cf/om/releases/tag/6.1.0) |
    | bosh-cli | [v6.3.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.3.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.16" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4416-1](https://usn.ubuntu.com/4416-1/).
  The CVEs are related to vulnerabilities with `libc6` and related libraries.
- CVE update to container image. Resolves [USN-4428-1](https://usn.ubuntu.com/4428-1/).
  The CVEs are related to vulnerabilities with `python2.7`, `python2.7-minimal`, `python3.5`, `python3.5-minimal` and related libraries.

## v4.2.15
Released July 10, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [5.0.0](https://github.com/pivotal-cf/om/releases/tag/5.0.0) |
    | bosh-cli | [v6.3.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.3.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.15" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4402-1](https://usn.ubuntu.com/4402-1/).
  The CVEs are related to vulnerabilities with `curl` and related libraries.

## v4.2.14
Released June 15, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.8.0](https://github.com/pivotal-cf/om/releases/tag/4.8.0) |
    | bosh-cli | [6.2.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.2.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.13" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4394-1](https://usn.ubuntu.com/4394-1/).
  The CVEs are related to vulnerabilities with `libsqlite`.

## v4.2.13
Released June 5, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.8.0](https://github.com/pivotal-cf/om/releases/tag/4.8.0) |
    | bosh-cli | [6.2.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.2.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.13" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4376-1](https://usn.ubuntu.com/4376-1/).
  The CVEs are related to vulnerabilities with `libssl`.
- CVE update to container image. Resolves [USN-4377-1](https://usn.ubuntu.com/4377-1/).
  The CVEs are related to vulnerabilities with `ca-certificates`.
- vSphere 7.0 with NSX-T 3.0 experienced a bug when using `create-vm` and `upgrade-opsman`.
  If NSX-T deployed a network that was read in the vCenter as multiple port groups with the same name
  those tasks would fail, and be unable to import the Ops Manager OVA file.

    The `network` property when creating an Ops Manager VM can take two new types of identifiers for identify a network.

    1. If using port groups, the `network` property must be `switch name/port group name`.
       For example, `network: edge-cluster-w01-vc-AZ01-vds01/pas-infrastructure-az1-ls`.
    1. [MO reference](https://kb.vmware.com/s/article/1017126) can also be used.

### Experimental Features
- **EXPERIMENTAL** `config-template` now supports ops manager syslog in tiles.
  In the tile metadata, this property is turned on with the `opsmanager_syslog: true` field.
  Tiles with this property enabled will now add the section to `product.yml`
  and create defaults in `default-vars.yml`.
- Added shorthand flag consistency to multiple commands.
  `--vars-file` shorthand is `-l` and `--var` shorthand is `-v`
- **EXPERIMENTAL** `config-template` can specify the number of collection ops files using `--size-of-collections`.
  Some use cases required that collections generate more ops-file for usage.
  The default value is still `10`.
- `config-template` has been updated to include placeholders for
  `network_name`, `singleton_availability_zone`, and `service_network_name`
  in `required-vars.yml` when appropriate.
- `config-template` Bug Fix: Required collections now parametrize correctly in `product.yml`.
  In the [om issue](https://github.com/pivotal-cf/om/issues/483)
  for `p-dataflow`, the following was _incorrectly_ returned:
  ```
  .properties.maven_repositories:
    value:
    - key: spring
      password: ((password))
      url: https://repo.spring.io/libs-release
      username: username
  ```

    `config-template` now returns the following correct subsection in `product.yml`:
    ```
    .properties.maven_repositories:
      value:
      - key: spring
        password:
          secret: ((password))
        url: https://repo.spring.io/libs-release
        username: username
    ```

    **if you have used the workaround described in the issue**
    (storing the value as a JSON object)
    you will need to update the credential in Credhub
    to not be a JSON object.
- `config-template` generated `resource-vars.yml`
  that had the potential to conflict with property names
  (spring cloud dataflow had a configurable property called `max_in_flight`
  which is also a resource config property).
  `config-template` now prepends **all** resource-vars with `resource-var-`.
  This prevents this entire class of conflicts.
  If using `config-template` to update vars/ops-files/etc,
  check your resource var names in any files vars may be drawn from.
  This resolves om issue [#484](https://github.com/pivotal-cf/om/issues/484).

## v4.2.11
Released May 20, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.6.0](https://github.com/pivotal-cf/om/releases/tag/4.6.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.11" target="_blank">Download</a>

### Bug Fixes
- _Sometimes_ vsphere `create-vm`/`delete-vm`/`upgrade-opsman` would fail with:
  `govc[stderr]: panic: send on closed channel`
  due to a bug in [govc](https://github.com/vmware/govmomi/issues/1972).

    These tasks have implemented the workaround described in the issue.

- CVE update to container image. Resolves [USN-4359-1](https://usn.ubuntu.com/4359-1/).
  The CVEs are related to vulnerabilities with `apt`.

## v4.2.9
Released April 28, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.6.0](https://github.com/pivotal-cf/om/releases/tag/4.6.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.9" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4329-1](https://usn.ubuntu.com/4329-1/).
  This CVE is related to vulnerabilities with `git`.
- CVE update to container image. Resolves [USN-4334-1](https://usn.ubuntu.com/4334-1/).
  This CVE is related to vulnerabilities with `git`.
- CVE update to container image. Resolves [USN-4333-1](https://usn.ubuntu.com/4333-1/).
  This CVE is related to vulnerabilities with `python`.

## v4.2.8
Released April 24, 2020

!!! bug "Known Issue"
    This version attempted to remove some unnecessary dependencies from the image.
    In this process, important utilities may have been removed as well.
    In particular, we know that `ssh` is missing.
    If you use this version and find any vital tools missing, please let us know.
    A forthcoming patch version will restore `ssh` and any other identified tools.

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.6.0](https://github.com/pivotal-cf/om/releases/tag/4.6.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.8" target="_blank">Download</a>

### Bug Fixes
- The `winfs-injector` has been bumped to support the new TAS Windows tile.
  When downloading a product from Pivnet, the [`download-product`][download-product] task
  uses `winfs-injector` to package the Windows rootfs in the tile.
  Newer version of TAS Windows, use a new packaging method, which requires this bump.

    If you see the following error, you need this fix.

    ```
    Checking if product needs winfs injected...+ '[' pas-windows == pas-windows ']'
    + '[' pivnet == pivnet ']'
    ++ basename downloaded-files/pas-windows-2.7.12-build.2.pivotal
    + TILE_FILENAME=pas-windows-2.7.12-build.2.pivotal
    + winfs-injector --input-tile downloaded-files/pas-windows-2.7.12-build.2.pivotal --output-tile downloaded-product/pas-windows-2.7.12-build.2.pivotal
    open /tmp/015434627/extracted-tile/embed/windowsfs-release/src/code.cloudfoundry.org/windows2016fs/2019/IMAGE_TAG: no such file or directory
    ```

## v4.2.7
Released March 25, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.6.0](https://github.com/pivotal-cf/om/releases/tag/4.6.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.14.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.14.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.7" target="_blank">Download</a>

### Bug Fixes
- `configure-director` now correctly handles when you don't name your iaas_configuration `default` on vSphere.
  Previously, naming a configuration anything other than `default` would result in an extra, empty `default` configuration.
  This closes issue [#469](https://github.com/pivotal-cf/om/issues/469).
- Downloading a stemcell associated with a product will try to download the light or heavy stemcell.
  If anyone has experienced the recent issue with `download-product`
  and the AWS heavy stemcell,
  this will resolve your issue.
  Please remove any custom globbing that might've been added to circumvent this issue.
  For example, `stemcall-iaas: light*aws` should just be `stemcell-iaas: aws` now.
- Heavy stemcells could not be downloaded.
  Support has now been added.
  Define `stemcell-heavy: true` in your `download-product` config file.
- CVE update to container image. Resolves [USN-4298-1](https://usn.ubuntu.com/4298-1/).
  This CVE is related to vulnerabilities with `libsqlite3`.
- CVE update to container image. Resolves [USN-4305-1](https://usn.ubuntu.com/4305-1/).
  This CVE is related to vulnerabilities with `libicu60`.

### Experimental Features
- **EXPERIMENTAL** `config-template` now includes the option to use a local product file with `--product-path`.

## v4.2.6
Released February 21, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.3.0](https://github.com/pivotal-cf/om/releases/tag/4.3.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.14.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.14.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.6" target="_blank">Download</a>

### Bug Fixes
- GCP [`create-vm`][create-vm] now correctly handles an empty tags list
- CVE update to container image. Resolves [USN-4274-1](https://usn.ubuntu.com/4274-1/).
  The CVEs are related to vulnerabilities with `libxml2`.
- Bumped the following low-severity CVE packages: libsystemd0 libudev1

## v4.2.5
Released February 10, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.3.0](https://github.com/pivotal-cf/om/releases/tag/4.3.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.14.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.14.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.2.5" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4243-1](https://usn.ubuntu.com/4243-1/).
  The CVEs are related to vulnerabilities with `libbsd`.
- CVE update to container image. Resolves [USN-4249-1](https://usn.ubuntu.com/4249-1/).
  The CVEs are related to vulnerabilities with `e2fsprogs`.
- CVE update to container image. Resolves [USN-4233-2](https://usn.ubuntu.com/4233-2/).
  The CVEs are related to vulnerabilities with `libgnutls30`.
- CVE update to container image. Resolves [USN-4256-1](https://usn.ubuntu.com/4256-1/).
  The CVEs are related to vulnerabilities with `libsasl2-2`.
- Bumped the following low-severity CVE packages: `libcom-err2`, `libext2fs2`, `libss2`, `linux-libc-dev`

## v4.2.4
Released January 28, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.3.0](https://github.com/pivotal-cf/om/releases/tag/4.3.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.14.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.14.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4236-1](https://usn.ubuntu.com/4236-1/).
  The CVEs are related to vulnerabilities with `Libgcrypt`.
- CVE update to container image. Resolves [USN-4233-1](https://usn.ubuntu.com/4233-1/).
  The CVEs are related to vulnerabilities with `GnuTLS`.
- Bumped the following low-severity CVE package: `linux-libc-dev`

## v4.2.3
Released December 12, 2019

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.3.0](https://github.com/pivotal-cf/om/releases/tag/4.3.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.14.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.14.0) |

### Bug Fixes
- When specifying `StorageSKU` for azure, `p-automator` would append `--storage-sku` twice in the creating VM invocation.
  It does not affect anything, but we removed the second instance to avoid confusion.
- CVE update to container image. Resolves [USN-4220-1](https://usn.ubuntu.com/4220-1/).
  The CVEs are related to vulnerabilities with `git`.
- Bumped the following low-severity CVE package: `linux-libc-dev`

## v4.2.2
Released December 3, 2019

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.3.0](https://github.com/pivotal-cf/om/releases/tag/4.3.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.14.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.14.0) |

### What's New
- The `p-automator` CLI includes the ability to extract the Ops Manager VM configuration (GCP and AWS Only at the moment).
  This works for Ops Managers that are already running and useful when [migrating to automation][upgrade-how-to].

  Usage:

  1. Get the Platform Automation Toolkit image from Tanzu Network.
  1. Import that image into `docker` to run the [`p-automation` locally][running-commands-locally].
  1. Create a [state file][state] that represents your current VM and IAAS.
  1. Invoke the `p-automator` CLI to get the configuration.

  For example, on AWS with an access key and secret key:

  ```bash
  docker run -it --rm -v $PWD:/workspace -w /workspace platform-automation-image \
    p-automator export-opsman-config \
    --state-file=state.yml \
    --aws-region=us-west-1 \
    --aws-secret-access-key some-secret-key \
    --aws-access-key-id some-access-key
  ```

  The outputted `opsman.yml` contains the information needed for Platform Automation Toolkit to manage the Ops Manager VM.

- When creating an `create-vm` task for Azure,
  the disk type and VM type can be specified.
  The configuration `storage_sku` and `vm_size` use the Azure values accordingly.
- The [`download-product`][download-product] task now supports the `SOURCE` param
  to specify where to download products and stemcells from.
  The supported sources are the Azure(`azure`), GCS(`gcs`), S3(`s3`), Tanzu Network(`pivnet`).
- [`configure-authentication`][configure-authentication],
  [`configure-ldap-authentication`][configure-ldap-authentication], and
  [`configure-saml-authentication`][configure-saml-authentication]
  now support passing through vars files to the underlying `om` command.
- When using [`configure-product`][configure-product] and [`configure-director`][configure-director],
  the `additional_vm_extensions` for a resource will have the following behaviour:
    - If not set in config file, the value from Ops Manager will be persisted.
    - If defined in the config file and an emtpy array (`[]`), the values on Ops Manager will be removed.
    - If defined in the file with a value (`["web_lb"]`), these values will be set on Ops Manager.
- When using [`configure-director`][configure-director]
  `vmextensions-configuration` can be defined to add|remove vm_extensions
  to|from the BOSH director. An example of this in the config:

    ```yaml
    vmextensions-configuration:
    - name: a_vm_extension
      cloud_properties:
        source_dest_check: false
    - name: another_vm_extension
      cloud_properties:
        foo: bar
    ```

### Deprecation Notices
- The `download-product-s3` task has been deprecated
  in favor of the [`download-product`][download-product] task and setting the `SOURCE: s3` in `params`.

    For example, the `download-product-s3` in a pipeline:

    ```yaml
    - task: download-pas
      image: platform-automation-image
      file: platform-automation-tasks/tasks/download-product-s3.yml
      params:
        CONFIG_FILE: download-product/pas.yml
    ```

    Will be changed to:

    ```yaml
    - task: download-pas
      image: platform-automation-image
      file: platform-automation-tasks/tasks/download-product.yml
      params:
        CONFIG_FILE: download-product/pas.yml
        SOURCE: s3
    ```

### Bug Fixes
- When creating a Ops Manager on Azure,
  there was a bug in offline environments.
  We are now using the full image reference ID when creating the VM.
- CVE update to container image. Resolves [USN-4205-1](https://usn.ubuntu.com/4205-1/).
  This CVE is related to vulnerabilities with `libsqlite3`.
  None of our code calls `libsqlite3` directly, but the IaaS CLIs rely on this package.

## v4.1.22
Released August 20, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.1.0](https://github.com/pivotal-cf/om/releases/tag/6.1.0) |
    | bosh-cli | [v6.3.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.3.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.18.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.18.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.1.22" target="_blank">Download</a>

### Bug Fixes
- `configure-product` will no longer assign a new GUID for unnamed collections.
  This means that for some tiles,
  configure-product will now avoid unnecessary changes to collections.
- `download-product` will work with supported versions of TAS Windows
  released after Friday August 20th, 2020.
  These versions do not work with older versions of Platform Automation.
  The TAS Windows tiles on Tanzu Network now include Open Source License files
  in the tile itself.
  Platform Automation needed to bump the winfs-injector version
  to ensure compatibility with this new arrangement.
- CVE updates to container image. Resolves [USN-4466-1](https://ubuntu.com/security/notices/USN-4466-1)
  The CVE is related to vulnerabilities in curl and libcurl.

## v4.1.21
Released July 30, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [6.1.0](https://github.com/pivotal-cf/om/releases/tag/6.1.0) |
    | bosh-cli | [v6.3.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.3.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.1.21" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4416-1](https://usn.ubuntu.com/4416-1/).
  The CVEs are related to vulnerabilities with `libc6` and related libraries.
- CVE update to container image. Resolves [USN-4428-1](https://usn.ubuntu.com/4428-1/).
  The CVEs are related to vulnerabilities with `python2.7`, `python2.7-minimal`, `python3.5`, `python3.5-minimal` and related libraries.

## v4.1.20
Released July 10, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [5.0.0](https://github.com/pivotal-cf/om/releases/tag/5.0.0) |
    | bosh-cli | [v6.3.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.3.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.1.20" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4394-1](https://usn.ubuntu.com/4394-1/).
  The CVEs are related to vulnerabilities with `libsqlite`.

## v4.1.19
Released June 15, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.8.0](https://github.com/pivotal-cf/om/releases/tag/4.8.0) |
    | bosh-cli | [6.2.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.2.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.1.19" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4394-1](https://usn.ubuntu.com/4394-1/).
  The CVEs are related to vulnerabilities with `libsqlite`.

## v4.1.18
Released June 5, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.8.0](https://github.com/pivotal-cf/om/releases/tag/4.8.0) |
    | bosh-cli | [6.2.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.2.1) |
    | credhub | [2.7.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.7.0) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.1.18" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4376-1](https://usn.ubuntu.com/4376-1/).
  The CVEs are related to vulnerabilities with `libssl`.
- CVE update to container image. Resolves [USN-4377-1](https://usn.ubuntu.com/4377-1/).
  The CVEs are related to vulnerabilities with `ca-certificates`.
- vSphere 7.0 with NSX-T 3.0 experienced a bug when using `create-vm` and `upgrade-opsman`.
  If NSX-T deployed a network that was read in the vCenter as multiple port groups with the same name
  those tasks would fail, and be unable to import the Ops Manager OVA file.

    The `network` property when creating an Ops Manager VM can take two new types of identifiers for identify a network.

    1. If using port groups, the `network` property must be `switch name/port group name`.
       For example, `network: edge-cluster-w01-vc-AZ01-vds01/pas-infrastructure-az1-ls`.
    1. [MO reference](https://kb.vmware.com/s/article/1017126) can also be used.

### Experimental Features
- **EXPERIMENTAL** `config-template` now supports ops manager syslog in tiles.
  In the tile metadata, this property is turned on with the `opsmanager_syslog: true` field.
  Tiles with this property enabled will now add the section to `product.yml`
  and create defaults in `default-vars.yml`.
- Added shorthand flag consistency to multiple commands.
  `--vars-file` shorthand is `-l` and `--var` shorthand is `-v`
- **EXPERIMENTAL** `config-template` can specify the number of collection ops files using `--size-of-collections`.
  Some use cases required that collections generate more ops-file for usage.
  The default value is still `10`.
- `config-template` has been updated to include placeholders for
  `network_name`, `singleton_availability_zone`, and `service_network_name`
  in `required-vars.yml` when appropriate.
- `config-template` Bug Fix: Required collections now parametrize correctly in `product.yml`.
  In the [om issue](https://github.com/pivotal-cf/om/issues/483)
  for `p-dataflow`, the following was _incorrectly_ returned:
  ```
  .properties.maven_repositories:
    value:
    - key: spring
      password: ((password))
      url: https://repo.spring.io/libs-release
      username: username
  ```

    `config-template` now returns the following correct subsection in `product.yml`:
    ```
    .properties.maven_repositories:
      value:
      - key: spring
        password:
          secret: ((password))
        url: https://repo.spring.io/libs-release
        username: username
    ```

    **if you have used the workaround described in the issue**
    (storing the value as a JSON object)
    you will need to update the credential in Credhub
    to not be a JSON object.
- `config-template` generated `resource-vars.yml`
  that had the potential to conflict with property names
  (spring cloud dataflow had a configurable property called `max_in_flight`
  which is also a resource config property).
  `config-template` now prepends **all** resource-vars with `resource-var-`.
  This prevents this entire class of conflicts.
  If using `config-template` to update vars/ops-files/etc,
  check your resource var names in any files vars may be drawn from.
  This resolves om issue [#484](https://github.com/pivotal-cf/om/issues/484).

## v4.1.16
Released May 14, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.6.0](https://github.com/pivotal-cf/om/releases/tag/4.6.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.1.16" target="_blank">Download</a>

### Bug Fixes
- _Sometimes_ vsphere `create-vm`/`delete-vm`/`upgrade-opsman` would fail with:
  `govc[stderr]: panic: send on closed channel`
  due to a bug in [govc](https://github.com/vmware/govmomi/issues/1972).

    These tasks have implemented the workaround described in the issue.

- CVE update to container image. Resolves [USN-4359-1](https://usn.ubuntu.com/4359-1/).
  The CVEs are related to vulnerabilities with `apt`.

## v4.1.14
Released April 28, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.6.0](https://github.com/pivotal-cf/om/releases/tag/4.6.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.1.14" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4329-1](https://usn.ubuntu.com/4329-1/).
  This CVE is related to vulnerabilities with `git`.
- CVE update to container image. Resolves [USN-4334-1](https://usn.ubuntu.com/4334-1/).
  This CVE is related to vulnerabilities with `git`.
- CVE update to container image. Resolves [USN-4333-1](https://usn.ubuntu.com/4333-1/).
  This CVE is related to vulnerabilities with `python`.
- Adding back the removed `ssh` Ubuntu package.

## v4.1.13
Released April 20, 2020

!!! bug "Known Issue"
    This version attempted to remove some unnecessary dependencies from the image.
    In this process, important utilities may have been removed as well.
    In particular, we know that `ssh` is missing.
    If you use this version and find any vital tools missing, please let us know.
    A forthcoming patch version will restore `ssh` and any other identified tools.

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.6.0](https://github.com/pivotal-cf/om/releases/tag/4.6.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.1.13" target="_blank">Download</a>

### Bug Fixes
- The `winfs-injector` has been bumped to support the new TAS Windows tile.
  When downloading a product from Pivnet, the [`download-product`][download-product] task
  uses `winfs-injector` to package the Windows rootfs in the tile.
  Newer version of TAS Windows, use a new packaging method, which requires this bump.

    If you see the following error, you need this fix.

    ```
    Checking if product needs winfs injected...+ '[' pas-windows == pas-windows ']'
    + '[' pivnet == pivnet ']'
    ++ basename downloaded-files/pas-windows-2.7.12-build.2.pivotal
    + TILE_FILENAME=pas-windows-2.7.12-build.2.pivotal
    + winfs-injector --input-tile downloaded-files/pas-windows-2.7.12-build.2.pivotal --output-tile downloaded-product/pas-windows-2.7.12-build.2.pivotal
    open /tmp/015434627/extracted-tile/embed/windowsfs-release/src/code.cloudfoundry.org/windows2016fs/2019/IMAGE_TAG: no such file or directory
    ```

## v4.1.12
Released March 25, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.6.0](https://github.com/pivotal-cf/om/releases/tag/4.6.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.14.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.14.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.1.12" target="_blank">Download</a>

### Bug Fixes
- `configure-director` now correctly handles when you don't name your iaas_configuration `default` on vSphere.
  Previously, naming a configuration anything other than `default` would result in an extra, empty `default` configuration.
  This closes issue [#469](https://github.com/pivotal-cf/om/issues/469).
- Downloading a stemcell associated with a product will try to download the light or heavy stemcell.
  If anyone has experienced the recent issue with `download-product`
  and the AWS heavy stemcell,
  this will resolve your issue.
  Please remove any custom globbing that might've been added to circumvent this issue.
  For example, `stemcall-iaas: light*aws` should just be `stemcell-iaas: aws` now.
- Heavy stemcells could not be downloaded.
  Support has now been added.
  Define `stemcell-heavy: true` in your `download-product` config file.
- CVE update to container image. Resolves [USN-4298-1](https://usn.ubuntu.com/4298-1/).
  This CVE is related to vulnerabilities with `libsqlite3`.
- CVE update to container image. Resolves [USN-4305-1](https://usn.ubuntu.com/4305-1/).
  This CVE is related to vulnerabilities with `libicu60`.

### Experimental Features
- **EXPERIMENTAL** `config-template` now includes the option to use a local product file with `--product-path`.


## v4.1.11
Released February 25, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.2.1](https://github.com/pivotal-cf/om/releases/tag/4.2.1) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.1.11" target="_blank">Download</a>

### Bug Fixes
- GCP [`create-vm`][create-vm] now correctly handles an empty tags list
- CVE update to container image. Resolves [USN-4274-1](https://usn.ubuntu.com/4274-1/).
  The CVEs are related to vulnerabilities with `libxml2`.
- Bumped the following low-severity CVE packages: libsystemd0 libudev1

## v4.1.10
Released February 7, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.2.1](https://github.com/pivotal-cf/om/releases/tag/4.2.1) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.1.10" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4243-1](https://usn.ubuntu.com/4243-1/).
  The CVEs are related to vulnerabilities with `libbsd`.
- CVE update to container image. Resolves [USN-4249-1](https://usn.ubuntu.com/4249-1/).
  The CVEs are related to vulnerabilities with `e2fsprogs`.
- CVE update to container image. Resolves [USN-4233-2](https://usn.ubuntu.com/4233-2/).
  The CVEs are related to vulnerabilities with `libgnutls30`.
- CVE update to container image. Resolves [USN-4256-1](https://usn.ubuntu.com/4256-1/).
  The CVEs are related to vulnerabilities with `libsasl2-2`.
- Bumped the following low-severity CVE packages: `libcom-err2`, `libext2fs2`, `libss2`, `linux-libc-dev`

## v4.1.9
Released January 22, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.2.1](https://github.com/pivotal-cf/om/releases/tag/4.2.1) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4236-1](https://usn.ubuntu.com/4236-1/).
  The CVEs are related to vulnerabilities with `Libgcrypt`.
- CVE update to container image. Resolves [USN-4233-1](https://usn.ubuntu.com/4233-1/).
  The CVEs are related to vulnerabilities with `GnuTLS`.

## v4.1.8
Released December 12, 2019

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.2.1](https://github.com/pivotal-cf/om/releases/tag/4.2.1) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4220-1](https://usn.ubuntu.com/4220-1/).
  The CVEs are related to vulnerabilities with `git`.
- Bumped the following low-severity CVE package: `linux-libc-dev`

## v4.1.7
Released December 3, 2019

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.2.1](https://github.com/pivotal-cf/om/releases/tag/4.2.1) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4205-1](https://usn.ubuntu.com/4205-1/).
  This CVE is related to vulnerabilities with `libsqlite3`.
  None of our code calls `libsqlite3` directly, but the IaaS CLIs rely on this package.
- When using the `check-pending-changes` task,
  it would not work because it reference a script that did not exist.
  The typo has been fixed and tested in the reference pipeline.
- Bumped the following low-severity CVE package: `linux-libc-dev`

## v4.1.5
Released November 19, 2019

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.2.1](https://github.com/pivotal-cf/om/releases/tag/4.2.1) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4172-1](https://usn.ubuntu.com/4172-1/).
  This CVE is related to vulnerabilities with `file` and `libmagic`.
- CVE update to container image. Resolves [USN-4168-1](https://usn.ubuntu.com/4168-1/).
  This CVE is related to vulnerabilities with `libidn2`.
- Bump `bosh` CLI to v6.1.1
- Bump `credhub` CLI to v2.6.1

### Experimental Features
- **EXPERIMENTAL** `config-template` now supports the `--config`, `--var`, `--vars-file`, and `--vars-env` flags.
- **EXPERIMENTAL** `config-template` now includes `max-in-flight` for all resources.

## v4.1.2
Released October 21, 2019

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [4.1.0](https://github.com/pivotal-cf/om/releases/tag/4.1.0) |
    | bosh-cli | [6.1.0](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.0) |
    | credhub | [2.6.0](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.0) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### What's New
- [Ops Manager config for vSphere][inputs-outputs-vsphere] now validates the required properties
- The new task [expiring-certificates]
  fails if there are any expiring certificates
  in a user specified time range.
  Root CAs cannot be included in this list until Ops Manager 2.7.

  Example Output:

  ```text
  Getting expiring certificates...
  [X] Ops Manager
      cf-79fba6887e8c29375eb7:
          .uaa.service_provider_key_credentials: expired on 09 Aug 19 17:05 UTC
  could not execute "expiring-certificates": found expiring certs in the foundation
  exit status 1
  ```

- [Telemetry][telemetry-docs] support has been added!
  To opt in, you must get the Telemetry tool from [Tanzu Network][telemetry],
  create a [config file][telemetry-config],
  and add the [collect-telemetry][collect-telemetry] and [send-telemetry][send-telemetry] tasks to your pipeline.
  For an example, please see the [Reference Pipelines][reference-pipeline].
- [stage-configure-apply][stage-configure-apply] task has been added.
  This task will take a product, stage it, configure it, and apply changes
  _only_ for that product (all other products remain unchanged).
  Use this task only if you have confidence in the ordering
  in which you apply-changes for your products.
- [check-pending-changes][check-pending-changes] task has been added.
  This task will perform a check on Ops Manager and fail if there are pending changes.
  This is useful when trying to prevent manual changes
  from being applied during the automation process.
- The VM state files currently support YAML,
  but when generated, JSON was outputted.
  This caused confusion.
  The generated state file is now outputted as YAML.

### Deprecation Notices
- The `host` field in the vcenter section of the [vsphere opsman.yml][inputs-outputs-vsphere] has been deprecated.
  Platform Automation Toolkit can initially choose where the VM is placed
  but cannot guarantee that it stays there
  or that other generated VMs are assigned to the same host.
- The `vpc_subnet` field in [azure_opsman.yml][inputs-outputs-azure] has been deprecated.
  In your opsman.yml, replace `vpc_subnet` with `subnet_id`.
  This change was to help mitigate confusion
  as VPC is an AWS, not an Azure, concept.
- The optional `use_unmanaged_disk` field in [azure_opsman.yml][inputs-outputs-azure] has been deprecated.
  In your opsman.yml, replace `use_unmanaged_disk: true` with `use_managed_disk: false`.
  The default for `use_managed_disk` is true.
  Unmanaged disk is not recommended by Azure.
  If you would like to use unmanaged disks,
  please opt-out by setting `use_managed_disk: false`.
- The optional `use_instance_profile` field in [aws_opsman.yml][inputs-outputs-aws] has been deprecated.
  It was redundant.
  When you don't specify `access_key_id` and `secret_access_key`,
  the authentication will try to use the instance profile on the executing machine -- for example, a concourse worker.
  This is works in conjunction of how the `aws` CLI find authentication.
- The required `security_group_id` field in [aws_opsman.yml][inputs-outputs-aws] has been deprecated.
  Replace `security_group_id` with `security_group_ids` as YAML array.
  For example, `security_group_id: sg-1`
  becomes `security_group_ids: [ sg-1 ]`.
  This allows the specification of multiple security groups to the Ops Manager VM.

### Bug Fixes
- CVE update to container image. Resolves [USN-4151-1](https://usn.ubuntu.com/4151-1/).
  This CVE is related to vulnerabilities with `python`.
  None of our code calls `python` directly, but the IaaS CLIs rely on this package.

### Experimental Features
- **EXPERIMENTAL** `config-template` now accepts `--pivnet-file-glob` instead of `--product-file-glob`.
  This is to create consistency with the `download-product` command's naming conventions.
  (PR: @poligraph)
   
## v4.0.16
Released May 14, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.2.3](https://github.com/pivotal-cf/om/releases/tag/3.2.3) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.0.16" target="_blank">Download</a>

### Bug Fixes
- _Sometimes_ vsphere `create-vm`/`delete-vm`/`upgrade-opsman` would fail with:
  `govc[stderr]: panic: send on closed channel`
  due to a bug in [govc](https://github.com/vmware/govmomi/issues/1972).

    These tasks have implemented the workaround described in the issue.

- CVE update to container image. Resolves [USN-4359-1](https://usn.ubuntu.com/4359-1/).
  The CVEs are related to vulnerabilities with `apt`.

## v4.0.14
Released April 28, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.2.3](https://github.com/pivotal-cf/om/releases/tag/3.2.3) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.0.14" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4329-1](https://usn.ubuntu.com/4329-1/).
  This CVE is related to vulnerabilities with `git`.
- CVE update to container image. Resolves [USN-4334-1](https://usn.ubuntu.com/4334-1/).
  This CVE is related to vulnerabilities with `git`. 
- CVE update to container image. Resolves [USN-4333-1](https://usn.ubuntu.com/4333-1/).
  This CVE is related to vulnerabilities with `python`. 
- Adding back the removed `ssh` Ubuntu package.

## v4.0.13
Released April 20, 2020

!!! bug "Known Issue"
    This version attempted to remove some unnecessary dependencies from the image.
    In this process, important utilities may have been removed as well.
    In particular, we know that `ssh` is missing.
    If you use this version and find any vital tools missing, please let us know.
    A forthcoming patch version will restore `ssh` and any other identified tools.

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.2.3](https://github.com/pivotal-cf/om/releases/tag/3.2.3) |
    | bosh-cli | [6.2.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.2.1) |
    | credhub | [2.6.2](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.2) |
    | winfs-injector | [0.16.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.16.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.0.13" target="_blank">Download</a>

### Bug Fixes
- The `winfs-injector` has been bumped to support the new TAS Windows tile.
  When downloading a product from Pivnet, the [`download-product`][download-product] task
  uses `winfs-injector` to package the Windows rootfs in the tile.
  Newer version of TAS Windows, use a new packaging method, which requires this bump.
  
    If you see the following error, you need this fix.
  
    ```
    Checking if product needs winfs injected...+ '[' pas-windows == pas-windows ']'
    + '[' pivnet == pivnet ']'
    ++ basename downloaded-files/pas-windows-2.7.12-build.2.pivotal
    + TILE_FILENAME=pas-windows-2.7.12-build.2.pivotal
    + winfs-injector --input-tile downloaded-files/pas-windows-2.7.12-build.2.pivotal --output-tile downloaded-product/pas-windows-2.7.12-build.2.pivotal
    open /tmp/015434627/extracted-tile/embed/windowsfs-release/src/code.cloudfoundry.org/windows2016fs/2019/IMAGE_TAG: no such file or directory
    ``` 

## v4.0.12
Released March 25, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.2.3](https://github.com/pivotal-cf/om/releases/tag/3.2.3) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.14.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.14.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.0.12" target="_blank">Download</a>

### Bug Fixes
- Downloading a stemcell associated with a product will try to download the light or heavy stemcell.
  If anyone has experienced the recent issue with `download-product`
  and the AWS heavy stemcell,
  this will resolve your issue.
  Please remove any custom globbing that might've been added to circumvent this issue.
  For example, `stemcall-iaas: light*aws` should just be `stemcell-iaas: aws` now. 
- CVE update to container image. Resolves [USN-4298-1](https://usn.ubuntu.com/4298-1/).
  This CVE is related to vulnerabilities with `libsqlite3`.
- CVE update to container image. Resolves [USN-4305-1](https://usn.ubuntu.com/4305-1/).
  This CVE is related to vulnerabilities with `libicu60`.

### Experimental Features
- **EXPERIMENTAL** `config-template` now supports the `--exclude-version` flag.
  If provided, the command will exclude the version directory in the `--output-directory` tree.
  The contents will with or without the flag will remain the same.
  Please note including the `--exclude-version` flag
  will make it more difficult to track changes between versions
  unless using a version control system (such as git).
- **EXPERIMENTAL** `config-template` supports `--pivnet-disable-ssl` to skip SSL validation.
- When using `config-template` (**EXPERIMENTAL**) or `download-product`,
  the `--pivnet-skip-ssl` is honored when capturing the token.

## v4.0.11
Released February 21, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.1.0](https://github.com/pivotal-cf/om/releases/tag/3.1.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.0.11" target="_blank">Download</a>

### Bug Fixes
- GCP [`create-vm`][create-vm] now correctly handles an empty tags list
- CVE update to container image. Resolves [USN-4274-1](https://usn.ubuntu.com/4274-1/).
  The CVEs are related to vulnerabilities with `libxml2`.
- Bumped the following low-severity CVE packages: libsystemd0 libudev1

## v4.0.10
Released February 4, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.1.0](https://github.com/pivotal-cf/om/releases/tag/3.1.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-4.0.10" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4243-1](https://usn.ubuntu.com/4243-1/).
  The CVEs are related to vulnerabilities with `libbsd`.
- CVE update to container image. Resolves [USN-4249-1](https://usn.ubuntu.com/4249-1/).
  The CVEs are related to vulnerabilities with `e2fsprogs`.
- CVE update to container image. Resolves [USN-4233-2](https://usn.ubuntu.com/4233-2/).
  The CVEs are related to vulnerabilities with `libgnutls30`.
- CVE update to container image. Resolves [USN-4256-1](https://usn.ubuntu.com/4256-1/).
  The CVEs are related to vulnerabilities with `libsasl2-2`.
- Bumped the following low-severity CVE packages: `libcom-err2`, `libext2fs2`, `libss2`, `linux-libc-dev`

## v4.0.9
Released January 22, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.1.0](https://github.com/pivotal-cf/om/releases/tag/3.1.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4236-1](https://usn.ubuntu.com/4236-1/).
  The CVEs are related to vulnerabilities with `Libgcrypt`.
- CVE update to container image. Resolves [USN-4233-1](https://usn.ubuntu.com/4233-1/).
  The CVEs are related to vulnerabilities with `GnuTLS`.
- Bumped the following low-severity CVE package: `linux-libc-dev`

## v4.0.8
Released December 12, 2019

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.1.0](https://github.com/pivotal-cf/om/releases/tag/3.1.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4220-1](https://usn.ubuntu.com/4220-1/).
  The CVEs are related to vulnerabilities with `git`.
- Bumped the following low-severity CVE package: `linux-libc-dev`

## v4.0.7
Released December 3, 2019

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.1.0](https://github.com/pivotal-cf/om/releases/tag/3.1.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4205-1](https://usn.ubuntu.com/4205-1/).
  This CVE is related to vulnerabilities with `libsqlite3`.
  None of our code calls `libsqlite3` directly, but the IaaS CLIs rely on this package.

## v4.0.6
Released November 6, 2019

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.1.0](https://github.com/pivotal-cf/om/releases/tag/3.1.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4172-1](https://usn.ubuntu.com/4172-1/).
  This CVE is related to vulnerabilities with `file` and `libmagic`.
- CVE update to container image. Resolves [USN-4168-1](https://usn.ubuntu.com/4168-1/).
  This CVE is related to vulnerabilities with `libidn2`.
- Bump `bosh` CLI to v6.1.1
- Bump `credhub` CLI to v2.6.1

## v4.0.5
Released October 25, 2019

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.1.0](https://github.com/pivotal-cf/om/releases/tag/3.1.0) |
    | bosh-cli | [5.5.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v5.5.1) |
    | credhub | [2.5.2](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.5.2) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4151-1](https://usn.ubuntu.com/4151-1/).
  This CVE is related to vulnerabilities with `python`.
  None of our code calls `python` directly, but the IaaS CLIs rely on this package.  

## v4.0.4

Released October 15, 2019, includes `om` version [3.1.0](https://github.com/pivotal-cf/om/releases/tag/3.1.0)

### Bug Fixes
- CVE update to container image. Resolves [USN-4142-1](https://usn.ubuntu.com/4142-1/).
  (related to vulnerabilities with `e2fsprogs`. While none of our code directly used these,
  they are present on the image.)
- Bumped the following low-severity CVE packages: `libcom-err2`, `libext2fs2`, `libss2`, `linux-libc-dev`

## v4.0.3

Released September 27, 2019, includes `om` version [3.1.0](https://github.com/pivotal-cf/om/releases/tag/3.1.0)

### Bug Fixes
- CVE update to container image. Resolves [USN-4127-1](https://usn.ubuntu.com/4127-1/).
  This CVE is related to vulnerabilities with `python`.
  None of our code calls `python` directly, but the IaaS CLIs rely on this package.
- CVE update to container image. Resolves [USN-4129-1](https://usn.ubuntu.com/4129-1/).
  (related to vulnerabilities with `curl` and `libcurl`. While none of our code directly used these,
  they are present on the image.)
- CVE update to container image. Resolves [USN-4132-1](https://usn.ubuntu.com/4132-1/).
  (related to vulnerabilities with `expat`. While none of our code directly used these,
  they are present on the image.)
- Bumped the following low-severity CVE packages: `libsystemd0`, `libudev1`, `linux-libc-dev`

## v4.0.1

Released September 4, 2019, includes `om` version [3.1.0](https://github.com/pivotal-cf/om/releases/tag/3.1.0)

### Bug Fixes
- CVE update to container image. Resolves [USN-4108-1](https://usn.ubuntu.com/4108-1/).
  (related to vulnerabilities with `libzstd`. While none of our code directly used these,
  they are present on the image.)
- Bumped the following low-severity CVE packages: `linux-libc-dev`

## v4.0.0

Released August 28, 2019, includes `om` version [3.1.0](https://github.com/pivotal-cf/om/releases/tag/3.1.0)

### Breaking Changes

- The tasks have been updated to extract their `bash` scripting into a separate script.
  The tasks' script can be used with different CI/CD systems like Jenkins.

  This will be a breaking change if your tasks resource is not named `platform-automation-tasks`.

  For example,

  ```yaml
  - get: tasks
  - task: configure-authentication
    file: tasks/tasks/configure-authentication.yml
  ```

  will be changed to

  ```yaml
  - get: platform-automation-tasks
  - task: configure-authentication
    file: platform-automation-tasks/tasks/configure-authentication.yml
  ```

  Notice that the resource name changed as did the relative path to the task YAML file in `file`.

### What's New
- [`configure-ldap-authentication`][configure-ldap-authentication], [`configure-saml-authentication`][configure-saml-authentication], and [`configure-authentication`][configure-authentication]
  can create a UAA client on the Ops Manager VM.
  The client_secret will be the value provided to this option `precreated-client-secret`.
  This is supported in OpsManager 2.5+.
- For Ops Manager 2.6+, new task [`pre-deploy-check`][pre-deploy-check]
  will validate that Ops Manager and it's staged products
  are configured correctly.
  This may be run at any time
  and may be used as a pre-check for `apply-changes`.
- For GCP, [`create-vm`][create-vm] will now allow you
  to specify a `gcp_service_account_name`
  for the new Ops Manager VM.
  This enables you to designate a service account name
  as opposed to providing a service account json object.
  This may be specified in the [Ops Manager config for GCP][inputs-outputs-gcp].
  For more information on GCP service accounts, refer to the [GCP service accounts][gcp-service-accounts] docs.
- For GCP, [`create-vm`][create-vm] supports setting `scopes` for the new Ops Manager VM.
  This may be specified in the [Ops Manager config for GCP][inputs-outputs-gcp].
  For more information on setting GCP scopes, refer to the [GCP scope][gcp-scope] docs.
- [`configure-director`][configure-director] now support [VM Extensions][vm-extensions].
  *Please note this is an advanced feature, and should be used at your own discretion.*  
- [`configure-director`][configure-director] now support [VM Types][vm-types].
  *Please note this is an advanced feature, and should be used at your own discretion.*
- Add support for new NSX and NSXT format in Ops Manager 2.7+
  when calling [`staged-config`][staged-config] and [`staged-director-config`][staged-director-config]
- [state][state] can now be defined in a `state-$timestamp.yml` format (like [`export-installation`][export-installation]).
  This is an _opt-in_ feature, and is only recommended
  if you are storing state in a non-versioned s3-compatible blobstore.
  To opt-in to this feature,
  a param must be added to your pipeline
  and given the value of `STATE_FILE: state-$timestamp.yml`
  for each invocation of the following commands:
      - [`create-vm`][create-vm]
      - [`delete-vm`][delete-vm]
      - [`upgrade-opsman`][upgrade-opsman]
- [gcp opsman.yml][inputs-outputs-gcp] now supports `ssh_public_key`.
  This is used to ssh into the Ops Manager VM to manage non-tile bosh add-ons.
- **EXPERIMENTAL** `config-template` now will provide required-vars in addition to default-vars.
- **EXPERIMENTAL** `config-template` will define vars with an `_` instead of a `/`.
  This is an aesthetically motivated change.
  Ops files are denoted with `/`,
  so changing the vars separators to `_` makes this easier to differentiate.
- **EXPERIMENTAL** `config-template` output `product-default-vars.yml` has been changed to `default-vars.yml`

### Bug Fixes
- [`download-product`][download-product] will now return a `download-product.json`
  if `stemcell-iaas` is defined, but there is no stemcell to download for that product.
- [vsphere opsman.yml][inputs-outputs-vsphere] now requires `ssh_public_key` for Ops Manager 2.6+
  This was added to mitigate an error during upgrade
  that would cause the VM to enter a reboot loop.
- When using AWS to create the Ops Manager VM with encrypted disks,
  the task [`create-vm`][create-vm] and [`upgrade-opsman`][upgrade-opsman] will wait for disk encryption to be completed.
  An exponential backoff will be and timeout after an hour if disk is not ready.

## v3.0.18
Released February 20, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.0.0](https://github.com/pivotal-cf/om/releases/tag/3.0.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-3.0.18" target="_blank">Download</a>

### Bug Fixes
- GCP [`create-vm`][create-vm] now correctly handles an empty tags list
- CVE update to container image. Resolves [USN-4274-1](https://usn.ubuntu.com/4274-1/).
  The CVEs are related to vulnerabilities with `libxml2`.
- Bumped the following low-severity CVE packages: libsystemd0 libudev1

## v3.0.17
Released February 3, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.0.0](https://github.com/pivotal-cf/om/releases/tag/3.0.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

    The full Docker image-receipt: <a href="https://platform-automation-release-candidate.s3-us-west-2.amazonaws.com/image-receipt-3.0.17" target="_blank">Download</a>

### Bug Fixes
- CVE update to container image. Resolves [USN-4243-1](https://usn.ubuntu.com/4243-1/).
  The CVEs are related to vulnerabilities with `libbsd`.
- CVE update to container image. Resolves [USN-4249-1](https://usn.ubuntu.com/4249-1/).
  The CVEs are related to vulnerabilities with `e2fsprogs`.
- CVE update to container image. Resolves [USN-4233-2](https://usn.ubuntu.com/4233-2/).
  The CVEs are related to vulnerabilities with `libgnutls30`.
- CVE update to container image. Resolves [USN-4256-1](https://usn.ubuntu.com/4256-1/).
  The CVEs are related to vulnerabilities with `libsasl2-2`.
- Bumped the following low-severity CVE packages: `libcom-err2`, `libext2fs2`, `libss2`, `linux-libc-dev`

## v3.0.16
Released January 28, 2020

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.0.0](https://github.com/pivotal-cf/om/releases/tag/3.0.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4236-1](https://usn.ubuntu.com/4236-1/).
  The CVEs are related to vulnerabilities with `Libgcrypt`.
- CVE update to container image. Resolves [USN-4233-1](https://usn.ubuntu.com/4233-1/).
  The CVEs are related to vulnerabilities with `GnuTLS`.
- Bumped the following low-severity CVE package: `linux-libc-dev`

## v3.0.15
Released December 12, 2019

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.0.0](https://github.com/pivotal-cf/om/releases/tag/3.0.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4220-1](https://usn.ubuntu.com/4220-1/).
  The CVEs are related to vulnerabilities with `git`.
- Bumped the following low-severity CVE package: `linux-libc-dev`

## v3.0.14
Released December 3, 2019

??? info "CLI Versions"

    | Name | version |
    |---|---|
    | om | [3.0.0](https://github.com/pivotal-cf/om/releases/tag/3.0.0) |
    | bosh-cli | [6.1.1](https://github.com/cloudfoundry/bosh-cli/releases/tag/v6.1.1) |
    | credhub | [2.6.1](https://github.com/cloudfoundry-incubator/credhub-cli/releases/tag/2.6.1) |
    | winfs-injector | [0.13.0](https://github.com/pivotal-cf/winfs-injector/releases/tag/0.13.0) |

### Bug Fixes
- CVE update to container image. Resolves [USN-4205-1](https://usn.ubuntu.com/4205-1/).
  This CVE is related to vulnerabilities with `libsqlite3`.
  None of our code calls `libsqlite3` directly, but the IaaS CLIs rely on this package.

## v3.0.13
Released November 14, 2019, includes `om` version [3.0.0](https://github.com/pivotal-cf/om/releases/tag/3.0.0)

### Bug Fixes
- CVE update to container image. Resolves [USN-4172-1](https://usn.ubuntu.com/4172-1/).
  This CVE is related to vulnerabilities with `file` and `libmagic`.
- CVE update to container image. Resolves [USN-4168-1](https://usn.ubuntu.com/4168-1/).
  This CVE is related to vulnerabilities with `libidn2`.
- Bump `bosh` CLI to v6.1.1
- Bump `credhub` CLI to v2.6.1

## v3.0.12
Released October 25, 2019, includes `om` version [3.0.0](https://github.com/pivotal-cf/om/releases/tag/3.0.0)

### Bug Fixes
- CVE update to container image. Resolves [USN-4151-1](https://usn.ubuntu.com/4151-1/).
  This CVE is related to vulnerabilities with `python`.
  None of our code calls `python` directly, but the IaaS CLIs rely on this package.

## v3.0.11

Released October 15, 2019, includes `om` version [3.0.0](https://github.com/pivotal-cf/om/releases/tag/3.0.0)

### Bug Fixes
- CVE update to container image. Resolves [USN-4142-1](https://usn.ubuntu.com/4142-1/).
  (related to vulnerabilities with `e2fsprogs`. While none of our code directly used these,
  they are present on the image.)
- Bumped the following low-severity CVE packages: `libcom-err2`, `libext2fs2`, `libss2`, `linux-libc-dev`

## v3.0.10
Released September 26, 2019, includes `om` version [3.0.0](https://github.com/pivotal-cf/om/releases/tag/3.0.0)

### Bug Fixes
- CVE update to container image. Resolves [USN-4127-1](https://usn.ubuntu.com/4127-1/).
  This CVE is related to vulnerabilities with `python`.
  None of our code calls `python` directly, but the IaaS CLIs rely on this package.
- CVE update to container image. Resolves [USN-4129-1](https://usn.ubuntu.com/4129-1/).
  (related to vulnerabilities with `curl` and `libcurl`. While none of our code directly used these,
  they are present on the image.)
- CVE update to container image. Resolves [USN-4132-1](https://usn.ubuntu.com/4132-1/).
  (related to vulnerabilities with `expat`. While none of our code directly used these,
  they are present on the image.)
- Bumped the following low-severity CVE packages: `libsystemd0`, `libudev1`, `linux-libc-dev`

## v3.0.8
Released September 4, 2019, includes `om` version [3.0.0](https://github.com/pivotal-cf/om/releases/tag/3.0.0)

### Bug Fixes
- CVE update to container image. Resolves [USN-4108-1](https://usn.ubuntu.com/4108-1/).
  (related to vulnerabilities with `libzstd`. While none of our code directly used these,
  they are present on the image.)
- Bumped the following low-severity CVE packages:
  `libpython2.7`, `libpython2.7-dev`, `libpython2.7-minimal`, `libpython2.7-stdlib`, `libssl1.1`
  `openssl`, `python-cryptography`, `python2.7`, `python2.7-dev`, `python2.7-minimal`

## v3.0.7
Released August 28, 2019, includes `om` version [3.0.0](https://github.com/pivotal-cf/om/releases/tag/3.0.0)

### Bug Fixes
- When using AWS to create the Ops Manager VM with encrypted disks,
  the task [`create-vm`][create-vm] and [`upgrade-opsman`][upgrade-opsman] will wait for disk encryption to be completed.
  An exponential backoff will be and timeout after an hour if disk is not ready.
- CVE update to container image. Resolves [USN-4071-1](https://usn.ubuntu.com/4071-1/).
  (related to vulnerabilities with `patch`. While none of our code directly used these,
  they are present on the image.)
- Bumped the following low-severity CVE packages:
  `linux-libc-dev`, `libldap-2.4-2`, `libldap-common`, `linux-libc-dev`

## v3.0.5
Released July 22, 2019, includes `om` version [3.0.0](https://github.com/pivotal-cf/om/releases/tag/3.0.0)

### Bug Fixes
- in [`credhub-interpolate`][credhub-interpolate], [`upload-product`][upload-product], and [`upload-stemcell`][upload-stemcell]
  setting `SKIP_MISSING: false` the command would fail.
  This has been fixed.  
- [`upgrade-opsman`][upgrade-opsman] would fail on the [`import-installation`][import-installation] step
  if the env file did not contain a target or decryption passphrase.
  This will now fail before the upgrade process begins
  to ensure faster feedback.
- [`upgrade-opsman`][upgrade-opsman] now respects environment variables
  when it makes calls internally to `om`
  (env file still required).
- `download-product-s3` does not require `pivnet-api-token` anymore.
- `om` CLI has been bumped to v3.0.0.
  This includes the following bug fixes:
    * `apply-changes --product <product>` will error with _product not found_ if that product has not been staged.
    * `upload-stemcell` now accepts `--floating false` in addition to `floating=false`.
      This was done to offer consistency between all of the flags on the command.
    * `skip-unchanged-products` was removed from `apply-changes`.
      This option has had issues with consistent successful behaviour.
      For example, if the apply changes fails for any reason, the subsequent apply changes cannot pick where it left off.
      This usually happens in the case of errands that are used for services.

        We are working on scoping a selective deploy feature that makes sense for users.
        We would love to have feedback from users about this.

    * remove `revert-staged-changes`
      `unstage-product` functionally does the same thing,
      but uses the API.
- Bumped the following low-severity CVE packages: `unzip`

## v3.0.4
Released July 11, 2019, includes `om` version [2.0.0](https://github.com/pivotal-cf/om/releases/tag/2.0.0)

### Bug Fixes
- Both [`configure-ldap-authentication`][configure-ldap-authentication]
  and [`configure-saml-authentication`][configure-saml-authentication]
  will now automatically
  create a BOSH UAA admin client as documented [here](https://docs.pivotal.io/pivotalcf/2-5/customizing/opsmanager-create-bosh-client.html#saml).
  This is only supported in OpsManager 2.4 and greater.
  You may specify the option `skip-create-bosh-admin-client` in your config YAML
  to skip creating this client.
  After the client has been created,
  you can find the client ID and secret
  by following [steps three and four found here](https://docs.pivotal.io/pivotalcf/2-5/customizing/opsmanager-create-bosh-client.html#-provision-admin-client).

    _This feature needs to be enabled
    to properly automate authentication for the bosh director when using LDAP and SAML._
    If `skip-create-bosh-admin-client: true` is specified, manual steps are required,
    and this task is no longer "automation".

- [`create-vm`][create-vm] and [`upgrade-opsman`][upgrade-opsman] now function with `gcp_service_account_name` on GCP.
  Previously, only providing a full `gcp_service_account` as a JSON blob worked.
- Environment variables passed to [`create-vm`][create-vm], [`delete-vm`][delete-vm], and [`upgrade-opsman`][upgrade-opsman]
  will be passed to the underlying IAAS CLI invocation.
  This allows our tasks to work with the `https_proxy` and `no_proxy` variables
  that can be [set in Concourse](https://github.com/concourse/concourse-bosh-release/blob/9764b66a6d85785735f6ea8ddcabf77785b5eddd/jobs/worker/spec#L50-L65).
- [`download-product`][download-product] task output of `assign-stemcell.yml` will have the correct `product-name`
- When using the `env.yml` for a task,
  extra values passed in the env file will now fail if they are not recognized properties.
  Invalid properties might now produce the following:
    ```bash
      $ om --env env.yml upload-product --product product.pivotal
      could not parse env file: yaml: unmarshal errors:
      line 5: field invalid-field not found in type main.options
    ```

- `credhub` CLI has been bumped to v2.5.1.
  This includes a fix of not raising an error when processing an empty YAML file.
- `om` CLI has been bumped to v2.0.0.
  This includes the following bug fixes:
    * `download-product` will now return a `download-file.json`
      if `stemcell-iaas` is defined but the product has no stemcell.
      Previously, this would exit gracefully, but not return a file.
    * Non-string environment variables can now be read and passed as strings to Ops Manager.
      For example, if your environment variable (`OM_NAME`) is set to `"123"` (with quotes escaped),
      it will be evaluated in your config file with the quotes.

        Given `config.yml`
        ```yaml
        value: ((NAME))
        ```

        `om interpolate -c config.yml --vars-env OM`

        Will evaluate to:
        ```yaml
          value: "123"
        ```

    * `bosh-env` will now set `BOSH_ALL_PROXY` without a trailing slash if one is provided
    * When using `bosh-env`, a check is done to ensure the SSH private key exists.
      If does not the command will exit 1.
    * `config-template` will enforce the default value for a property to always be `configurable: false`.
      This is inline with the OpsManager behaviour.

- CVE update to container image. Resolves [USN-4040-1](https://usn.ubuntu.com/4040-1/).
  (related to vulnerabilities with `Expat`. While none of our code directly used these,
  they are present on the image.)
- CVE update to container image. Resolves [USN-4038-1](https://usn.ubuntu.com/4038-1/) and [USN-4038-3](https://usn.ubuntu.com/4038-3/).
  (related to vulnerabilities with `bzip`. While none of our code directly used these,
  they are present on the image.)
- CVE update to container image. Resolves [USN-4019-1](https://usn.ubuntu.com/4019-1/).
  (related to vulnerabilities with `SQLite`. While none of our code directly used these,
  they are present on the image.)
- CVE update to container image. Resolves [CVE-2019-11477](https://people.canonical.com/~ubuntu-security/cve/2019/CVE-2019-11477.html).
  (related to vulnerabilities with `linux-libc-dev`. While none of our code directly used these,
  they are present on the image.)
- CVE update to container image. Resolves [USN-4049-1](https://usn.ubuntu.com/4049-1/).
  (related to vulnerabilities with `libglib`. While none of our code directly used these,
  they are present on the image.)

## v3.0.2
Released July 8, 2019, includes `om` version [1.0.0](https://github.com/pivotal-cf/om/releases/tag/1.0.0)

### Bug Fixes
- CVE update to container image. Resolves [USN-4014-1](https://usn.ubuntu.com/4014-1/).
  (related to vulnerabilities with `GLib`. While none of our code directly used these,
  they are present on the image.)
- CVE update to container image. Resolves [USN-4015-1](https://usn.ubuntu.com/4015-1/).
  (related to vulnerabilities with `DBus`. While none of our code directly used these,
  they are present on the image.)
- CVE update to container image. Resolves [USN-3999-1](https://usn.ubuntu.com/3999-1/).
  (related to vulnerabilities with `GnuTLS`. While none of our code directly used these,
  they are present on the image.)
- CVE update to container image. Resolves [USN-4001-1](https://usn.ubuntu.com/4001-1/).
  (related to vulnerabilities with `libseccomp`. While none of our code directly used these,
  they are present on the image.)
- CVE update to container image. Resolves [USN-4004-1](https://usn.ubuntu.com/4004-1/).
  (related to vulnerabilities with `Berkeley DB`. While none of our code directly used these,
  they are present on the image.)
- CVE update to container image. Resolves [USN-3993-1](https://usn.ubuntu.com/3993-1/).
  (related to vulnerabilities with `curl`. While none of our code directly used these,
  they are present on the image.)

## v3.0.1
Released May 24, 2019, includes `om` version [1.0.0](https://github.com/pivotal-cf/om/releases/tag/1.0.0)

### Breaking Changes
- `om` will now follow conventional Semantic Versioning,
  with breaking changes in major bumps,
  non-breaking changes for minor bumps,
  and bug fixes for patches.
- The [`credhub-interpolate`][credhub-interpolate] task can have multiple
  interpolation paths. The `INTERPOLATION_PATH` param is now plural: `INTERPOLATION_PATHS`.
  IF you are using a custom `INTERPOLATION_PATH` for `credhub-interpolate`, you will need to update
  your `pipeline.yml` to this new param.
  As an example, if your credhub-interpolate job is defined as so:
```yaml
# OLD pipeline.yml PRIOR TO 3.0.0 RELEASE
- name: example-credhub-interpolate
  plan:
  - get: platform-automation-tasks
  - get: platform-automation-image
  - get: config
  - task: credhub-interpolate
    image: platform-automation-image
    file: platform-automation-tasks/tasks/credhub-interpolate.yml
    input_mapping:
      files: config
    params:
      # all required
      CREDHUB_CA_CERT: ((credhub_ca_cert))
      CREDHUB_CLIENT: ((credhub_client))
      CREDHUB_SECRET: ((credhub_secret))
      CREDHUB_SERVER: ((credhub_server))
      PREFIX: /private-foundation
      INTERPOLATION_PATH: foundation/config-path
      SKIP_MISSING: true
```
  it should now look like
```yaml hl_lines="19"
# NEW pipeline.yml FOR 3.0.0 RELEASE
- name: example-credhub-interpolate
  plan:
  - get: platform-automation-tasks
  - get: platform-automation-image
  - get: config
  - task: credhub-interpolate
    image: platform-automation-image
    file: platform-automation-tasks/tasks/credhub-interpolate.yml
    input_mapping:
      files: config
    params:
      # all required
      CREDHUB_CA_CERT: ((credhub_ca_cert))
      CREDHUB_CLIENT: ((credhub_client))
      CREDHUB_SECRET: ((credhub_secret))
      CREDHUB_SERVER: ((credhub_server))
      PREFIX: /private-foundation
      INTERPOLATION_PATHS: foundation/config-path
      SKIP_MISSING: true
```

- the [`upload-product`][upload-product] option `--sha256` has been changed to `--shasum`.
  IF you are using the `--config` flag in `upload-product`, your config file will need to update from:
```yaml
# OLD upload-product-config.yml PRIOR TO 3.0.0 RELEASE
product-version: 1.2.3-build.4
sha256: 6daededd8fb4c341d0cd437a
```
  to:
```yaml hl_lines="3"
# NEW upload-product-config.yml FOR 3.0.0 RELEASE
product-version: 1.2.3-build.4
shasum: 6daededd8fb4c341d0cd437a # NOTE the name of this value is changed
```
  This change was added to future-proof the param name for when sha256 is no longer the
  de facto way of defining shasums.

### What's New
- The new command [`assign-multi-stemcell`][assign-multi-stemcell] assigns multiple stemcells to a provided product.
  This feature is only available in OpsMan 2.6+.
- [`download-product`][download-product] ensures sha sum checking when downloading the file from Tanzu Network.
- [`download-product`][download-product] can now disable ssl validation when connecting to Tanzu Network.
  This helps with environments with SSL and proxying issues.
  Add `pivnet-disable-ssl: true` in your [download-product-config][download-product-config] to use this feature.
- On [GCP][inputs-outputs-gcp], if you did not assign a public IP, Google would assign
  one for you. This has been changed to only assign a public IP if defined in your `opsman.yml`.
- On [Azure][inputs-outputs-azure], if you did not assign a public IP, Azure would assign
  one for you. This has been changed to only assign a public IP if defined in your `opsman.yml`.
- `om interpolate` (example in the [test task][test-interpolate]) now supports
   the ability to accept partial vars files. This is added support for users who may also be using
   credhub-interpolate or who want to mix interpolation methods. To make use of this feature, include
   the `--skip-missing` flag.
- [`credhub-interpolate`][credhub-interpolate] now supports the `SKIP_MISSING`
   parameter. For more information on how to use this feature and if it fits for your foundation(s), see the
   [Secrets Handling][secrets-handling-multiple-sources] section.
- the [reference pipeline][reference-pipeline] has been updated to give an example of
  [`credhub-interpolate`][credhub-interpolate] in practice. For more information
  about credhub, see [Secrets Handling][secrets-handling-multiple-sources]
- `om` now has support for `config-template` (a Platform Automation Toolkit encouraged replacement of
   `tile-config-generator`). This is an experimental command that can only be run currently using `docker run`.
   For more information and instruction on how to use `config-template`, please see
   [Creating a Product Config File][config-template].
- [`upload-stemcell`][upload-stemcell] now supports the ability to include a config file.
  This allows you to define an expected `shasum` that will validate the calculated shasum of the provided
  `stemcell` uploaded in the task. This was added to give feature parity with [`upload-product`][upload-product]
- [Azure][inputs-outputs-azure] now allows NSG(network security group) to be optional.
  This change was made because NSGs can be assigned at the subnet level rather than just the VM level. This
  param is also not required by the [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/vm?view=azure-cli-latest).
  Platform Automation Toolkit now reflects this.
- [staged-director-config][staged-director-config] now supports returning multiple IaaS
  configurations. `iaas-configurations` is a top level key returned in Ops Manager 2.2+. If using an Ops
  Manager 2.1 or earlier, `iaas_configuration` will continue to be a key nested under `properties-configuration`.
- [configure-director][configure-director] now supports setting multiple IaaS configurations.
  If using this feature, be sure to use the top-level `iaas-configurations` key, rather than the nested
  `properties-configuration.iaas_configuration` key. If using a single IaaS, `properties-configuration.iaas_configuration`
  is still supported, but the new `iaas_configurations` top-level key is recommended.

    ```yaml hl_lines="2"
    # Configuration for 2.2+
    iaas-configurations:
    - additional_cloud_properties: {}
      name: ((iaas-configurations_0_name))
    - additional_cloud_properties: {}
      name: ((iaas-configurations_1_name))
      ...
    networks-configuration: ...
    properties-configuration: ...
    ```

    ```yaml hl_lines="5"
    # Configuration 2.1 and earlier
    networks-configuration: ...
    properties-configuration:
        director_configuration: ...
        iaas_configuration:
          additional_cloud_properties: {}
          name: ((iaas-configurations_0_name))
          ...
        security_configuration: ...
    ```

### Bug Fixes
- OpenStack would sometimes be unable to associate the public IP when creating the VM, because it was
  waiting for the VM to come up. The `--wait` flag has been added to validate that the VM creation is
  complete before more work is done to the VM.
- [`credhub-interpolate`][credhub-interpolate] now accepts multiple files for the `INTERPOLATION_PATHS`.
- CVE update to container image. Resolves [USN-3911-1](https://usn.ubuntu.com/3911-1/).
  (related to vulnerabilities with `libmagic1`. While none of our code directly used these,
  they are present on the image.)
- Improved error messaging for [vSphere][inputs-outputs-vsphere] VM creation if neither `ssh-password` or `ssh-public-key` are set.
  One or the other is required to create a VM.

{% include ".internal_link_url.md" %}
{% include ".external_link_url.md" %}
