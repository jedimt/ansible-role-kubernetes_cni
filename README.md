Role Name
=========

Install either the Calico or Weave CNI plugin for Kubernetes.

Requirements
------------

None

Role Variables
--------------

    # CNI plugin to install (callico|weave)
    cni_plugin: "calico"

    # Calico version to install
    calico_version: "v3.25.0"
    calico_manifest_url: "https://raw.githubusercontent.com/projectcalico/calico/{{ calico_version }}/manifests/calico.yaml"

    # Weave
    weave_version: "v2.8.1"
    weave_manifest_url: "https://github.com/weaveworks/weave/releases/download/{{ weave_version }}/weave-daemonset-k8s.yaml"

Dependencies
------------

None.

Example Playbook
----------------

    # ===========================================================================
    # Install K8s CNI
    # ===========================================================================
    - name: Install K8s networking plugin
      hosts: k8s_master
      tags: play_k8s_network

      vars_files:
        # Ansible vault with all required passwords
        - "/home/apatt/github/demopod-ansible/credentials.yml"

      roles:
        - ansible-role-kubernetes-network-plugin

License
-------

MIT
