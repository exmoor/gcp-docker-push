# Github Action for GCP docker registry push

A GitHub Action for building docker image and push to GCP container registry.

## Usage

In your actions workflow, insert this:

```bash
- name: Build, Push and Deploy service to Google Cloud Run
  uses: exmoor/gcp-docker-push@master
  with:
    image: [your-hostname]/[your-project]/[image]
    project: [your-project]
    region: [gcp-region]
    service key: ${{ secrets.GCLOUD_AUTH }}
    directory: [directory with Dockerfile]
```

Your `GCLOUD_AUTH` secret (or whatever you name it) must be a base64 encoded
gcloud service key.

The image must be "pushable" to one of Google's container registries, i.e. it
should be in the `gcr.io/[project]/[image]` or `eu.gcr.io/[project]/[image]`
format.
