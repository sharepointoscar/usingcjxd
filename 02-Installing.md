# Installing CJXD Binary

As of the writing of this guide, the CJXD is installed only using the following command.

> **NOTE:** If you are on OS X, you cannot install it via Homebrew, as that is a different version.

```bash
curl -L https://storage.googleapis.com/artifacts.jenkinsxio.appspot.com/binaries/cjxd/latest/jx-darwin-amd64.tar.gz | tar xzv

# move the executable to proper location
sudo mv jx /usr/local/bin

# validate binary is in proper location
which jx

# lastly check the version
jx --version
```

# Create a Kubernetes Cluster
Now that we have the correct `jx` binary, it is time to create the Kubernetes cluster.  To do that we will execute the following command:

```bash
# create a cluster with the name jxboot-omedina, skip jx installation
jx create cluster gke --skip-installation -n jxboot-omedina
```
We go through several prompts and answer questions.  The next step is to **activate** the CloudBees Jenkins X Distribution using the following command:

> **WARNING:** If you fail to do this, nothing else will work as expected.

```bash
# activate CloudBees Jenkins X Distribution
jx create cluster gke --skip-installation -n jxboot-omedina
```

Finally we are ready to install Jenkins X on our newly created cluster using the following command:

```bash
# use jx boot to install jenkins x on the kubernetes cluster
jx boot
```
Amongst the question you will answer are:

- Git Owner name: This is the Github Org NOT your personal account
- Storage Buckets for: *Logs*, *Reports* and *Chartmuseum repository*
- Pipeline Bot Git: This usually is a Github actual account which has proper permissions in the Org to create, delete and do other things against repos.

> **TIP:** If you are prompted to upgrade your jx binary, please select **N** as this will install an incorrect `jx` binary and you already have it.

Next you will be asked if you'd like to configure **Docker Registry**

If you are using a cloud provider that does not have a registry service, you can create one at **Docker Hub**, then answer this question with the URL for that registry.  You can use any registry you already have.

If you are using **Google Cloud** a registry will automatically be created for you by hitting **Enter**.

# What's Next?
At this point we have a working Jenkins X Distribution cluster working.  It is time to explore how to further configure it.

On our next chapter, we will focus on adding a custom domain.