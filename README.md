```loryleticee.alwaysdata_records```
=========

Sets dns records in alwaysdata via API calls

Requirements
------------

Each item in playload must contains alwaysdata_domain_id, name and dns keys
```playload``` and ```alwaysdata_token``` variables **must be set**

Role Variables
--------------
```
alwaysdata_token: xxxxxxxxx (required)
record_type:  (A,TXT,AAA, ...)
annotation: A text for identify records made by ansible in alwaysdata record metadatas
delete: if set to true , only delete records. Value is false by default

playload: dict of records (required)

  playload:
   - key: "example_1" (required)
     name: "example_1"  (required)
     alwaysdata_domain_id: "107938" (required)
     dns: web # dns must be declare with record value as line 5-6 (required)
```
Dependencies
------------

There is no dependencies 

Example Playbook
----------------
Create
```
- name: Create DNS records
  hosts: local
  roles:
    - role: loryleticee.alwaysdata_records
      vars:
        alwaysdata_token: xxxxxxxxxxxxxxxx
        #record_type:  A
        # annotation: ANSIBLE_MANAGED_ITEM
        # delete: false

        web: "10.0.0.253"
        api: "192.168.0.4"

        playload:
          - key: "example_1"
            name: "example_1" 
            alwaysdata_domain_id: "107938"
            dns: web # dns must be declare with record value as line 5-6

          - key: "example_2"
            name: "example_2"
            alwaysdata_domain_id: "102931"
            dns: api # dns must be declare with record value as line 5-6
```
Delete
```
- name: Delete DNS records
  hosts: local
  roles:
    - role: loryleticee.alwaysdata_records
      vars:
        alwaysdata_token: xxxxxxxxxxxxxxxx
        delete: true

        web: "10.0.0.253"
        api: "192.168.0.4"

        playload:
          - key: "example_1"
            name: "example_1" 
            alwaysdata_domain_id: "107938"
            dns: web # dns must be declare with record value as line 5-6

          - key: "example_2"
            name: "example_2"
            alwaysdata_domain_id: "102931"
            dns: api # dns must be declare with record value as line 5-6
```
License
-------

BSD

Author Information
------------------
Github: https://github.com/loryleticee

Mail: baleiniers_rouleau.6l@icloud.com

