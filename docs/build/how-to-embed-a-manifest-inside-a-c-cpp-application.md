---
title: 'Postupy: vložení manifestu do aplikace C/C++ | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
- embedding manifests
- makefiles, updating to embed manifest
ms.assetid: ec0bac69-2fdc-466c-ab0d-710a22974e5d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a759533a8e88ef05e3660e0e9b36525df378334
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369049"
---
# <a name="how-to-embed-a-manifest-inside-a-cc-application"></a>Postupy: Vložení manifestu do aplikace C/C++
Je doporučeno, že aplikace C/C++ (nebo knihovna) mají jeho manifest vložená do konečné binární, protože zaručí se tím správný modul runtime chování ve většině scénářů. Ve výchozím nastavení [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] pokusí k sestavení projektu ze zdrojových souborů pro vložení manifestu; viz [generování manifestu v sadě Visual Studio](../build/manifest-generation-in-visual-studio.md) Další informace. Ale pokud je aplikace vytvořené s použitím nmake, některé změny existujícího souboru pravidel jsou nezbytné. V této části ukazuje, jak změnit stávající soubory pravidel pro automaticky vložení manifestu do konečné binárního souboru.  
  
## <a name="two-approaches"></a>Dva přístupy  
 Existují dva způsoby pro vložení manifestu do aplikace nebo knihovny.  
  
-   Pokud nejsou provádění přírůstkové sestavení můžete přímo vložení manifestu pomocí příkazového řádku, který je podobný následujícímu jako krok po sestavení:  
  
     **mt.exe-manifest MyApp.exe.manifest-outputresource:MyApp.exe;1**  
  
     or  
  
     **mt.exe-manifest MyLibrary.dll.manifest-outputresource:MyLibrary.dll;2**  
  
     (1 pro EXE, 2 pro knihovny DLL.)  
  
-   Pokud byste přírůstkové sestavení, přímou úpravou prostředku, jak je vidět tady bude zakažte přírůstkové sestavování a způsobit úplné opětovné sestavení; Proto by měla být provedena jiný přístup:  
  
    -   Propojte binárního souboru ke generování souboru MyApp.exe.manifest.  
  
    -   Převeďte manifest souboru prostředků.  
  
    -   Znovu propojte (přírůstkově) pro vložení manifestu prostředků do binárního souboru.  
  
 Následující příklady ukazují, jak změnit soubory pravidel začlenit obě metody.  
  
## <a name="makefiles-before"></a>Soubory pravidel (před)  
 Vezměte v úvahu nmake skript pro MyApp.exe, jednoduchou aplikaci z jednoho souboru:  
  
```  
# build MyApp.exe  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /INCREMENTAL  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
!endif  
  
MyApp.exe : MyApp.obj  
    link $** /out:$@ $(LFLAGS)  
  
MyApp.obj : MyApp.cpp  
  
clean :   
    del MyApp.obj MyApp.exe  
```  
  
 Pokud tento skript se spustí s Visual C++ beze změny, vytvoří úspěšně MyApp.exe. Vytvoří také externí souboru manifestu MyApp.exe.manifest, pro použití v operačním systému k načtení závislé sestavení za běhu.  
  
 Velmi podobná nmake skript pro MyLibrary.dll:  
  
```  
# build MyLibrary.dll  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /DLL /INCREMENTAL  
  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
LFLAGS=$(LFLAGS) /DLL  
  
!endif  
  
MyLibrary.dll : MyLibrary.obj  
    link $** /out:$@ $(LFLAGS)  
  
MyLibrary.obj : MyLibrary.cpp  
  
clean :   
    del MyLibrary.obj MyLibrary.dll  
```  
  
## <a name="makefiles-after"></a>Soubory pravidel (po)  
 K sestavení s vložených manifesty, je nutné provést čtyři malé změny k původní soubory pravidel. Pro soubor pravidel MyApp.exe:  
  
```  
# build MyApp.exe  
!include makefile.inc  
#^^^^^^^^^^^^^^^^^^^^ Change #1. (Add full path if necessary.)  
  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /INCREMENTAL  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
!endif  
  
MyApp.exe : MyApp.obj  
    link $** /out:$@ $(LFLAGS)  
    $(_VC_MANIFEST_EMBED_EXE)  
#^^^^^^^^^^^^^^^^^^^^^^^^^^^^ Change #2  
  
MyApp.obj : MyApp.cpp  
  
clean :   
    del MyApp.obj MyApp.exe  
    $(_VC_MANIFEST_CLEAN)  
#^^^^^^^^^^^^^^^^^^^^^^^^ Change #3  
  
!include makefile.targ.inc  
#^^^^^^^^^^^^^^^^^^^^^^^^^ Change #4. (Add full path if necessary.)  
```  
  
 Pro soubor pravidel MyLibrary.dll:  
  
