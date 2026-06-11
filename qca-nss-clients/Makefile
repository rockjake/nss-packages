include $(TOPDIR)/rules.mk

PKG_NAME:=qca-nss-clients
PKG_RELEASE:=8

PKG_SOURCE_URL:=https://git.codelinaro.org/clo/qsdk/oss/lklm/nss-clients.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2024-09-12
PKG_SOURCE_VERSION:=51be82d
PKG_MIRROR_HASH:=9777801a267b3cb54c8105bf3931181e9f5ee74df19c6d8c6f4aa4536b5515dd
QSDK_VERSION:=12.5
PKG_VERSION:=$(QSDK_VERSION).$(subst -,.,$(PKG_SOURCE_DATE))~$(PKG_SOURCE_VERSION)

PKG_BUILD_PARALLEL:=1

PKG_CONFIG_DEPENDS:=\
	CONFIG_NSS_DRV_BRIDGE_ENABLE \
	CONFIG_NSS_DRV_GRE_ENABLE \
	CONFIG_NSS_DRV_GRE_REDIR_ENABLE \
	CONFIG_NSS_DRV_IGS_ENABLE \
	CONFIG_NSS_DRV_IPV4_REASM_ENABLE \
	CONFIG_NSS_DRV_IPV6_ENABLE \
	CONFIG_NSS_DRV_IPV6_REASM_ENABLE \
	CONFIG_NSS_DRV_L2TP_ENABLE \
	CONFIG_NSS_DRV_LAG_ENABLE \
	CONFIG_NSS_DRV_LSO_RX_ENABLE \
	CONFIG_NSS_DRV_MAPT_ENABLE \
	CONFIG_NSS_DRV_MATCH_ENABLE \
	CONFIG_NSS_DRV_MIRROR_ENABLE \
	CONFIG_NSS_DRV_PPPOE_ENABLE \
	CONFIG_NSS_DRV_PPTP_ENABLE \
	CONFIG_NSS_DRV_QRFS_ENABLE \
	CONFIG_NSS_DRV_RMNET_ENABLE \
	CONFIG_NSS_DRV_SHAPER_ENABLE \
	CONFIG_NSS_DRV_TUN6RD_ENABLE \
	CONFIG_NSS_DRV_TUNIPIP6_ENABLE \
	CONFIG_NSS_DRV_VLAN_ENABLE \
	CONFIG_NSS_DRV_VXLAN_ENABLE \
	CONFIG_NSS_DRV_WIFIOFFLOAD_ENABLE \
	CONFIG_NSS_DRV_WIFI_MESH_ENABLE

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

ifeq ($(CONFIG_TARGET_SUBTARGET), "ipq807x")
  SOC="ipq807x_64"
  subtarget:=$(CONFIG_TARGET_SUBTARGET)
else ifeq ($(CONFIG_TARGET_SUBTARGET), "ipq60xx")
  SOC="ipq60xx_64"
  subtarget:=$(CONFIG_TARGET_SUBTARGET)
else ifeq ($(CONFIG_TARGET_SUBTARGET), "ipq50xx")
  SOC="ipq50xx_64"
  subtarget:=$(CONFIG_TARGET_SUBTARGET)
else
  SOC=$(CONFIG_TARGET_BOARD)
endif

define KernelPackage/qca-nss-drv-tun6rd
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS connection manager for 6rd tunnels
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_TUN6RD_ENABLE \
	   +6rd \
	   +kmod-sit
  FILES:=$(PKG_BUILD_DIR)/qca-nss-tun6rd.ko
  AUTOLOAD:=$(call AutoLoad,60,qca-nss-tun6rd)
endef

define KernelPackage/qca-nss-drv-tun6rd/description
Kernel modules for NSS connection manager - Support for 6rd tunnel
endef

define KernelPackage/qca-nss-drv-l2tpv2
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS connection manager for L2TPv2 protocol
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_L2TP_ENABLE \
	   +kmod-l2tp \
	   +kmod-ppp
  FILES:=$(PKG_BUILD_DIR)/l2tp/l2tpv2/qca-nss-l2tpv2.ko
  KCONFIG:=CONFIG_L2TP=y
  AUTOLOAD:=$(call AutoLoad,51,qca-nss-l2tpv2)
endef

define KernelPackage/qca-nss-drv-l2tpv2/description
Kernel modules for NSS connection manager - Support for l2tp tunnel
endef

