include $(TOPDIR)/rules.mk

PKG_NAME:=msgpack
PKG_VERSION:=2017-03-11
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/msgpack/msgpack-c.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=597cd63121a3a01b812b27a75621fe5fc4a640ad
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1
CMAKE_INSTALL:=1
#CMAKE_OPTIONS += -DSYSCONF_INSTALL_DIR=/etc

PKG_MAINTAINER:=DS
PKG_LICENSE:=MIT
PKG_FIXUP:=autoreconf
#PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/msgpack
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=msgpack lib
  DEPENDS:=+pkg-config +libtool-bin +libopenssl +libconfig +libevent +ncurses +libevent2
endef

define Build/Configure
  $(call Build/Configure/Default)
endef

define Package/msgpack/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/lib* $(1)/usr/lib
endef

$(eval $(call BuildPackage,msgpack))
