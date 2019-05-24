
# Copyright (C) 2016 Onion Corporation
# 
# Author: Lazar Demin  <lazar@onion.io>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
PKG_NAME:=hlk7688a-pins-ctrl
PKG_VERSION:=0.4
PKG_RELEASE:=1


PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=fc35371610c0a1e6a6a751bfe6c8b5ccff153651
PKG_SOURCE_URL:=https://github.com/Tolmeros/hlk7688a-pins-ctrl.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk


# application package
define Package/$(PKG_NAME)
	SECTION:=hlk7688a
	CATEGORY:=hlk7688a
	SUBMENU:=Utilities
	TITLE:=Utility to control the hlk7688a low-level hardware (pins assignment)
endef

define Package/$(PKG_NAME)/description
Utility to control the Omega2's low-level hardware
endef


#TARGET_LIB += -lpthread -lcurl -loniondebug -ljson-c -lubus -lubox -lblobmsg_json -luci
TARGET_CFLAGS += $(FPIC) 

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
	CC="$(TARGET_CC)" \
	CFLAGS="$(TARGET_CFLAGS)" \
	LDFLAGS="$(TARGET_LDFLAGS)" \
	LIB="$(TARGET_LIB)"
endef


define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	# install the binary
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bin/hlk7688a-pins-ctrl $(1)/usr/bin/
	# Should make link aka pins-ctrl to hlk7688a-pins-ctrl ?
endef



$(eval $(call BuildPackage,$(PKG_NAME)))

