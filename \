variable "hcloud_token" {}

provider "hcloud" {
    version = "1.16"
    token = var.hcloud_token

}

data "hcloud_ssh_key" "ssh_key" {
    fingerprint = "d7:39:df:90:cf:08:15:f1:42:ba:82:f6:89:eb:8f:c6"
}

resource "hcloud_server" "vpn" {
  name = "vpn"
  image = "ubuntu-16.04"
  server_type = "cx11"
  location = "fsn1"
  ssh_keys = ["${data.hcloud_ssh_key.ssh_key.id}"]
}

data "hcloud_server" "vpn" {
    name = "vpn"
}

output "server_ip" {
    value = data.hcloud_server.vpn.ipv4_address
}