define KernelPackage/qca-nss-drv-pptp
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS connection manager for PPTP protocol
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_PPTP_ENABLE \
	   +kmod-pptp
  FILES:=$(PKG_BUILD_DIR)/pptp/qca-nss-pptp.ko
  AUTOLOAD:=$(call AutoLoad,51,qca-nss-pptp)
endef

define KernelPackage/qca-nss-drv-pptp/description
Kernel modules for NSS connection manager - Support for PPTP tunnel
endef

define KernelPackage/qca-nss-drv-pppoe
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS connection manager for PPPoE protocol
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_PPPOE_ENABLE \
	   +kmod-bonding \
	   +kmod-ppp \
	   +kmod-pppoe
  FILES:=$(PKG_BUILD_DIR)/pppoe/qca-nss-pppoe.ko
  AUTOLOAD:=$(call AutoLoad,51,qca-nss-pppoe)
endef

define KernelPackage/qca-nss-drv-pppoe/Description
Kernel modules for NSS connection manager - Support for PPPoE
endef

define KernelPackage/qca-nss-drv-map-t
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS connection manager for MAP-T protocol
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_MAPT_ENABLE \
	   +kmod-nat46
  FILES:=$(PKG_BUILD_DIR)/map/map-t/qca-nss-map-t.ko
  AUTOLOAD:=$(call AutoLoad,51,qca-nss-map-t)
endef

define KernelPackage/qca-nss-drv-map-t/description
Kernel modules for NSS connection manager - Support for MAP-T
endef

define KernelPackage/qca-nss-drv-gre
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS connection manager for GRE protocol
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_GRE_ENABLE \
	   +kmod-gre6
  FILES:=$(PKG_BUILD_DIR)/gre/qca-nss-gre.ko $(PKG_BUILD_DIR)/gre/test/qca-nss-gre-test.ko
  AUTOLOAD:=$(call AutoLoad,51,qca-nss-gre)
endef

define KernelPackage/qca-nss-drv-gre/description
Kernel modules for NSS connection manager - Support for GRE
endef

define KernelPackage/qca-nss-drv-tunipip6
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS connection manager for IPIP6 tunnels
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_TUNIPIP6_ENABLE \
	   +kmod-ip6-tunnel \
	   +kmod-iptunnel6
  FILES:=$(PKG_BUILD_DIR)/tunipip6/qca-nss-tunipip6.ko
  AUTOLOAD:=$(call AutoLoad,60,qca-nss-tunipip6)
endef

define KernelPackage/qca-nss-drv-tunipip6/description
Kernel modules for NSS connection manager
Add support for DS-lite and ipip6 tunnel
endef

define KernelPackage/qca-nss-drv-bridge-mgr
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=Kernel driver for NSS bridge manager
  DEPENDS:=@(TARGET_qualcommax_ipq807x||TARGET_qualcommax_ipq60xx) \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_BRIDGE_ENABLE \
	   +kmod-qca-nss-drv-vlan-mgr \
	   +kmod-bonding
ifneq ($(CONFIG_PACKAGE_kmod-qca-ovsmgr),)
  DEPENDS+=+kmod-qca-ovsmgr
endif
  FILES:=$(PKG_BUILD_DIR)/bridge/qca-nss-bridge-mgr.ko
  AUTOLOAD:=$(call AutoLoad,51,qca-nss-bridge-mgr)
endef

define KernelPackage/qca-nss-drv-bridge-mgr/Description
Kernel modules for NSS bridge manager
endef

define KernelPackage/qca-nss-drv-vlan-mgr
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=Kernel driver for NSS vlan manager
  DEPENDS:=@(TARGET_qualcommax_ipq807x||TARGET_qualcommax_ipq60xx) \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_VLAN_ENABLE \
	   +kmod-bonding
  FILES:=$(PKG_BUILD_DIR)/vlan/qca-nss-vlan.ko
  AUTOLOAD:=$(call AutoLoad,51,qca-nss-vlan)
endef

define KernelPackage/qca-nss-drv-vlan-mgr/Description
Kernel modules for NSS vlan manager
endef

define KernelPackage/qca-nss-drv-qdisc
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=Qdisc for configuring shapers in NSS
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_SHAPER_ENABLE \
	   +!TARGET_qualcommax_ipq50xx:kmod-qca-nss-drv-bridge-mgr
  FILES:=$(PKG_BUILD_DIR)/nss_qdisc/qca-nss-qdisc.ko
  KCONFIG:=CONFIG_NET_CLS_ACT=y
endef

