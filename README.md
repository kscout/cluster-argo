# Cluster Argo
Argo installation.

# Table Of Contents
- [Overview](#overview)
- [Instructions](#instructions)

# Overview
Argo installation instructions for OpenShift 3.1.

# Instructions
1. Create a new project named `kscout-argo`:
   ```
   oc new-project kscout-argo
   ```
2. Install Argo controller and UI:
   ```
   curl -L oc apply -f https://raw.githubusercontent.com/argoproj/argo/v2.2.1/manifests/install.yaml \
       sed 's/namespace: argo/namespace: kscout-argo/g' | \
	   oc apply -f -
   ```
3. Give Argo workflows admin privileges:
   ```
   oc create rolebinding default-admin --clusterrole=admin --serviceaccount=default:default
   ```
   *Once the jobs we run become more defined this step will be replaced with a
   more locked down service account*
