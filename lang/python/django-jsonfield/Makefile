#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=django-jsonfield
PKG_VERSION:=1.0.1
PKG_RELEASE:=5

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/source/d/$(PKG_NAME)/
PKG_HASH:=6c0afd5554739365b55d86e285cf966cc3a45682fff963463364ea1f6511ca3e

PKG_MAINTAINER:=Alexandru Ardelean <ardeleanalex@gmail.com>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/$(PKG_NAME)/Default
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=JSONField for django models
  URL:=https://github.com/adamchainz/django-jsonfield
endef

define Package/python-$(PKG_NAME)
$(call Package/$(PKG_NAME)/Default)
  DEPENDS:= \
	+PACKAGE_python-$(PKG_NAME):python \
	python-django1
  VARIANT:=python
  MDEPENDS:=python-django1
endef

define Package/python-$(PKG_NAME)/description
  JSONField for django models
endef

define Package/python3-$(PKG_NAME)
$(call Package/$(PKG_NAME)/Default)
  DEPENDS:= \
	+PACKAGE_python3-$(PKG_NAME):python3 \
	python3-django
  VARIANT:=python3
  MDEPENDS:=python3-django
endef

define Package/python3-$(PKG_NAME)/description
$(call define Package/python-$(PKG_NAME)/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-$(PKG_NAME)))
$(eval $(call BuildPackage,python-$(PKG_NAME)))
$(eval $(call BuildPackage,python-$(PKG_NAME)-src))

$(eval $(call Py3Package,python3-$(PKG_NAME)))
$(eval $(call BuildPackage,python3-$(PKG_NAME)))
$(eval $(call BuildPackage,python3-$(PKG_NAME)-src))
