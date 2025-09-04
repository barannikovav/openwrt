include $(TOPDIR)/rules.mk

PKG_NAME:=wireless-regdb
PKG_RELEASE:=1
PKG_LICENSE:=ISC
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE_URL:=https://github.com/yapqq/unlimit-regdb
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2024-10-14
PKG_SOURCE_VERSION:=de796831228e27cc5c9b2130fe55c279bfaa88d0
PKG_MIRROR_HASH:=e5e7ed60771c7a21f7aa445e08091ee43bccd888bc2c5f47968bc0491e4330dc

PKG_MAINTAINER:=Felix Fietkau <nbd@nbd.name>

include $(INCLUDE_DIR)/package.mk

define Package/wireless-regdb
  PKGARCH:=all
  SECTION:=firmware
  CATEGORY:=Firmware
  URL:=https://git.kernel.org/pub/scm/linux/kernel/git/wens/wireless-regdb.git
  TITLE:=Wireless Regulatory Database
endef

define Build/Compile
	$(STAGING_DIR_HOST)/bin/$(PYTHON) $(PKG_BUILD_DIR)/db2fw.py $(PKG_BUILD_DIR)/regulatory.db $(PKG_BUILD_DIR)/db.txt
endef

define Package/wireless-regdb/install
	$(INSTALL_DIR) $(1)/lib/firmware
	$(CP) $(PKG_BUILD_DIR)/regulatory.db $(1)/lib/firmware/
endef

$(eval $(call BuildPackage,wireless-regdb))
