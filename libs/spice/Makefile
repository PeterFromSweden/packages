#
# Copyright (C) 2019 Yousong Zhou <yszhou4tech@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=spice
PKG_VERSION:=0.14.1
PKG_RELEASE:=1
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://www.spice-space.org/download/releases/spice-server
PKG_HASH:=1ead5de63d06eededed4017db37240f07bef0abffbaf621899647e7e685a1519
PKG_LICENSE:=LGPL-2.1-only
PKG_LICENSE_FILES:=COPYING
PKG_INSTALL:=1
PKG_MAINTAINER:=Yousong Zhou <yszhou4tech@gmail.com>

PKG_BUILD_DEPENDS+=spice-protocol

include $(INCLUDE_DIR)/package.mk

define Package/libspice-server
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=SPICE server library
  URL:=https://www.spice-space.org/index.html
  DEPENDS:=+glib2 +libjpeg +libopenssl +pixman +zlib
endef

define Package/libspice-server/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libspice-server.so* $(1)/usr/lib
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib
endef

# audio codec
CONFIGURE_ARGS += \
	--disable-opus \
	--disable-celt051 \

CONFIGURE_ARGS += \
	--disable-lz4 \
	--disable-manual \
	--disable-gstreamer \
	--disable-smartcard \
	--disable-statistics \

$(eval $(call BuildPackage,libspice-server))
