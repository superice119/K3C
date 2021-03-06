#
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=socat
PKG_VERSION:=1.7.1.3
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://www.dest-unreach.org/socat/download/
PKG_MD5SUM:=2081987fb0cb0290b8105574058cb329

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/socat
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libpthread
  TITLE:=A multipurpose relay (SOcket CAT)
  URL:=http://www.dest-unreach.org/socat/
endef

define Package/socat/description
	SoCat (for SOcket CAT) establishes two bidirectional byte streams and
	transfers data between them.
	Data channels may be files, pipes, devices (terminal or modem, etc.), or
	sockets (Unix, IPv4, IPv6, raw, UDP, TCP, SSL). It provides forking,
	logging and tracing, different modes for interprocess communication and
	many more options.
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--disable-libwrap \
		--disable-readline \
		--disable-openssl \
		--enable-termios \
		, \
		sc_cv_termios_ispeed="no" \
		sc_cv_sys_crdly_shift=9 \
		sc_cv_sys_tabdly_shift=11 \
		sc_cv_sys_csize_shift=4 \
	)
endef

define Package/socat/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/socat $(1)/usr/bin/
endef

$(eval $(call BuildPackage,socat))
