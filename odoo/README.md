# Ansible Role for Odoo

## Description and basic usage

This role allows to install, configure and deploy Odoo on any infrastructure.

This role is used by appending it to your ansible playbook:

```yml
- hosts: odoo_servers
  roles:
    - odoo
```

## Target OS

* Debian 10

## Available variables

Variable | Default value
---------|--------------
odoo_version | 14.0
odoo_service | odoo
odoo_user | odoo
odoo_user_passwd |  
odoo_user_system | True
odoo_init | True
odoo_init_env | {}
odoo_restart | True
odoo_rootdir | "/home/{{ odoo_user }}/{{ odoo_service }}"
odoo_workdir | "{{ odoo_rootdir }}"
odoo_bin | "odoo-bin"
odoo_sources_owner | "{{ ansible_env.USER }}"
odoo_stop_timeout | 5
odoo_repo_type | git
odoo_repo_url | "https://github.com/odoo/odoo.git"
odoo_repo_dest | "{{ odoo_rootdir }}"
odoo_repo_rev | "{{ odoo_version }}"
odoo_repo_update | yes
odoo_repo_depth | 1
odoo_repo_single_branch | yes
odoo_config_file | "/etc/{{ odoo_service }}/server.conf"
odoo_config_force | True
odoo_config_addons_path | "{ odoo_workdir }}/addons"
odoo_config_admin_passwd | admin
odoo_config_csv_internal_sep | ","
odoo_config_data_dir | "/home/{{ odoo_user }}/.local/share/Odoo"
odoo_config_db_host | localhost
odoo_config_db_maxconn | 64
odoo_config_db_name | False
odoo_config_db_password | "{{ odoo_user_passwd }}"
odoo_config_db_port | 5432
odoo_config_db_sslmode | prefer
odoo_config_db_template | template1
odoo_config_db_user | "{{ odoo_user }}"
odoo_config_dbfilter | "{{ odoo_config_db_name and '^' + odoo_config_db_name + '$' or '' }}"
odoo_config_demo | {}
odoo_config_email_from | False
odoo_config_geoip_database | /usr/share/GeoIP/GeoLite2-City.mmdb
odoo_config_http_enable | True
odoo_config_http_interface |  
odoo_config_http_port | 8069
odoo_config_import_partial |  
odoo_config_limit_memory_hard | 2684354560
odoo_config_limit_memory_soft | 2147483648
odoo_config_limit_request | 8192
odoo_config_limit_time_cpu | 60
odoo_config_limit_time_real | 120
odoo_config_limit_time_real_cron | -1
odoo_config_list_db | True
odoo_config_log_db | False
odoo_config_log_db_level | warning
odoo_config_log_handler | :INFO
odoo_config_log_level | info
odoo_config_logfile | "{{ odoo_logfile }}"
odoo_config_longpolling_port | 8072
odoo_config_max_cron_threads | 2
odoo_config_osv_memory_age_limit | False
odoo_config_osv_memory_count_limit | False
odoo_config_pg_path |  
odoo_config_pidfile |  
odoo_config_proxy_mode | False
odoo_config_reportgz | False
odoo_config_screencasts |  
odoo_config_screenshots | /tmp/odoo_tests
odoo_config_server_wide_modules | base,web
odoo_config_smtp_password | False
odoo_config_smtp_port | 25
odoo_config_smtp_server | localhost
odoo_config_smtp_ssl | False
odoo_config_smtp_user | False
odoo_config_syslog | False
odoo_config_test_enable | False
odoo_config_test_file |  
odoo_config_test_tags | None
odoo_config_transient_age_limit | 1.0
odoo_config_translate_modules | ['all']
odoo_config_unaccent | False
odoo_config_upgrade_path |  
odoo_config_without_demo | False
odoo_config_workers | 0
odoo_config_custom | {}
odoo_config_groups_custom | {}
odoo_extra_system_packages | []
odoo_extra_pip_packages | []
odoo_extra_pip_requirements | "{{ odoo_rootdir }}/requirements.txt"
odoo_extra_npm_packages | []
odoo_extra_tools | []
odoo_logrotate |  True
odoo_logdir | "/var/log/{{ odoo_service }}"
odoo_logfile | "{{ odoo_logdir }}/server.log"
odoo_maintenance_team | "Odoo IT team"
odoo_newrelic_account_id |  
odoo_newrelic_api_key |  
odoo_newrelic_app_name | Odoo
odoo_newrelic_config_file | "{{ odoo_config_file | dirname }}/newrelic.ini"
odoo_newrelic_environment | production
odoo_newrelic_license_key |  
odoo_newrelic_log_file | "/var/log/newrelic/python-agent.log"
odoo_newrelic_region | EU
odoo_nginx_cache_folder | "/var/cache/nginx"
odoo_nginx_client_max_body_size | 25M
odoo_nginx_document_root | "/var/www/html/"
odoo_nginx_server_name | "_"
odoo_nginx_timeout | 720s
odoo_nginx_trusted_ip |  
odoo_postgresql_version | 13
odoo_postgresql_set_user | True
odoo_postgresql_user_role_attr | CREATEDB,NOSUPERUSER
odoo_postgresql_active_unaccent | True
odoo_postgresql_login_user | "{{ odoo_config_db_user }}"
odoo_postgresql_login_password | "{{ odoo_config_db_password }}"
odoo_delete_database_backup | True
odoo_delete_datadir_backup | False
odoo_delete_old_lock | False
odoo_update_datadir_backup | "{{ odoo_config_data_dir }}/../backup"
odoo_update_database_backup | "/tmp/{{ odoo_config_db_name }}-{{ ansible_date_time.iso8601_basic_short }}.sql"
odoo_update_lockdir | "{{ odoo_config_data_dir }}/.lock"
odoo_update_logfile | "{{ odoo_logrotate and odoo_logfile or odoo_config_logfile }}"
odoo_update_modules | all
odoo_update_release_file |  
odoo_update_wait_delay | 0
odoo_update_wait_sleep | 5
odoo_update_wait_timeout | 900
odoo_clone_dest_db_script |  
odoo_clone_src_db_host |  
odoo_clone_src_db_port |  
odoo_clone_src_db_sslmode |  
odoo_clone_src_db_user |  
odoo_clone_src_db_password |  
odoo_clone_src_db_name |  
odoo_clone_src_db_backup | "/tmp/{{ odoo_clone_src_db_name }}-{{ ansible_date_time.iso8601_basic_short }}.dump"
odoo_clone_src_data_dir |  

