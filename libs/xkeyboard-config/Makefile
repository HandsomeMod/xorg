#
# Copyright (C) 2019 Lucian Cristian <lucian.cristian@gmail.com>
# Copyright (C) 2020-2021 HandsomeMod Project
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=xkeyboard-config
PKG_VERSION:=2.32
PKG_RELEASE:=1

PKG_SOURCE_URL:=http://xorg.freedesktop.org/archive/individual/data/$(PKG_NAME)/
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_HASH:=1feee317ba39b91902b0cbd2987c0c73e6afbfc8f4c096367a5c86c216c036a8

PKG_BUILD_DEPENDS:=intltool/host perl-xml-parser/host
PKG_BUILD_PARALLEL:=1
#PKG_FIXUP:=autoconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/xkeyboard-config
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libx11 +xkbcomp
  TITLE:=X keyboard configuration files
  URL:=http://www.freedesktop.org/wiki/Software/XKeyboardConfig
endef

CONFIGURE_VARS+= \
	PATH=$(STAGING_DIR_HOSTPKG)/bin:$(STAGING_DIR_HOSTPKG)/usr/bin:$(PATH)

MAKE_FLAGS+= \
	PATH=$(STAGING_DIR_HOSTPKG)/bin:$(STAGING_DIR_HOSTPKG)/usr/bin:$(PATH)

MAKE_VARS+= \
	PATH=$(STAGING_DIR_HOSTPKG)/bin:$(STAGING_DIR_HOSTPKG)/usr/bin:$(PATH)

CONFIGURE_ARGS += \
  --with-xkb-rules-symlink=xorg \
  --enable-compat-rules=yes \
  --without-xsltproc \
  --enable-runtime-deps \
  --prefix=/usr

define Build/InstallDev
	$(INSTALL_DIR) \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/share/pkgconfig \
	  $(1)/usr/lib/
endef

define Package/xkeyboard-config/install
	$(INSTALL_DIR) \
	  $(1)/usr/share

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/share/X11 \
	  $(1)/usr/share/
endef

$(eval $(call BuildPackage,xkeyboard-config))
