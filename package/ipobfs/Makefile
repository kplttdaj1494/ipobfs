include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=ipobfs
PKG_RELEASE:=1
PKG_VERSION:=1.0

PKG_BUILD_DIR:=$(KERNEL_BUILD_DIR)/ipobfs-$(PKG_VERSION)
export KERNELDIR:=$(LINUX_DIR)

include $(INCLUDE_DIR)/package.mk


# User space package definition removed - building kernel module only

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./ipobfs_mod $(PKG_BUILD_DIR)/
endef

define Build/Compile
	$(MAKE) $(KERNEL_MAKEOPTS) -C $(PKG_BUILD_DIR)/ipobfs_mod
endef

include $(INCLUDE_DIR)/kernel-defaults.mk
include $(INCLUDE_DIR)/package-defaults.mk


define KernelPackage/ipobfs
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Zapret
  TITLE:=ipobfs kernel module
  FILES:= $(PKG_BUILD_DIR)/ipobfs_mod/ipobfs.$(LINUX_KMOD_SUFFIX)
endef


$(eval $(call KernelPackage,ipobfs))
