#
# Copyright (C) 2016 Dan Luedtke <mail@danrl.com>
#
# This is free software, licensed under the Apache License, Version 2.0 .
#

include $(TOPDIR)/rules.mk

PKG_MAINTAINER:=Amnezia Admin <admin@amnezia.org>
LUCI_TITLE:=AmneziaWG Web UI
LUCI_DESCRIPTION:=Provides Web UI for AmneziaWG
PKG_VERSION:=2.0.4
LUCI_DEPENDS:=+amneziawg-tools +ucode +luci-lib-uqr +resolveip
LUCI_PKGARCH:=all
PKGARCH:=all

PKG_LICENSE:=Apache-2.0
PKG_PROVIDES:=luci-proto-amneziawg

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
