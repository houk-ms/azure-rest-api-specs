## AZ

These settings apply only when `--az` is specified on the command line.

``` yaml $(az) && $(package-migrate)
az:
  extensions: migrate
  namespace: azure.mgmt.migrate
  package-name: azure-mgmt-migrate
az-output-folder: $(azure-cli-extension-folder)/src/migrate
python-sdk-output-folder: "$(az-output-folder)/azext_migrate/vendored_sdks/migrate"
```

``` yaml $(az) && $(package-offazure)
az:
  extensions: offazure
  namespace: azure.mgmt.offazure
  package-name: azure-mgmt-offazure
  client-subscription-bound: false
sdk-no-flatten: true
az-output-folder: $(azure-cli-extension-folder)/src/offazure
python-sdk-output-folder: "$(az-output-folder)/azext_offazure/vendored_sdks/offazure"
directive:
  - where:
        group: offazure hyper-v-cluster
    set:
        group: offazure hyperv cluster
  - where:
        group: offazure hyper-v-host
    set:
        group: offazure hyperv host
  - where:
        group: offazure hyper-v-job
    set:
        group: offazure hyperv job
  - where:
        group: offazure hyper-v-machine
    set:
        group: offazure hyperv machine
  - where:
        group: offazure hyper-v-operation-status
    set:
        group: offazure hyperv operation-status
  - where:
        group: offazure hyper-v-run-as-account
    set:
        group: offazure hyperv run-as-account
  - where:
        group: offazure hyper-v-site
    set:
        group: offazure hyperv site
  - where:
        group: offazure job
    set:
        group: offazure vmware job
  - where:
        group: offazure machine
    set:
        group: offazure vmware machine
  - where:
        group: offazure run-as-account
    set:
        group: offazure vmware run-as-account
  - where:
        group: offazure site 
    set:
        group: offazure vmware site
  - where:
        group: offazure v-center
    set:
        group: offazure vmware vcenter
  - where:
        group: offazure v-mware-operation-status
    set:
        group: offazure vmware operation-status
  - where:
        command: offazure hyper-v-cluster show-all-cluster-in-site
    set:
        command: offazure hyperv cluster list
  - where:
        command: offazure hyper-v-cluster show-cluster
    set:
        command: offazure hyperv cluster show
cli:
  cli-directive:
    - where:
        group: 'Jobs'
      hidden: true
    - where:
        group: 'VMwareOperationsStatus'
      hidden: true
    - where:
        group: 'HyperVJobs'
      hidden: true
    - where:
        group: 'HyperVOperationsStatus'
      hidden: true
    - where:
        group: 'HyperVCluster'
        op: 'PutCluster'
      hidden: true
```