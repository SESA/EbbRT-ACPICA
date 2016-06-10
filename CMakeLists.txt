cmake_minimum_required(VERSION 2.6)

# This must be before the project() command so cmake finds our platform
# definition
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/../../cmake")

# This skips compiler verification which will fail because we haven't finished
# installing the necessary libraries
set(CMAKE_C_COMPILER_WORKS 1)

project(Acpica C)

# Initialize CXXFLAGS.
set(CMAKE_C_FLAGS                "-Wall -Werror -DACPI_LIBRARY -iquote ${CMAKE_SOURCE_DIR}/include")
set(CMAKE_C_FLAGS_DEBUG          "-O0 -g")
set(CMAKE_C_FLAGS_MINSIZEREL     "-Os -DNDEBUG")
set(CMAKE_C_FLAGS_RELEASE        "-O4 -flto -DNDEBUG")
set(CMAKE_C_FLAGS_RELWITHDEBINFO "-O2 -g")

add_library(acpica STATIC
  ${CMAKE_SOURCE_DIR}/components/tables/tbfind.c
  ${CMAKE_SOURCE_DIR}/components/tables/tbxfroot.c
  ${CMAKE_SOURCE_DIR}/components/tables/tbutils.c
  ${CMAKE_SOURCE_DIR}/components/tables/tbxface.c
  ${CMAKE_SOURCE_DIR}/components/tables/tbfadt.c
  ${CMAKE_SOURCE_DIR}/components/tables/tbinstal.c
  ${CMAKE_SOURCE_DIR}/components/tables/tbxfload.c
  ${CMAKE_SOURCE_DIR}/components/tables/tbprint.c
  ${CMAKE_SOURCE_DIR}/components/resources/rsdump.c
  ${CMAKE_SOURCE_DIR}/components/resources/rsinfo.c
  ${CMAKE_SOURCE_DIR}/components/resources/rsserial.c
  ${CMAKE_SOURCE_DIR}/components/resources/rsio.c
  ${CMAKE_SOURCE_DIR}/components/resources/rsmemory.c
  ${CMAKE_SOURCE_DIR}/components/resources/rsdumpinfo.c
  ${CMAKE_SOURCE_DIR}/components/resources/rsmisc.c
  ${CMAKE_SOURCE_DIR}/components/resources/rsutils.c
  ${CMAKE_SOURCE_DIR}/components/resources/rsaddr.c
  ${CMAKE_SOURCE_DIR}/components/resources/rscalc.c
  ${CMAKE_SOURCE_DIR}/components/resources/rslist.c
  ${CMAKE_SOURCE_DIR}/components/resources/rscreate.c
  ${CMAKE_SOURCE_DIR}/components/resources/rsxface.c
  ${CMAKE_SOURCE_DIR}/components/resources/rsirq.c
  ${CMAKE_SOURCE_DIR}/components/events/evregion.c
  ${CMAKE_SOURCE_DIR}/components/events/evsci.c
  ${CMAKE_SOURCE_DIR}/components/events/evgpeinit.c
  ${CMAKE_SOURCE_DIR}/components/events/evxface.c
  ${CMAKE_SOURCE_DIR}/components/events/evrgnini.c
  ${CMAKE_SOURCE_DIR}/components/events/evgpeblk.c
  ${CMAKE_SOURCE_DIR}/components/events/evgpeutil.c
  ${CMAKE_SOURCE_DIR}/components/events/evxfgpe.c
  ${CMAKE_SOURCE_DIR}/components/events/evglock.c
  ${CMAKE_SOURCE_DIR}/components/events/evxfevnt.c
  ${CMAKE_SOURCE_DIR}/components/events/evhandler.c
  ${CMAKE_SOURCE_DIR}/components/events/evgpe.c
  ${CMAKE_SOURCE_DIR}/components/events/evmisc.c
  ${CMAKE_SOURCE_DIR}/components/events/evxfregn.c
  ${CMAKE_SOURCE_DIR}/components/events/evevent.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dsobject.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dswload2.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dswscope.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dsutils.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dswstate.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dsargs.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dsfield.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dswexec.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dsmethod.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dscontrol.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dsinit.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dswload.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dsmthdat.c
  ${CMAKE_SOURCE_DIR}/components/dispatcher/dsopcode.c
  ${CMAKE_SOURCE_DIR}/components/executer/exregion.c
  ${CMAKE_SOURCE_DIR}/components/executer/exconfig.c
  ${CMAKE_SOURCE_DIR}/components/executer/exmisc.c
  ${CMAKE_SOURCE_DIR}/components/executer/exprep.c
  ${CMAKE_SOURCE_DIR}/components/executer/excreate.c
  ${CMAKE_SOURCE_DIR}/components/executer/exfldio.c
  ${CMAKE_SOURCE_DIR}/components/executer/exfield.c
  ${CMAKE_SOURCE_DIR}/components/executer/exstorob.c
  ${CMAKE_SOURCE_DIR}/components/executer/exnames.c
  ${CMAKE_SOURCE_DIR}/components/executer/exdump.c
  ${CMAKE_SOURCE_DIR}/components/executer/exoparg3.c
  ${CMAKE_SOURCE_DIR}/components/executer/exresop.c
  ${CMAKE_SOURCE_DIR}/components/executer/exstore.c
  ${CMAKE_SOURCE_DIR}/components/executer/exdebug.c
  ${CMAKE_SOURCE_DIR}/components/executer/exoparg2.c
  ${CMAKE_SOURCE_DIR}/components/executer/exstoren.c
  ${CMAKE_SOURCE_DIR}/components/executer/exsystem.c
  ${CMAKE_SOURCE_DIR}/components/executer/exoparg1.c
  ${CMAKE_SOURCE_DIR}/components/executer/exutils.c
  ${CMAKE_SOURCE_DIR}/components/executer/exresnte.c
  ${CMAKE_SOURCE_DIR}/components/executer/exmutex.c
  ${CMAKE_SOURCE_DIR}/components/executer/exoparg6.c
  ${CMAKE_SOURCE_DIR}/components/executer/exresolv.c
  ${CMAKE_SOURCE_DIR}/components/executer/exconvrt.c
  ${CMAKE_SOURCE_DIR}/components/disassembler/dmobject.c
  ${CMAKE_SOURCE_DIR}/components/disassembler/dmutils.c
  ${CMAKE_SOURCE_DIR}/components/disassembler/dmresrcl.c
  ${CMAKE_SOURCE_DIR}/components/disassembler/dmbuffer.c
  ${CMAKE_SOURCE_DIR}/components/disassembler/dmresrcs.c
  ${CMAKE_SOURCE_DIR}/components/disassembler/dmwalk.c
  ${CMAKE_SOURCE_DIR}/components/disassembler/dmnames.c
  ${CMAKE_SOURCE_DIR}/components/disassembler/dmresrc.c
  ${CMAKE_SOURCE_DIR}/components/disassembler/dmdeferred.c
  ${CMAKE_SOURCE_DIR}/components/disassembler/dmopcode.c
  ${CMAKE_SOURCE_DIR}/components/disassembler/dmresrcl2.c
  ${CMAKE_SOURCE_DIR}/components/debugger/dbfileio.c
  ${CMAKE_SOURCE_DIR}/components/debugger/dbdisply.c
  ${CMAKE_SOURCE_DIR}/components/debugger/dbstats.c
  ${CMAKE_SOURCE_DIR}/components/debugger/dbexec.c
  ${CMAKE_SOURCE_DIR}/components/debugger/dbnames.c
  ${CMAKE_SOURCE_DIR}/components/debugger/dbutils.c
  ${CMAKE_SOURCE_DIR}/components/debugger/dbcmds.c
  ${CMAKE_SOURCE_DIR}/components/debugger/dbinput.c
  ${CMAKE_SOURCE_DIR}/components/debugger/dbconvert.c
  ${CMAKE_SOURCE_DIR}/components/debugger/dbxface.c
  ${CMAKE_SOURCE_DIR}/components/debugger/dbhistry.c
  ${CMAKE_SOURCE_DIR}/components/debugger/dbmethod.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsprepkg.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsxfname.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsconvert.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsrepair.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsobject.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsutils.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsdump.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nssearch.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nspredef.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsxfeval.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsdumpdv.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsaccess.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsalloc.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsarguments.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsrepair2.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsparse.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nseval.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsxfobj.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsnames.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nswalk.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsinit.c
  ${CMAKE_SOURCE_DIR}/components/namespace/nsload.c
  ${CMAKE_SOURCE_DIR}/components/hardware/hwgpe.c
  ${CMAKE_SOURCE_DIR}/components/hardware/hwvalid.c
  ${CMAKE_SOURCE_DIR}/components/hardware/hwsleep.c
  ${CMAKE_SOURCE_DIR}/components/hardware/hwxface.c
  ${CMAKE_SOURCE_DIR}/components/hardware/hwregs.c
  ${CMAKE_SOURCE_DIR}/components/hardware/hwpci.c
  ${CMAKE_SOURCE_DIR}/components/hardware/hwxfsleep.c
  ${CMAKE_SOURCE_DIR}/components/hardware/hwacpi.c
  ${CMAKE_SOURCE_DIR}/components/hardware/hwtimer.c
  ${CMAKE_SOURCE_DIR}/components/hardware/hwesleep.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utcopy.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utstring.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utxface.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utmath.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utexcep.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utalloc.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utmutex.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utstate.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utids.c
  ${CMAKE_SOURCE_DIR}/components/utilities/uttrack.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utxferror.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utownerid.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utxfinit.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utcache.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utaddress.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utdecode.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utosi.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utclib.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utpredef.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utglobal.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utmisc.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utlock.c
  ${CMAKE_SOURCE_DIR}/components/utilities/uteval.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utobject.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utdelete.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utresrc.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utinit.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utdebug.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utbuffer.c
  ${CMAKE_SOURCE_DIR}/components/utilities/uterror.c
  ${CMAKE_SOURCE_DIR}/components/utilities/utxfmutex.c
  ${CMAKE_SOURCE_DIR}/components/parser/pswalk.c
  ${CMAKE_SOURCE_DIR}/components/parser/psparse.c
  ${CMAKE_SOURCE_DIR}/components/parser/psopcode.c
  ${CMAKE_SOURCE_DIR}/components/parser/pstree.c
  ${CMAKE_SOURCE_DIR}/components/parser/psscope.c
  ${CMAKE_SOURCE_DIR}/components/parser/psxface.c
  ${CMAKE_SOURCE_DIR}/components/parser/psutils.c
  ${CMAKE_SOURCE_DIR}/components/parser/psloop.c
  ${CMAKE_SOURCE_DIR}/components/parser/psopinfo.c
  ${CMAKE_SOURCE_DIR}/components/parser/psobject.c
  ${CMAKE_SOURCE_DIR}/components/parser/psargs.c
  )

install(TARGETS acpica
  ARCHIVE DESTINATION lib)

install(DIRECTORY ${CMAKE_SOURCE_DIR}/include/ DESTINATION include
  FILES_MATCHING PATTERN "*.h")
