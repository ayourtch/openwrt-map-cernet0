#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=map-mdpc
PKG_VERSION:=00001
PKG_RELEASE:=00001

PKG_SOURCE_URL:=https://github.com/ayourtch/mdpc.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=eef3fc50c380ec165c3ad31be690760887de9d60
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/map-mdpc/$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/map-mdpc
  SECTION:=net
  DEPENDS:=+odhcp6c +map-cernet
  CATEGORY:=Network
  TITLE:=MAP DHCPv6 Provisioning Cruft
  MAINTAINER:=Andrew Yourtchenko <ayourtch@gmail.com>
  PKGARCH:=all
endef

define Package/map-mdpc/description
Provides the mdpc utility to generate the CLI for ivictl based on the DHCP parameters from odhcp6c.
endef

define Build/Compile
	$(TARGET_CC) -o $(PKG_BUILD_DIR)/mdpc \
                $(PKG_BUILD_DIR)/mdpc.c 
endef

define Build/Configure
endef

#        $(CP) -r ./files/* $(1)/
define Package/map-mdpc/install
	$(INSTALL_DIR) $(1)/sbin
	$(CP) -r ./files/* $(1)/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mdpc $(1)/sbin/
endef

$(eval $(call BuildPackage,map-mdpc))