define KernelPackage/qca-nss-drv-qdisc/Description
Linux qdisc that aids in configuring shapers in the NSS
endef

define KernelPackage/qca-nss-drv-igs
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS connection manager to perform ingress shaping
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_IGS_ENABLE \
	   +kmod-qca-nss-drv-qdisc \
	   +kmod-ifb \
	   +kmod-nf-conntrack \
	   +kmod-sched-core
  FILES:=$(PKG_BUILD_DIR)/nss_qdisc/igs/act_nssmirred.ko
endef

define KernelPackage/qca-nss-drv-igs/description
Linux action that helps in offloading traffic to an IFB interface to perform ingress shaping.
endef

define KernelPackage/qca-nss-drv-lag-mgr
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS LAG (link aggregation) manager
  DEPENDS:=@(TARGET_qualcommax_ipq807x||TARGET_qualcommax_ipq60xx) \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_LAG_ENABLE \
	   +kmod-qca-nss-drv-vlan-mgr \
	   +kmod-bonding
  FILES:=$(PKG_BUILD_DIR)/lag/qca-nss-lag-mgr.ko
  AUTOLOAD:=$(call AutoLoad,51,qca-nss-lag-mgr)
endef

define KernelPackage/qca-nss-drv-lag-mgr/description
Kernel modules for NSS LAG manager
endef

define KernelPackage/qca-nss-drv-netlink
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS NETLINK manager for QCA NSS driver
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_IPV6_ENABLE \
	   +@NSS_DRV_WIFIOFFLOAD_ENABLE \
	   +@NSS_DRV_UDP_ST_ENABLE:NSS_DRV_RMNET_ENABLE \
	   +PACKAGE_kmod-qca-nss-drv-gre:kmod-qca-nss-drv-gre \
	   +PACKAGE_kmod-qca-nss-drv-igs:kmod-qca-nss-drv-igs \
	   +PACKAGE_kmod-qca-nss-drv-l2tpv2:kmod-qca-nss-drv-l2tpv2 \
	   +PACKAGE_kmod-qca-nss-drv-lag-mgr:kmod-qca-nss-drv-lag-mgr \
	   +PACKAGE_kmod-qca-nss-drv-map-t:kmod-qca-nss-drv-map-t \
	   +PACKAGE_kmod-qca-nss-drv-match:kmod-qca-nss-drv-match \
	   +PACKAGE_kmod-qca-nss-drv-mirror:kmod-qca-nss-drv-mirror \
	   +PACKAGE_kmod-qca-nss-drv-pppoe:kmod-qca-nss-drv-pppoe \
	   +PACKAGE_kmod-qca-nss-drv-pptp:kmod-qca-nss-drv-pptp \
	   +PACKAGE_kmod-qca-nss-drv-qdisc:kmod-qca-nss-drv-qdisc \
	   +PACKAGE_kmod-qca-nss-drv-tun6rd:kmod-qca-nss-drv-tun6rd \
	   +PACKAGE_kmod-qca-nss-drv-tunipip6:kmod-qca-nss-drv-tunipip6 \
	   +PACKAGE_kmod-qca-nss-drv-vxlanmgr:kmod-qca-nss-drv-vxlanmgr \
	   +@(PACKAGE_kmod-qca-nss-drv-gre):NSS_DRV_GRE_REDIR_ENABLE
  FILES:=$(PKG_BUILD_DIR)/netlink/qca-nss-netlink.ko
endef

define KernelPackage/qca-nss-drv-netlink/Description
Kernel module for NSS netlink manager
endef

define KernelPackage/qca-nss-drv-netlink/config
	source "$(SOURCE)/Config.in"
endef

define KernelPackage/qca-nss-drv-eogremgr
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS EOGRE manager for QCA NSS driver
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +kmod-qca-nss-drv-gre
  FILES:=$(PKG_BUILD_DIR)/eogremgr/qca-nss-eogremgr.ko
endef

define KernelPackage/qca-nss-drv-eogremgr/description
Kernel module for managing NSS EoGRE
endef

define KernelPackage/qca-nss-drv-vxlanmgr
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS VxLAN manager for QCA NSS driver
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_VXLAN_ENABLE \
	   +kmod-vxlan
  FILES:=$(PKG_BUILD_DIR)/vxlanmgr/qca-nss-vxlanmgr.ko
  AUTOLOAD:=$(call AutoLoad,51,qca-nss-vxlanmgr)
endef

define KernelPackage/qca-nss-drv-vxlanmgr/description
Kernel module for managing NSS VxLAN
endef

