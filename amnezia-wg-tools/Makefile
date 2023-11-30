#
# Copyright (C) 2016-2019 Jason A. Donenfeld <Jason@zx2c4.com>
# Copyright (C) 2016 Baptiste Jonglez <openwrt@bitsofnetworks.org>
# Copyright (C) 2016-2017 Dan Luedtke <mail@danrl.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=amnezia-wg-tools

PKG_VERSION:=0.0.1-kmod
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/amnezia-vpn/amnezia-wg-tools/archive/refs/tags/
PKG_HASH:=0d8cdf6d767700cb6d2cc895d45b1f94668663b00138627329766bb9e36d894e

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=COPYING


include $(INCLUDE_DIR)/package.mk

MAKE_PATH:=src
MAKE_VARS += PLATFORM=linux

define Package/amnezia-wg-tools
  CATEGORY:=Network
  URL:=https://www.wireguard.com
  MAINTAINER:=Jason A. Donenfeld <Jason@zx2c4.com>
  TITLE:=WireGuard userspace control program (wg)
  DEPENDS:= \
	  +@BUSYBOX_CONFIG_IP \
	  +@BUSYBOX_CONFIG_FEATURE_IP_LINK
endef

define Package/amnezia-wg-tools/description
  WireGuard is a novel VPN that runs inside the Linux Kernel and utilizes
  state-of-the-art cryptography. It aims to be faster, simpler, leaner, and
  more useful than IPSec, while avoiding the massive headache. It intends to
  be considerably more performant than OpenVPN.  WireGuard is designed as a
  general purpose VPN for running on embedded interfaces and super computers
  alike, fit for many different circumstances. It uses UDP.

  This package provides the userspace control program for WireGuard,
  `wg(8)`, a netifd protocol helper, and a re-resolve watchdog script.
endef

define Package/amnezia-wg-tools/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/wg $(1)/usr/bin/amneziawg
	$(INSTALL_BIN) ./files/amneziawg_watchdog $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/lib/netifd/proto/
	$(INSTALL_BIN) ./files/amneziawg.sh $(1)/lib/netifd/proto/
endef

$(eval $(call BuildPackage,amnezia-wg-tools))