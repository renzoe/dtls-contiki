all: dtls-client dtls-server

	$(MAKE) $(MAKEFLAGS) ROLE=server dtls-server
	$(MAKE) $(MAKEFLAGS) clean
	$(MAKE) $(MAKEFLAGS) ROLE=client dtls-client

CONTIKI = ../../contiki
CFLAGS += -DPROJECT_CONF_H=\"project-conf.h\"

# Out-of-tree App Development for contiki 2.7 Issue: https://github.com/contiki-os/contiki/issues/289
APPDS += $(addprefix ../../apps/, $(APPS))
APPS  += dtls

DTLS=1


ifneq ($(ROLE),client)
 CFLAGS += -DHARD_CODED_ADDRESS=\"aaaa::02:232\"
else
 CFLAGS += -DHARD_CODED_ADDRESS=\"aaaa::02:230\"
endif



# IPv6
WITH_UIP6=1
CFLAGS += -DUIP_CONF_IPV6=1


# variable for Makefile.include
ifneq ($(TARGET), minimal-net)

 CFLAGS += -DUIP_CONF_IPV6_RPL=0
 CFLAGS += -DUIP_CONF_ROUTER=0
 #CFLAGS+=-DUIP_CONF_IPV6_CHECKS=1 #this gave me debug

else

 #${info INFO: compiling without RPL}
 #CFLAGS += -DUIP_CONF_IPV6_RPL=0

endif


include $(CONTIKI)/Makefile.include

