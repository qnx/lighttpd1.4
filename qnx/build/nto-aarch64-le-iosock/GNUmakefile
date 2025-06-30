ifneq ($(wildcard $(QNX_TARGET)/io-sock),)
    $(info "+++ IO-SOCK FOUND +++")
    ifndef QCONFIG
        QCONFIG=qconfig.mk
    endif
    include $(QCONFIG)
    include $(MKFILES_ROOT)/qmake-cfg.mk
else
$(warning "--- IO-SOCK NOT FOUND ---")
all:
install:
check:
clean:

endif
