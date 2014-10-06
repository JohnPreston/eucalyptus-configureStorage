Role Name
=========

A brief description of the role goes here.

Requirements
------------

hosts:

- clc | Cloud Controller

- sc | Storage Controllers

Role Variables
--------------

| Parameter | Required | Default | Description
|--- |--- |--- |---
| sc_clusters | Yes | [] | List of sets to configure the backend for EBS services | See examples for SAN


Cluster variables
-----------------

| Parameter | Required | Default | Description
|--- |--- |--- |---
| partition | Yes | None | Storage of the Availability zone
| mode | Yes | None | Storage mode used in the availability Zone
| properties | Yes | [] | List which contains all the key/value items for the given mode

For the properties, see Eucalyptus documentation [here](https://www.eucalyptus.com/docs/eucalyptus/4.0/#install-guide/configure_storage_controller.html)


Dependencies
------------

- JohnPreston.eucalyptus-credentials

Example Playbook
----------------

```

- hosts: clc
  roles:
  - JohnPreston.eucalyptus-configureStorage
  vars:
  - sc_clusters:
    - {'partition': 'az-01', 'mode': 'das', 'properties': [ {'name': 'dasdevice', 'value': 'vg01'}]}
    - {'partition': 'az-02', 'mode': 'netapp', 'properties': [{'name':'sanhost', 'value': '10.105.2.103'},
      {'name': sanuser', 'value': 'root'}, {'name': 'sanpassword', 'value': 'N3t4pp'}]}

```


License
-------

BSD

Author Information
------------------

John Preston [John Mille]