Precisions
* odoo_config_custom: to add new options - _e.g.: upgrades_path = /home/odoo/odoo/upgrades_
* odoo_config_groups_custom: to add new option groups - _e.g.: [queue_job]
channel = root:2_

## Available tags

* **all**: Run everything.
* **application**: Update application source code.
* **backup**: Manage database backup when updating application.
* **clone**: Clone a source database before updating application.
* **configuration**: Update application configuration.
* **packages**: Update required packages list.

In addition to tags, here are some variables:

Variable | Default value
---------|--------------
odoo_install_packages | True
odoo_set_configuration | True
odoo_set_fail2ban | True
odoo_set_logrotate | True
odoo_set_newrelic | False
odoo_set_nginx | True
odoo_set_postgresql | True
odoo_set_service | True
odoo_set_user| True
odoo_update_application | True
odoo_update_database | True
odoo_update_sources | True
odoo_backup_database | True
odoo_backup_filestore | True (only if odoo_backup_database)
odoo_clone_database | False
odoo_clone_filestore | True (only if odoo_clone_database)

## Available handlers

This role provides an handler which restart Odoo. You can use it in your own task through:

```yml
- hosts: odoo_servers
  tasks:
    - name: "Useless task that will restart Odoo on changed"
      notify: "Restart Odoo"
  roles:
    - odoo
```

## Roadmap

* Support for Debian 11
