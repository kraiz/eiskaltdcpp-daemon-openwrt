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
endef

define Package/eiskaltdcpp/description
  EiskaltDC++ is a cross-platform program that uses the Direct Connect and ADC protocols
endef

define Build/Configure
	$(call Build/Configure/Default)
endef

#TOOL_PATH = ${STAGING_DIR}/../toolchain-mips_34kc_gcc-4.8-linaro_uClibc-0.9.33.2
#ENV_PATH = ${STAGING_DIR}/../target-mips_34kc_uClibc-0.9.33.2
#TARGET_CFLAGS += -DDSO_DLFCN -DHAVE_DLFCN_H -I${ENV_PATH}/usr/include -I${ENV_PATH}/include -I${TOOL_PATH}/usr/include -I${TOOL_PATH}/include -Os -pipe -mno-branch-likely -mips32r2 -mtune=34kc -fno-caller-saves -fhonour-copts -Wno-error=unused-but-set-variable -msoft-float -fpic -fomit-frame-pointer -Wall

CMAKE_OPTIONS = \
#	-DCMAKE_BUILD_TYPE=Release  \
#	-DCMAKE_INSTALL_PREFIX=/opt  \
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
#   -DCMAKE_C_COMPILER=$(TOOL_PATH)/bin/mips-openwrt-linux-uclibc-gcc \
#	-DCMAKE_CXX_COMPILER=$(TOOL_PATH)/bin/mips-openwrt-linux-uclibc-g++ \
#	-DCMAKE_FIND_ROOT_PATH=$(ENV_PATH)

define Package/eiskaltdcpp/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/eiskaltdcpp-daemon $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,eiskaltdcpp))
