# CFCR federation BOSH release

This BOSH release is used for joining multiple
CFCR-managed Kubernetes clusters into a federation.

## Usage example

TODO

## Contribution and maintenance

### Repackaging dependencies
According to the documentation, the v2 of the `kubefed` tool depends on
kubebuilder. However, at the time of writing, a few binaries had to be
overridden. When packaging the kubebuilder blob, download the release
archive, extract it to a temp folder removing the folder structure,
e.g.: `tar zvxf kubebuilder_1.0.0_linux_amd64.tar.gz -C blah --strip=2`.
then remove the following files:
- `kube-apiserver`
- `kubectl`
- `vendor.tar.gz`

and then re-package the archive: `tar zvcf ../kubebuilder-1.0.0-linux-amd64.tar.gz *`

All other blobs are downloaded from the sources indicated in the 
[federation README](https://github.com/kubernetes-sigs/federation-v2/blob/master/docs/userguide.md#kubebuilder)