# IP Fix

## Open Network Setting File

- ### vi /etc/sysconfig/network-scripts/ifcfg-ens33

        TYPE="Ethernet"
        PROXY_METHOD="none"
        BROWSER_ONLY="no"
        BOOTPROTO="dhcp"
        DEFROUTE="yes"
        IPV4_FAILURE_FATAL="no"
        IPV6INIT="yes"
        IPV6_AUTOCONF="yes"
        IPV6_DEFROUTE="yes"
        IPV6_FAILURE_FATAL="no"
        IPV6_ADDR_GEN_MODE="stable-privacy"
        NAME="ens33"
        UUID="e6f18915-1f27-4f47-915b-ad89b50e4ec3"
        DEVICE="ens33"
        ONBOOT="yes"
        ZONE=
    - ens33부분은 네트워크 설정에 따라달라질수 있음

- ### IP Setting

        BOOTPROTO="static"
        IPADDR="192.168.192.130"
        GATEWAY="192.168.192.2"
        DNS1="168.126.63.1"
        DNS2="168.126.63.2"

- ### Network Restart
        systemctl restart network