define KernelPackage/qca-nss-drv-match
 SECTION:=kernel
 CATEGORY:=Kernel modules
 SUBMENU:=Network Devices
 TITLE:=NSS Match for QCA NSS driver
 DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_MATCH_ENABLE \
	   +@NSS_DRV_WIFIOFFLOAD_ENABLE
 FILES:=$(PKG_BUILD_DIR)/match/qca-nss-match.ko
endef

define KernelPackage/qca-nss-drv-match/description
Kernel module for managing NSS Match
endef

define KernelPackage/qca-nss-drv-mirror
 SECTION:=kernel
 CATEGORY:=Kernel modules
 SUBMENU:=Network Devices
 TITLE:=Module for mirroring packets from NSS to host
 DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_MIRROR_ENABLE
 FILES:=$(PKG_BUILD_DIR)/mirror/qca-nss-mirror.ko
endef

define KernelPackage/qca-nss-drv-mirror/Description
Kernel module for managing NSS Mirror
endef

define KernelPackage/qca-nss-drv-wifi-meshmgr
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  TITLE:=NSS WiFi-Mesh manager for QCA NSS driver
  DEPENDS:=@TARGET_qualcommax \
	   +kmod-qca-nss-drv \
	   +@NSS_DRV_WIFI_MESH_ENABLE
  FILES:=$(PKG_BUILD_DIR)/wifi_meshmgr/qca-nss-wifi-meshmgr.ko
  AUTOLOAD:=$(call AutoLoad,51,qca-nss-wifi-meshmgr)
endef

define KernelPackage/qca-nss-drv-wifi-meshmgr/Description
Kernel module for WiFi Mesh manager
endef