```  
# build MyLibrary.dll  
!include makefile.inc  
#^^^^^^^^^^^^^^^^^^^^ Change #1. (Add full path if necessary.)  
  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /DLL /INCREMENTAL  
  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
LFLAGS=$(LFLAGS) /DLL  
  
!endif  
  
MyLibrary.dll : MyLibrary.obj  
    link $** /out:$@ $(LFLAGS)  
    $(_VC_MANIFEST_EMBED_DLL)  
#^^^^^^^^^^^^^^^^^^^^^^^^^^^^ Change #2.  
  
MyLibrary.obj : MyLibrary.cpp  
  
clean :   
    del MyLibrary.obj MyLibrary.dll  
    $(_VC_MANIFEST_CLEAN)  
#^^^^^^^^^^^^^^^^^^^^^^^^ Change #3.  
  
!include makefile.targ.inc  
#^^^^^^^^^^^^^^^^^^^^^^^^^ Change #4. (Add full path if necessary.)  
```  
  
 Soubory pravidel teď obsahuje dva soubory, které provádějí skutečné pracovní, makefile.inc a makefile.targ.inc.  
  
 Vytvořte makefile.inc a zkopírujte do něj následující:  
  
```  
# makefile.inc -- Include this file into existing makefile at the very top.  
  
# _VC_MANIFEST_INC specifies whether build is incremental (1 - incremental).  
# _VC_MANIFEST_BASENAME specifies name of a temporary resource file.  
  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /INCREMENTAL  
_VC_MANIFEST_INC=1  
_VC_MANIFEST_BASENAME=__VC90.Debug  
  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
_VC_MANIFEST_INC=0  
_VC_MANIFEST_BASENAME=__VC90  
  
!endif  
  
####################################################  
# Specifying name of temporary resource file used only in incremental builds:  
  
!if "$(_VC_MANIFEST_INC)" == "1"  
_VC_MANIFEST_AUTO_RES=$(_VC_MANIFEST_BASENAME).auto.res  
!else  
_VC_MANIFEST_AUTO_RES=  
!endif  
  
####################################################  
# _VC_MANIFEST_EMBED_EXE - command to embed manifest in EXE:  
  
!if "$(_VC_MANIFEST_INC)" == "1"  
  
#MT_SPECIAL_RETURN=1090650113  
#MT_SPECIAL_SWITCH=-notify_resource_update  
MT_SPECIAL_RETURN=0  
MT_SPECIAL_SWITCH=  
_VC_MANIFEST_EMBED_EXE= \  
if exist $@.manifest mt.exe -manifest $@.manifest -out:$(_VC_MANIFEST_BASENAME).auto.manifest $(MT_SPECIAL_SWITCH) & \  
if "%ERRORLEVEL%" == "$(MT_SPECIAL_RETURN)" \  
rc /r $(_VC_MANIFEST_BASENAME).auto.rc & \  
link $** /out:$@ $(LFLAGS)  
  
!else  
  
_VC_MANIFEST_EMBED_EXE= \  
if exist $@.manifest mt.exe -manifest $@.manifest -outputresource:$@;1  
  
!endif  
  
####################################################  
# _VC_MANIFEST_CLEAN - command to clean resources files generated temporarily:  
  
!if "$(_VC_MANIFEST_INC)" == "1"  
  
_VC_MANIFEST_CLEAN=-del $(_VC_MANIFEST_BASENAME).auto.res \  
    $(_VC_MANIFEST_BASENAME).auto.rc \  
    $(_VC_MANIFEST_BASENAME).auto.manifest  
  
!else  
  
_VC_MANIFEST_CLEAN=  
  
!endif  
  
# End of makefile.inc   
####################################################  
```  
  
 Teď vytvořte makefile.targ.inc a zkopírujte do něj následující:  
  
```  
# makefile.targ.inc - include this at the very bottom of the existing makefile  
  
####################################################  
# Commands to generate initial empty manifest file and the RC file  
# that references it, and for generating the .res file:  
  
$(_VC_MANIFEST_BASENAME).auto.res : $(_VC_MANIFEST_BASENAME).auto.rc  
  
$(_VC_MANIFEST_BASENAME).auto.rc : $(_VC_MANIFEST_BASENAME).auto.manifest  
    type <<$@  
#include <winuser.h>  
1RT_MANIFEST"$(_VC_MANIFEST_BASENAME).auto.manifest"  
<< KEEP  
  
$(_VC_MANIFEST_BASENAME).auto.manifest :  
    type <<$@  
<?xml version='1.0' encoding='UTF-8' standalone='yes'?>  
<assembly xmlns='urn:schemas-microsoft-com:asm.v1' manifestVersion='1.0'>  
</assembly>  
<< KEEP  
  
# end of makefile.targ.inc  
```  
  
## <a name="see-also"></a>Viz také  
 [Základní informace o generování manifestu pro programy C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)