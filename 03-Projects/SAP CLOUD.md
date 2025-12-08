---
id: "25"
aliases: []
tags:
  - project
  - Testing
Last edited time: 2025-09-29T15:13:00
Owner: Jeremie Cyrille
---

sphere et databricks
formation PL300

priorité: formation datashpère et databricks

formation:

- [datasphere](https://www.sap.com/france/products/data-cloud/datasphere/trial.html)
  Account:
- ON premeise sap 4/HANA
  GCP-ovh
  k2ETPoAmnmA6U7tDtD25
  gcp-gmail
  eM5gH0yB2OBihZDXzt2M
  marketing
  5ELIwyS9uw3psFDKMTa4
  POC:
- configurer l'instance SAP ABAP 1909
- FIchier de configuration en cour,
- configuere l'instance avec
- on le fait en on premise
  code 60 day trial
- CB8609EF0ABE599A
- aNe@MxqwnM@E7c2QCSEE
- tISFTXnaWA0NNtDWH5E8

```bash
sudo docker run -p 49013:49013 -p 49015:49015 -p 49041-49045:49041-49045 -p 1138-1139:1128-1129 -p 59023-59024:59013-59014 -p 49030-49033:49030-49033 -p 51000-51060:51000-51060 -p 53075:53075 -h hxehost -v /data/hxe:/hana/mounts --ulimit nofile=1048576:1048576 --sysctl kernel.shmmax=1073741824 --sysctl net.ipv4.ip_local_port_range='60000 65535' --sysctl kernel.shmmni=524288 --sysctl kernel.shmall=8388608 --name saptest --agree-to-sap-license --passwords-url /data/user.json --proxy-host proxy.wdf.sap.corp --proxy-port 8080 --no-proxy localhost,127.0.0.1,hxehost,hxehost.localdomain
```

`

```bash
sudo docker run -p 39013:39013 -p 39017:39017 -p 39041-39045:39041-39045 -p 1128-1129:1128-1129 -p 59013-59014:59013-59014 -v /data/<directory_name>:/hana/mounts \
--ulimit nofile=1048576:1048576 \
--sysctl kernel.shmmax=1073741824 \
--sysctl net.ipv4.ip_local_port_range='40000 60999' \
--sysctl kernel.shmmni=524288 \
--sysctl kernel.shmall=8388608 \
--name testsap \
store/saplabs/hanaexpress:<tag> \
--passwords-url file://data/user.json \
--agree-to-sap-license
```

`

```bash
# Ce code est compatible avec Terraform 4.25.0, ainsi qu'avec les versions rétrocompatibles avec 4.25.0.
# Pour en savoir plus sur la validation de ce code Terraform, consultez la page https://developer.hashicorp.com/terraform/tutorials/gcp-get-started/google-cloud-platform-build#format-and-validate-the-configuration

resource "google_compute_instance" "sles-15-sp5-sap-20251015-001159" {
  boot_disk {
    auto_delete = true
    device_name = "sles-15-sp5-sap-20251015-001159"

    initialize_params {
      image = "projects/suse-sap-cloud/global/images/sles-15-sp5-sap-v20250610-x86-64"
      size  = 10
      type  = "pd-balanced"
    }

    mode = "READ_WRITE"
  }

  can_ip_forward      = false
  deletion_protection = false
  enable_display      = false

  labels = {
    goog-ec-src           = "vm_add-tf"
    goog-gcp-marketplace  = ""
    goog-ops-agent-policy = "v2-x86-template-1-4-0"
  }

  machine_type = "e2-medium"

  metadata = {
    enable-osconfig = "TRUE"
    enable-oslogin  = "true"
  }

  name = "sles-15-sp5-sap-20251015-001159"

  network_interface {
    access_config {
      network_tier = "PREMIUM"
    }

    queue_count = 0
    stack_type  = "IPV4_ONLY"
    subnetwork  = "projects/sap-test-473708/regions/us-central1/subnetworks/default"
  }

  scheduling {
    automatic_restart   = true
    on_host_maintenance = "MIGRATE"
    preemptible         = false
    provisioning_model  = "STANDARD"
  }

  service_account {
    email  = "435075021851-compute@developer.gserviceaccount.com"
    scopes = ["https://www.googleapis.com/auth/devstorage.read_only", "https://www.googleapis.com/auth/logging.write", "https://www.googleapis.com/auth/monitoring.write", "https://www.googleapis.com/auth/service.management.readonly", "https://www.googleapis.com/auth/servicecontrol", "https://www.googleapis.com/auth/trace.append"]
  }

  shielded_instance_config {
    enable_integrity_monitoring = true
    enable_secure_boot          = false
    enable_vtpm                 = true
  }

  zone = "us-central1-a"
}

module "ops_agent_policy" {
  source          = "github.com/terraform-google-modules/terraform-google-cloud-operations/modules/ops-agent-policy"
  project         = "sap-test-473708"
  zone            = "us-central1-a"
  assignment_id   = "goog-ops-agent-v2-x86-template-1-4-0-us-central1-a"
  agents_rule = {
    package_state = "installed"
    version = "latest"
  }
  instance_filter = {
    all = false
    inclusion_labels = [{
      labels = {
        goog-ops-agent-policy = "v2-x86-template-1-4-0"
      }
    }]
  }
}
```

o4eWwwq2YAvtqILaI0wd

module "s4" {
source = "gcs::<https://www.googleapis.com/storage/v1/cloudsapdeploy/deployments/latest/terraform_s4.zip>"

primary_startup_url = var.module.s4.primary_startup_url
package_location = var.module.s4.package_location
deployment_name = var.module.s4.deployment_name
zone1_name = var.module.s4.zone1_name
existing_dns_zone_name = var.module.s4.existing_dns_zone_name
app_machine_type = var.module.s4.app_machine_type
sap_boot_disk_image_app = var.module.s4.sap_boot_disk_image_app
sap_boot_disk_image_ascs = var.module.s4.sap_boot_disk_image_ascs
sap_boot_disk_image_db = var.module.s4.sap_boot_disk_image_db
sap_version = var.module.s4.sap_version
vpc_name = var.module.s4.vpc_name
network_project = var.module.s4.network_project
db_machine_type = var.module.s4.db_machine_type
app_vms_multiplier = var.module.s4.app_vms_multiplier
app_sid = var.module.s4.app_sid
gcp_project_id = var.module.s4.gcp_project_id
vm_prefix = var.module.s4.vm_prefix
media_bucket_name = var.module.s4.media_bucket_name
ascs_machine_type = var.module.s4.ascs_machine_type
region_name = var.module.s4.region_name
db_sid = var.module.s4.db_sid
sap_instance_id_db = var.module.s4.sap_instance_id_db
sap_instance_id_ascs = var.module.s4.sap_instance_id_ascs
sap_instance_id_app = var.module.s4.sap_instance_id_app
app_disk_type = var.module.s4.app_disk_type
ascs_disk_type = var.module.s4.ascs_disk_type
db_data_disk_type = var.module.s4.db_data_disk_type
db_disk_type = var.module.s4.db_disk_type
db_log_disk_type = var.module.s4.db_log_disk_type
hana_secret_name = var.module.s4.hana_secret_name
application_secret_name = var.module.s4.application_secret_name
subnet_name = var.module.s4.subnet_name
filestore_location = var.module.s4.filestore_location
public_ip = var.module.s4.public_ip
public_ansible_runner_ip = var.module.s4.public_ansible_runner_ip
create_comms_firewall = var.module.s4.create_comms_firewall
deployment_has_dns = var.module.s4.deployment_has_dns
db_sa_email = var.module.s4.db_sa_email
ascs_sa_email = var.module.s4.ascs_sa_email
app_sa_email = var.module.s4.app_sa_email
custom_tags = var.module.s4.custom_tags
app_vm_names = var.module.s4.app_vm_names
fstore_mount_point = var.module.s4.fstore_mount_point
db_vm_names = var.module.s4.db_vm_names
ascs_vm_names = var.module.s4.ascs_vm_names
disk_size_map = var.module.s4.disk_size_map
}
echo "=== HANA Services ===" && \
hdbsql -i 90 -d SYSTEMDB -u SYSTEM -p YourStrongPassword123! "SELECT SERVICE_NAME, PORT FROM SYS.M_SERVICES WHERE ACTIVE_STATUS='YES'" && \
echo -e "\n=== XS Apps ===" && \
find /hana/shared/HXE -name "_.xsapp" 2>/dev/null && \
echo -e "\n=== HTTP Services ===" && \
hdbsql -i 90 -d SYSTEMDB -u SYSTEM -p YourStrongPassword123! "SELECT _FROM SYS.HTTP_SERVICES"
hdbsql -i 90 -d SYSTEMDB -u SYSTEM -p YourStrongPassword123! << EOF
SELECT _FROM M_SERVICES;
SELECT _FROM M_SERVICE_NETWORK_IO WHERE SERVICE_NAME='xsengine';
EOF
<http://35.205.82.167:8090/sap/hana/admin/cockpit>
