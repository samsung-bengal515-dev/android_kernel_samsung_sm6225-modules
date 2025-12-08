KBUILD_OPTIONS += TOUCH_ROOT=$(KERNEL_SRC)/$(M)
KBUILD_OPTIONS += MODNAME?=touch_dlkm

#KBUILD_EXTRA_SYMBOLS += $(M)/../display-drivers/msm/dsi/Module.symvers
KBUILD_EXTRA_SYMBOLS +=$(OUT)/obj/sm6225-modules/qcom/opensource/display-drivers/msm/Module.symvers
ifeq ($(SEC_SAMSUNG_EXPERIENCE_PLATFORM_CATEGORY), sep_lite_new)
	KBUILD_EXTRA_SYMBOLS += $(KERNEL_SRC)/drivers/samsung/bsp/class/Module.symvers
endif
export KBUILD_EXTRA_SYMBOLS

all:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) modules $(KBUILD_OPTIONS)

modules_install:
	$(MAKE) INSTALL_MOD_STRIP=1 -C $(KERNEL_SRC) M=$(M) modules_install

%:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) $@ $(KBUILD_OPTIONS) $(KBUILD_EXTRA_SYMBOLS)

clean:
	rm -f *.o *.ko *.mod.c *.mod.o *~ .*.cmd Module.symvers
	rm -rf .tmp_versions
