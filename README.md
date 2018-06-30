etcd
=========

Um distribuido e confiavel sistema de chave-valor para dados criticos de sistemas.

Requerimentos
------------

Se utilizar a configuração de autenticação via TLS, será necessario ter o `trusted_ca`, o `cert` e a `key` do servidor previamente instalados para a comunicacao entre o cluster.

Variaveis
--------------

Configura a versao do etcd a ser utilizada

    etcd_version: v3.3.8

Path de instalacao e de armazenamento de arquivos do etcd.

    etcd_install_path: /opt
    etcd_data_dir: /var/lib/etcd

Configuracao do cluster, assim como em qual interface o etcd irá rodar.

    etcd_cluster: False
    etcd_cluster_token: 82d47a30529dae4c9f8988fa36cba5d8
    etcd_cluster_iface: eth0

Configuraçao de autenticação via TLS.

    etcd_ssl: False
    etcd_ssl_cafile: /etc/etcd/ssl/cafile.crt
    etcd_ssl_crtfile: /etc/etcd/ssl/cert.crt
    etcd_ssl_keyfile: /etc/etcd/ssl/cert.key

Dependencias
------------

Nenhuma

Playbook exemplo
----------------

playbook.yml:

    - hosts: etcd
      vars:
        etcd_version: v3.3.8
        etcd_cluster_iface: eth1
        etcd_cluster: True
        etcd_ssl: False

      roles:
         - etcd

inventory:

    [etcd]
    etcd-server-01
    etcd-server-02
    etcd-server-03

Licença
-------

BSD/MIT

Informação sobre autor.
------------------

Desenvolvida por Thiago Freitas (deadcow@archlinux.com.br) em 06/2018.
