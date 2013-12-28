#
# Copyright (C) 2013 Michael Heimpold
#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libsomsp
PKG_VERSION:=2013-12-09
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/mhei/libsomsp.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=b220cf626966d4c38039b3ede8989ce739c21a8b
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_LICENSE:=LGPLv2.1
PKG_LICENSE_FILES:=

PKG_MAINTAINER:=Michael Heimpold <mhei@heimpold.de>

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libsomsp
  SECTION:=metering
  CATEGORY:=Metering
  DEPENDS:=+librt
  TITLE:=Library for the SOMS protocol
endef

define Package/libsomsp/description
  libsomsp is a free software library to send/receive data streams with the
  Simple Open Metering Specification Protocol. This protocol is a lightweight
  binary protocol with the focus on transmitting metering data from meters
  over IP. It uses the Object Identification System (OBIS) as defined by the
  OMS Group (http://www.oms-group.org/) to identify meter readings.
endef

define Build/Configure
	( cd "$(PKG_BUILD_DIR)"; ./autogen.sh )
	$(call Build/Configure/Default)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

define Package/libsomsp/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libsomsp))
