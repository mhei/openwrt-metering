#
# Copyright (C) 2013 Michael Heimpold
#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=sunsmeterd
PKG_VERSION:=2013-12-09
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/mhei/sunsmeterd.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=549700ed6ad9ffe7af3a630c0759e24fb0c725ad
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_LICENSE:=GPLv2
PKG_LICENSE_FILES:=

PKG_MAINTAINER:=Michael Heimpold <mhei@heimpold.de>

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/sunsmeterd
  SECTION:=metering
  CATEGORY:=Metering
  DEPENDS:=+libsomsp +libmodbus +libdaemon
  TITLE:=SOMSP/SunSpec converter daemon
endef

define Package/sunsmeterd/description
  The sunsmeter daemon receives a SOMSP stream (simple open metering specification
  protocol) from a metering daemon and provides this data using SunSpec Alliance's
  meter modell via Modbus (e.g. Modbus/RTU via RS-485... or Modbus/TCP via Ethernet).
endef

define Build/Configure
	( cd "$(PKG_BUILD_DIR)"; ./autogen.sh )
	$(call Build/Configure/Default)
endef

define Package/sunsmeterd/conffiles
/etc/config/sunsmeterd
endef

define Package/sunsmeterd/install
	$(INSTALL_DIR) $(1)/etc/config $(1)/etc/init.d $(1)/usr/bin

	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/sunsmeterd $(1)/usr/bin/
	$(INSTALL_BIN) ./files/sunsmeterd.init $(1)/etc/init.d/sunsmeterd
	$(INSTALL_CONF) ./files/sunsmeterd.config $(1)/etc/config/sunsmeterd
endef

$(eval $(call BuildPackage,sunsmeterd))
