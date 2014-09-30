include $(TOPDIR)/rules.mk

PKG_NAME:=eiskaltdcpp
PKG_VERSION:=0.1.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/eiskaltdcpp/eiskaltdcpp.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=c3822eefefb5a94e1686029542b8152e73bf889d
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/eiskaltdcpp
  SECTION:=base
  CATEGORY:=Network
  TITLE:=Eiskalt DC++ Client
  URL:=https://github.com/eiskaltdcpp/eiskaltdcpp
  DEPENDS:=+bzip2
endef

define Package/eiskaltdcpp/description
  EiskaltDC++ is a cross-platform program that uses the Direct Connect and ADC protocols
endef

define Build/Configure
	$(call Build/Configure/Default)
endef

CMAKE_OPTIONS = \
	-DUSE_IDNA=OFF  \
	-DLINK=STATIC  \
	-DUSE_QT=OFF  \
	-DFREE_SPACE_BAR_C=OFF  \
	-DDBUS_NOTIFY=OFF  \
	-DUSE_LIBNOTIFY=OFF  \
	-DNO_UI_DAEMON=ON  \
	-DJSONRPC_DAEMON=ON  \
	-DWITH_EMOTICONS=OFF  \
	-DWITH_EXAMPLES=OFF  \
	-DFORCE_XDG=OFF  \
	-DLOCAL_BOOST=ON  \
	-DDO_NOT_USE_MUTEX=ON 
    -DCMAKE_C_COMPILER=$(TOOLCHAIN_DIR)/bin/mips-openwrt-linux-uclibc-gcc \
 	-DCMAKE_CXX_COMPILER=$(TOOLCHAIN_DIR)/bin/mips-openwrt-linux-uclibc-g++

define Package/eiskaltdcpp/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/eiskaltdcpp-daemon $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,eiskaltdcpp))
