#
# Copyright (C) 2014-2017 ZengFei Zhang <zhangzengfei@kunteng.org>
#
# This is free software, licensed under the GNU General Public License v3.
# See /LICENSE for more information.
#
# update log:
# 	tag:0.07.451 commit:2429f797214980abbb60815970ee16c4f469725e add ftp support

include $(TOPDIR)/rules.mk

PKG_NAME:=xfrpc
PKG_VERSION:=0.07.496
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://gitee.com/apfree/xfrp.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_VERSION)

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)


include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/$(PKG_NAME)
  SECTION:=net
  CATEGORY:=Network
  URL:=https://github.com/KunTengRom/xfrp
  TITLE:=xfrps client for Embedded system
  DEPENDS:=+libevent2 +libopenssl +libjson-c +zlib
endef

define Package/$(PKG_NAME)/description
	xFrps is a fast reverse proxy to help you expose a local server behind a NAT or firewall to the internet.
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin $(1)/etc/config $(1)/etc/init.d
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/xfrpc $(1)/usr/bin/xfrpc
	$(INSTALL_CONF) ./files/xfrpc.config $(1)/etc/config/xfrpc
	$(INSTALL_BIN) ./files/xfrpc.init $(1)/etc/init.d/xfrpc

	# register package into kt market
	$(INSTALL_DIR) $(1)/etc/market
	$(INSTALL_DIR) $(1)/etc/market/$(PKG_NAME)
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
