#
# Copyright (C) 2016-2019 Jason A. Donenfeld <Jason@zx2c4.com>
# Copyright (C) 2016 Baptiste Jonglez <openwrt@bitsofnetworks.org>
# Copyright (C) 2016-2017 Dan Luedtke <mail@danrl.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=amneziawg-tools
PKG_VERSION:=0.0.1
PKG_RELEASE:=1

PKG_SOURCE:=v$(PKG_VERSION)-kmod.tar.gz
PKG_SOURCE_URL:=https://github.com/amnezia-vpn/amnezia-wg-tools/archive/refs/tags/
PKG_HASH:=cc4f523f7ec171b7bb3bdd1bcf4ff2f6833364fab6cad309310a84f33eeafa9b

PKG_MAINTAINER:=Amnezia Admin <admin@amnezia.org>
PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DIR=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)-kmod

include $(INCLUDE_DIR)/package.mk

MAKE_PATH:=src
MAKE_VARS += PLATFORM=linux

define Package/amneziawg-tools
  CATEGORY:=Network
  URL:=https://amnezia.org/
  MAINTAINER:=Iurii Egorov <admin@amnezia.org>
  TITLE:=AmneziaWG userspace control program (amneziawg)
  DEPENDS:= \
	  +@BUSYBOX_CONFIG_IP \
	  +@BUSYBOX_CONFIG_FEATURE_IP_LINK
endef

define Package/amneziawg-tools/description
  Amnezia VPN — simple and free app to run a self-hosted VPN with
	high privacy requirements.

  This package provides the userspace control program for AmneziaWG,
  `amneziawg`, a netifd protocol helper, and a re-resolve watchdog script.
endef

define Package/amneziawg-tools/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/wg $(1)/usr/bin/amneziawg
	$(INSTALL_BIN) ./files/amneziawg_watchdog $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/lib/netifd/proto/
	$(INSTALL_BIN) ./files/amneziawg.sh $(1)/lib/netifd/proto/
endef

$(eval $(call BuildPackage,amneziawg-tools))
