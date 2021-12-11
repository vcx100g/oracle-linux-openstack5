# Local setup, remember set

kollacli property set openstack_release 5.0.1


## Port use 5432
sudo docker run -d -p 5432:5432 --name registry --restart=always \
    -v /var/lib/registry:/registry_data \
    -e REGISTRY_STORAGE_FILESYSTEM_ROOTDIRECTORY=/registry_data \
    -e REGISTRY_HTTP_TLS_KEY=/registry_data/conf.d/domain.key \
    -e REGISTRY_HTTP_TLS_CERTIFICATE=/registry_data/conf.d/domain.crt \
    registry:2
sudo ./import_to_registry.sh -c masternode.localdomain:5432

kollacli config reset
kollacli setdeploy local
kollacli host add masternode.localdomain
kollacli group addhost control masternode.localdomain
kollacli group addhost compute masternode.localdomain
kollacli group addhost database masternode.localdomain
kollacli group addhost network masternode.localdomain
kollacli group addhost storage masternode.localdomain
kollacli property set docker_registry masternode.localdomain:5432
kollacli password init
kollacli property set enable_haproxy no
kollacli property set network_interface lo
kollacli property set kolla_internal_address 127.0.0.1
kollacli property set neutron_external_interface ens33
kollacli deploy  
