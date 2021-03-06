# $Id: Makefile,v 1.21 2012/01/20 19:49:49 kreis Exp $

#########################################################################
# XDAQ Components for Distributed Data Acquisition                      #
# Copyright (C) 2000-2004, CERN.			                #
# All rights reserved.                                                  #
# Authors: J. Gutleber and L. Orsini					#
#                                                                       #
# For the licensing terms see LICENSE.		                        #
# For the list of contributors see CREDITS.   			        #
#########################################################################

##
#
# This is the example Makefile
#
# make Library=ExampleName
#
##
include $(XDAQ_ROOT)/config/mfAutoconf.rules
include $(XDAQ_ROOT)/config/mfDefs.$(XDAQ_OS)

Project=pixel
Package=PixelFECSupervisor

Sources=PixelFECSupervisor.cc

IncludeDirs = \
        $(BUILD_HOME)/$(Project) \
        $(XDAQ_ROOT)/include/hal \
        $(XDAQ_ROOT)/include/i2o \
        $(XDAQ_ROOT)/include/i2o/shared \
        $(XDAQ_ROOT)/include/interface/evb \
        $(XDAQ_ROOT)/include/interface/shared \
        $(ENV_CMS_TK_DIAG_ROOT)/tools/soapdiagappender/include \
        $(ENV_CMS_TK_DIAG_ROOT)/tools/xmldiagappender/include \
        $(ENV_CMS_TK_DIAG_ROOT)/tools/diagbag/include \
        $(ENV_CMS_TK_DIAG_ROOT)/toolbox \
        $(ENV_CMS_TK_DIAG_ROOT)/ 

LibraryDirs = 

UserSourcePath = 

UserCFlags = -O
UserCCFlags = -g -O -Wno-long-long
UserDynamicLinkFlags =
UserStaticLinkFlags =
UserExecutableLinkFlags =

# These libraries can be platform specific and
# potentially need conditional processing
#

DependentLibraryDirs =  $(BUILD_HOME)/pixel/lib \
			$(ENV_CMS_TK_DIAG_ROOT)/tools/lib \
                        $(XDAQ_ROOT)/lib	

DependentLibraries = PixelFECInterface SiPixelObjects TkDiagBagWizard xmldiagappender PixelTestStandUtilities PixelGUIUtilities GenericHAL CAENVME CAENLinuxBusAdapter PixelDCSUtilities Pixelb2inUtilities occi nnz11 clntsh


ifeq ($(VMEDUMMY), yes)
UserCCFlags += -DVMEDUMMY
BusAdapter:=DummyBusAdapters
endif


Libraries = 

#
# Compile the source files and create a shared library
#

DynamicLibrary= PixelFECSupervisor


StaticLibrary=

ifdef Executable
Libraries=toolbox xdata xcept xoap xerces-c log4cplus mimetic
Executables= $(Executable).cc
endif

include $(XDAQ_ROOT)/config/Makefile.rules
include $(BUILD_HOME)/$(Project)/RPM.version
include $(XDAQ_ROOT)/config/mfRPM.rules
