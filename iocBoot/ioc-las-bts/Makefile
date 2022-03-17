IOC_TOP=/reg/g/pcds/epics/ioc/common/ads-ioc/R0.5.0/
IOC_INSTANCE_PATH := $(shell pwd)

# Set PRODUCTION_IOC to 1 to move from a testing to a production IOC:
PRODUCTION_IOC := 1

PROJECT_NAME := lcls-plc-las-bts
PROJECT_PATH := ../../lcls-plc-las-bts/lcls-plc-las-bts.tsproj
PLC := las_bts

PYTMC_OPTS := 
PREFIX := PLC:LAS:BTS

# With two $$, as in $$(IOC) below, this will be expanded in the
# environment of st.cmd:
DB_PARAMETERS := 'SIM=,BTPS=LTLHN:BTPS,PREFIX=$(PREFIX):,IOCNAME=$$(IOC),IOC=$$(IOC)'

all: build paths clean fix_archive_file

fix_archive_file:
	msi -M $(DB_PARAMETERS),IOC=ioc-las-bts \
		$(ARCHIVE_PATH)/las_bts.db.archive > $(ARCHIVE_PATH)/.las_bts.db.archive
	install -p -m 0444 $(ARCHIVE_PATH)/.las_bts.db.archive $(ARCHIVE_PATH)/las_bts.db.archive

include $(IOC_TOP)/iocBoot/templates/Makefile.base
