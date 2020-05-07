---
title: 'Postupy: Vložení manifestu do aplikace C/C++'
ms.date: 05/06/2019
helpviewer_keywords:
- manifests [C++]
- embedding manifests
- makefiles, updating to embed manifest
ms.assetid: ec0bac69-2fdc-466c-ab0d-710a22974e5d
ms.openlocfilehash: 2f125ee445d4ee9efdf21c37134d4c5adbca256d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322971"
---
# <a name="how-to-embed-a-manifest-inside-a-cc-application"></a>Postupy: Vložení manifestu do aplikace C/C++

Doporučujeme, abyste vložili manifest vaší aplikace nebo knihovny do finálního binárního souboru, protože to garantuje správné běhové chování ve většině scénářů. Ve výchozím nastavení se Visual Studio pokusí vložit manifest při sestavení projektu. Další informace naleznete v tématu [generování manifestu v aplikaci Visual Studio](manifest-generation-in-visual-studio.md). Pokud však sestavíte aplikaci pomocí nástroje NMAKE, je nutné provést nějaké změny souboru pravidel. V této části se dozvíte, jak změnit soubory pravidel tak, aby automaticky vložily manifest do finálního binárního souboru.

## <a name="two-approaches"></a>Dva přístupy

Existují dva způsoby, jak vložit manifest do aplikace nebo knihovny.

- Pokud neprovádíte přírůstkové sestavení, můžete manifest přímo vložit pomocí příkazového řádku podobného následujícímu jako krok po sestavení:

   ```cmd
   mt.exe -manifest MyApp.exe.manifest -outputresource:MyApp.exe;1
   ```

   – nebo –

   ```cmd
   mt.exe -manifest MyLibrary.dll.manifest -outputresource:MyLibrary.dll;2
   ```

   Použijte 1 pro EXE a 2 pro knihovnu DLL.

- Pokud provádíte přírůstkové sestavení, použijte následující postup:

  - Vytvořte propojení binárního souboru, aby se vygeneroval soubor MyApp. exe. manifest.

  - Převeďte manifest na soubor prostředků.

  - Znovu propojit (přírůstkově) pro vložení prostředku manifestu do binárního souboru.

Následující příklady ukazují, jak změnit soubory pravidel pro zahrnutí obou postupů.

## <a name="makefiles-before"></a>Soubory pravidel (před)

Zvažte skript NMAKE pro MyApp. exe, jednoduchou aplikaci vytvořenou z jednoho souboru:

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

Pokud se tento skript v aplikaci Visual Studio nezměnil, úspěšně vytvoří MyApp. exe. Vytvoří také externí soubor manifestu MyApp. exe. manifest, který bude použit operačním systémem k načtení závislých sestavení za běhu.

Skript NMAKE pro MyLibrary. dll vypadá velmi podobně:

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

## <a name="makefiles-after"></a>Soubory pravidel (za)

Pro sestavování pomocí vložených manifestů musíte provést čtyři malé změny původních souborů pravidel. Pro soubor MyApp. exe makefile:

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

Pro soubor pravidel MyLibrary. dll:

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

Soubory pravidel nyní obsahují dva soubory, které mají skutečnou práci, makefile. Inc a makefile. cílo. Inc.

Vytvořte soubor makefile. Inc a zkopírujte do něj následující:

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

Nyní vytvořte **soubor pravidel. cílo. Inc** a zkopírujte do něj následující:

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

[Základní informace o generování manifestu pro programy C/C++](understanding-manifest-generation-for-c-cpp-programs.md)