define Build/InstallDev/qca-nss-clients
	$(INSTALL_DIR) $(1)/usr/include/qca-nss-clients
	$(CP) $(PKG_BUILD_DIR)/netlink/include/* $(1)/usr/include/qca-nss-clients/
	$(CP) $(PKG_BUILD_DIR)/exports/* $(1)/usr/include/qca-nss-clients/
endef

define Build/InstallDev
	$(call Build/InstallDev/qca-nss-clients,$(1))
endef

define KernelPackage/qca-nss-drv-netlink/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/qca-nss-netlink.init $(1)/etc/init.d/qca-nss-netlink
endef

EXTRA_CFLAGS+= \
	-I$(STAGING_DIR)/usr/include/qca-nss-drv \
	-I$(STAGING_DIR)/usr/include/qca-nss-crypto \
	-I$(STAGING_DIR)/usr/include/qca-nss-ecm \
	-I$(STAGING_DIR)/usr/include/qca-ssdk \
	-I$(STAGING_DIR)/usr/include/qca-ssdk/fal \
	-I$(STAGING_DIR)/usr/include/nat46

# Build individual packages if selected

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-tun6rd),)
NSS_CLIENTS_MAKE_OPTS+=tun6rd=m
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-l2tpv2),)
NSS_CLIENTS_MAKE_OPTS+=l2tpv2=y
EXTRA_CFLAGS += -DNSS_L2TPV2_ENABLED
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-pptp),)
NSS_CLIENTS_MAKE_OPTS+=pptp=y
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-map-t),)
NSS_CLIENTS_MAKE_OPTS+=map-t=y
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-tunipip6),)
NSS_CLIENTS_MAKE_OPTS+=tunipip6=y
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-qdisc),)
NSS_CLIENTS_MAKE_OPTS+=qdisc=y
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-igs),)
NSS_CLIENTS_MAKE_OPTS+=igs=y
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-bridge-mgr),)
NSS_CLIENTS_MAKE_OPTS+=bridge-mgr=y
#enable OVS bridge if ovsmgr is enabled
ifneq ($(CONFIG_PACKAGE_kmod-qca-ovsmgr),)
NSS_CLIENTS_MAKE_OPTS+= NSS_BRIDGE_MGR_OVS_ENABLE=y
EXTRA_CFLAGS+= -I$(STAGING_DIR)/usr/include/qca-ovsmgr
endif
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-vlan-mgr),)
NSS_CLIENTS_MAKE_OPTS+=vlan-mgr=y
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-lag-mgr),)
NSS_CLIENTS_MAKE_OPTS+=lag-mgr=y
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-gre),)
EXTRA_CFLAGS+= -I$(PKG_BUILD_DIR)/exports
NSS_CLIENTS_MAKE_OPTS+=gre=y
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-pppoe),)
NSS_CLIENTS_MAKE_OPTS+=pppoe=y
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-netlink),)
NSS_CLIENTS_MAKE_OPTS+=netlink=y

ifdef CONFIG_NSS_DRV_UDP_ST_ENABLE
NSS_CLIENTS_MAKE_OPTS+=CONFIG_NSS_NLUDP_ST=y
endif

ifdef CONFIG_NSS_DRV_QRFS_ENABLE
NSS_CLIENTS_MAKE_OPTS+=CONFIG_NSS_NLQRFS=y
endif

ifdef CONFIG_NSS_DRV_GRE_REDIR_ENABLE
NSS_CLIENTS_MAKE_OPTS+=CONFIG_NSS_NLGRE_REDIR_FAMILY=y
endif

ifdef CONFIG_NSS_DRV_IPV4_REASM_ENABLE
NSS_CLIENTS_MAKE_OPTS+=CONFIG_NSS_NLIPV4_REASM=y
endif

ifdef CONFIG_NSS_DRV_IPV6_REASM_ENABLE
NSS_CLIENTS_MAKE_OPTS+=CONFIG_NSS_NLIPV6_REASM=y
endif

ifdef CONFIG_NSS_DRV_LSO_RX_ENABLE
NSS_CLIENTS_MAKE_OPTS+=CONFIG_NSS_NLLSO_RX=y
endif

ifeq ($(CONFIG_KERNEL_IPQ_MEM_PROFILE),256)
EXTRA_CFLAGS+= -DNSS_NETLINK_UDP_ST_NO_RMNET_SUPPORT
else ifeq ($(CONFIG_LOWMEM_FLASH),y)
EXTRA_CFLAGS+= -DNSS_NETLINK_UDP_ST_NO_RMNET_SUPPORT
endif

endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-eogremgr),)
NSS_CLIENTS_MAKE_OPTS+=eogremgr=y
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-vxlanmgr),)
NSS_CLIENTS_MAKE_OPTS+=vxlanmgr=y
EXTRA_CFLAGS += -DNSS_VXLAN_ENABLED
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-match),)
NSS_CLIENTS_MAKE_OPTS+=match=y
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-mirror),)
NSS_CLIENTS_MAKE_OPTS+=mirror=y
endif

ifneq ($(CONFIG_PACKAGE_kmod-qca-nss-drv-wifi-meshmgr),)
NSS_CLIENTS_MAKE_OPTS+=wifi-meshmgr=y
endif

EXTRA_CFLAGS+= \
	-Wno-missing-prototypes \
	-Wno-missing-declarations \
	-Wno-empty-body

define Build/Compile
	+$(MAKE) -C "$(LINUX_DIR)" $(strip $(NSS_CLIENTS_MAKE_OPTS)) \
	  CROSS_COMPILE="$(TARGET_CROSS)" \
	  ARCH="$(LINUX_KARCH)" \
	  M="$(PKG_BUILD_DIR)" \
	  EXTRA_CFLAGS="$(EXTRA_CFLAGS)" \
	  SoC=$(SOC) \
	  $(KERNEL_MAKE_FLAGS) \
	  $(PKG_JOBS) \
	  modules
endef

$(eval $(call KernelPackage,qca-nss-drv-tun6rd))
$(eval $(call KernelPackage,qca-nss-drv-l2tpv2))
$(eval $(call KernelPackage,qca-nss-drv-pptp))
$(eval $(call KernelPackage,qca-nss-drv-pppoe))
$(eval $(call KernelPackage,qca-nss-drv-map-t))
$(eval $(call KernelPackage,qca-nss-drv-tunipip6))
$(eval $(call KernelPackage,qca-nss-drv-qdisc))
$(eval $(call KernelPackage,qca-nss-drv-igs))
$(eval $(call KernelPackage,qca-nss-drv-netlink))
$(eval $(call KernelPackage,qca-nss-drv-bridge-mgr))
$(eval $(call KernelPackage,qca-nss-drv-vlan-mgr))
$(eval $(call KernelPackage,qca-nss-drv-lag-mgr))
$(eval $(call KernelPackage,qca-nss-drv-gre))
$(eval $(call KernelPackage,qca-nss-drv-eogremgr))
$(eval $(call KernelPackage,qca-nss-drv-vxlanmgr))
$(eval $(call KernelPackage,qca-nss-drv-match))
$(eval $(call KernelPackage,qca-nss-drv-mirror))
$(eval $(call KernelPackage,qca-nss-drv-wifi-meshmgr))
