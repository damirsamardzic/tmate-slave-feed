include $(TOPDIR)/rules.mk

PKG_NAME:=tmate-slave
PKG_VERSION:=2017-03-11
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/tmate-io/tmate-slave.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=76ec591e91731f49d1b1f4d3339d73b95d13e11b
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1
#CMAKE_INSTALL:=1
#CMAKE_OPTIONS += -DSYSCONF_INSTALL_DIR=/etc

PKG_MAINTAINER:=DS
PKG_LICENSE:=MIT
PKG_FIXUP:=autoreconf
#PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
#include $(INCLUDE_DIR)/cmake.mk

define Package/tmate-slave
  SECTION:=net
  CATEGORY:=Network
  TITLE:=tmate slave server
  DEPENDS:=+pkg-config +libtool-bin +libopenssl +libconfig +libevent +libevent2 +msgpack +libssh +uclibcxx +libncursesw +libncurses +libpthread +bash +openssh-keygen +librt +terminfo
endef

define Build/Configure
  $(call Build/Configure/Default, --enable-debug=no --enable-latency=no)
endef

TARGET_CFLAGS += -D_GNU_SOURCE

define Package/tmate-slave/install
	$(INSTALL_DIR) $(1)/usr/bin $(1)/etc/tmate-slave $(1)/etc/init.d $(1)/etc/config
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tmate-slave $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/create_key* $(1)/etc/tmate-slave
	$(INSTALL_BIN) ./files/tmate-slave.init $(1)/etc/init.d/tmate-slave
	$(INSTALL_DATA) ./files/tmate-slave.conf $(1)/etc/config/tmate-slave
endef

$(eval $(call BuildPackage,tmate-slave))
