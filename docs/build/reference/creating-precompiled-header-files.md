---
title: "Vytváření předkompilovaných hlavičkových souborů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: pch
dev_langs: C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8d33382e520a13c5cd131cdc03f21fb4708cb9eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-precompiled-header-files"></a>Vytváření předkompilovaných hlavičkových souborů
  
Kompilátory jazyka Microsoft C a C++ nabízí možnosti pro předkompilaci kódu žádné jazyka C nebo C++, včetně vloženého kódu. Pomocí této funkce výkonu můžete kompilovat stabilní tělo kódu, ukládat zkompilovaný kód v souboru a, během následných kompilací seskupovat předkompilovaný kód s kódem, který je pořád ve vývoji. Každá následná kompilace je rychlejší, protože není potřeba zopakovat kód stabilní.  
  
Toto téma obsahuje následující témata předkompilovaných hlaviček:  
  
-   [Kdy předkompilovat zdrojový kód](#when-to-precompile-source-code)  
  
-   [Dvě možnosti pro předkompilaci kódu](#two-choices-for-precompiling-code)  
  
-   [Pravidla konzistence předkompilovaných hlaviček](#precompiled-header-consistency-rules)  
  
-   [Pravidla konzistence pro použití předkompilovaných hlaviček podle souborů](#consistency-rules-for-per-file-use-of-precompiled-headers)  
  
-   [Pravidla konzistence pro /Yc a /Yu](#consistency-rules-for-yc-and-yu)  
  
-   [Použití předkompilovaných hlaviček v projektu](#using-precompiled-headers-in-a-project)  
  
-   [Soubory PCH v procesu sestavení](#pch-files-in-the-build-process)  
  
-   [Ukázkový soubor pravidel pro PCH](#sample-makefile-for-pch)  
  
-   [Ukázkový kód pro PCH](#example-code-for-pch)  
  
Referenční informace o možnostech kompilátoru související s předkompilovaných hlaviček najdete v tématu [/Y (předkompilované hlavičky)](../../build/reference/y-precompiled-headers.md).  
  
<a name="when-to-precompile-source-code"></a>  
  
## <a name="when-to-precompile-source-code"></a>Kdy předkompilovat zdrojový kód  
  
Předkompilované kód je užitečná během cyklu vývoje zkrátit dobu kompilace, zvlášť pokud:  
  
-   Vždy používejte rozsáhlý soubor kódu, která se zřídka mění.  
  
-   Váš program se skládá z více modulů, které všechny používají standardní sadu zahrnout soubory a stejné možnosti jako kompilace. V takovém případě obsahují soubory můžete předkompilovaných do jednoho předkompilovaných hlaviček.  
  
První kompilace – ten, který vytvoří soubor předkompilovaných hlaviček (PCH) – trvá trochu déle než následné kompilace. Následné kompilace můžete pokračovat rychleji zahrnutím předkompilovaných kódu.  
  
Můžete předkompilovat programy C a C++. V jazyce C++ programování je běžnou praxí oddělit informace o třídě rozhraní do hlavičkových souborů. Tyto soubory hlaviček můžou být součástí později programy, které používají třídu. Předkompilace tyto hlavičky, můžete snížit dobu, kterou program vyžádá zkompilovat.  
  
> [!NOTE]
>  Přestože je možné použít pouze jeden soubor předkompilovaných hlaviček (.pch) na zdrojový soubor, můžete použít více .pch soubory v projektu.  
  
<a name="two-choices-for-precompiling-code"></a>  
  
# <a name="two-choices-for-precompiling-code"></a>Dvě možnosti pro předkompilaci kódu  
  
S Visual C++ může předkompilovat jazyka C nebo C++ kódu; nejste omezená na předkompilace pouze soubory hlaviček.  
  
Předkompilace vyžaduje plánování, ale nabízí výrazně rychlejší kompilace Pokud předkompilovat zdrojový kód než jednoduché hlavičkových souborů.  
  
Předkompilujte kód, když víte, že zdrojové soubory vašeho použít společné sady soubory hlaviček, ale neobsahují je ve stejném pořadí, nebo pokud chcete zahrnout do vaší předkompilaci zdrojového kódu.  
  
Jsou možnosti předkompilovaných hlaviček [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) a [/Yu (Použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md). Použití **/Yc** vytvořit předkompilovaných hlaviček. Při použití s nepovinným [hdrstop –](../../preprocessor/hdrstop.md) – Direktiva pragma, **/Yc** umožňuje předkompilovat oba soubory hlaviček a zdrojový kód. Vyberte **/Yu** používat existující předkompilovaných hlaviček v existující kompilace. Můžete také použít **/Fp** s **/Yc** a **/Yu** možnosti poskytnout alternativní název pro předkompilované hlavičky.  
  
Referenční témata – možnost kompilátoru pro **/Yu** a **/Yc** popisují postup přístup k této funkci ve vývojovém prostředí.  
  
<a name="precompiled-header-consistency-rules"></a>  
  
## <a name="precompiled-header-consistency-rules"></a>Pravidla konzistence předkompilovaných hlaviček  
  
Soubory PCH obsahovat informace o prostředí počítače a paměti adresu informace o programu, byste měli používat jenom soubor PCH na počítači, kde se vytvořila.  
  
<a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>  
  
## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Pravidla konzistence pro použití předkompilovaných hlaviček podle souborů

[/Yu](../../build/reference/yu-use-precompiled-header-file.md) – možnost kompilátoru umožňuje určit soubor PCH.  
  
Při použití souborů PCH kompilátor předpokládá stejné prostředí kompilace – ten, který používá – možnosti kompilátoru konzistentní, pragmas a tak dále –, který byl v platnosti když vytvoříte soubor PCH, pokud neurčíte jinak. Pokud kompilátor zjistí nekonzistence, vydá upozornění a identifikuje nekonzistencí, kde je to možné. Takové upozornění nutně znamenat problém se souborem PCH; upozorňují jednoduše je možné je v konfliktu. Požadavky na konzistence pro soubory PCH jsou popsané v následujících částech.  
  
### <a name="compiler-option-consistency"></a>Konzistence – možnost kompilátoru  
  
Následující možnosti kompilátoru můžete aktivovat upozornění nekonzistenci při použití souborů PCH:  
  
-   Makra vytvořený preprocesor (/ D) možnost musí být stejná mezi kompilace vytvořený soubor PCH a aktuální kompilace. Stav definované konstanty není zaškrtnuto, ale vést k neočekávaným výsledkům může dojít, pokud tyto změnit.  
  
-   Soubory PCH s možností/e a /EP nefungují.  
  
-   Soubory PCH musí být vytvořen pomocí buď vygenerovat procházet informace (/ FR) možnost nebo vyloučit lokální proměnné (/ Fr) možnost následné kompilace, které používají soubor PCH mohli používat tyto možnosti.  
  
### <a name="c-70-compatible-z7"></a>C kompatibilní 7.0 (/ Z7)  
  
Pokud tato možnost je v platnosti při vytváření souboru PCH, můžete použít následné kompilace, které používají soubor PCH informace o ladění.  
  
Pokud C kompatibilní 7.0 (/ Z7) možnost není platit při vytváření souboru PCH, následné kompilace, které používají soubor PCH a /Z7 aktivovat upozornění. Informace o ladění je umístěn v souboru .obj aktuální, a lokální symboly definované v souboru PCH nejsou k dispozici pro ladicí program.  
  
### <a name="include-path-consistency"></a>Zahrnout cesta konzistence  
  
Soubor PCH neobsahuje informace o cestě zahrnout, která byla v platnosti, když byla vytvořena. Při použití souborů PCH kompilátor vždy používá zadaná cesta zahrnutí v aktuální kompilace.  
  
### <a name="source-file-consistency"></a>Zdrojový soubor konzistence  
  
Pokud zadáte možnost Použít předkompilovaný hlavičkový soubor (/Yu), kompilátor ignoruje všechny preprocesor – direktivy (včetně direktivy), které se zobrazují ve zdrojovém kódu, který bude předkompilovaných. Kompilace určeného takové direktivy preprocesoru musí být stejný jako kompilace používá pro možnost Vytvořit předkompilovaný hlavičkový soubor (/Yc).  
  
### <a name="pragma-consistency"></a>Konzistence – Direktiva pragma    
  
Direktivy zpracování při vytváření souboru PCH obvykle vliv na soubor, ke které je soubor PCH následně použít. `comment` a `message` direktivy neovlivní zbytek kompilace.  
  
Tyto direktivy vliv pouze na kód v souboru PCH; kód, který je následně použije soubor PCH neovlivňují:  
  
||||  
|-|-|-|  
|`comment`|`page`|`subtitle`|  
|`linesize`|`pagesize`|`title`|  
|`message`|`skip`||  
  
Tyto direktivy jsou uchovány v rámci předkompilovaných hlaviček a ovlivnit zbytek kompilace, která používá předkompilované hlavičky:  
  
||||  
|-|-|-|  
|`alloc_text`|`include_alias`|`pack`|  
|`auto_inline`|`init_seg`|`pointers_to_members`|  
|`check_stack`|`inline_depth`|`setlocale`|  
|`code_seg`|`inline_recursion`|`vtordisp`|  
|`data_seg`|`intrinsic`|`warning`|  
|`function`|`optimize`||  
  
<a name="consistency-rules-for-yc-and-yu"></a>  
  
## <a name="consistency-rules-for-yc-and-yu"></a>Pravidla konzistence pro /Yc a /Yu  
  
Při použití předkompilovaných hlaviček vytvořený /Yc a /Yu kompilátor porovná aktuální kompilace prostředí tak, aby ten, který při vytvoření souboru PCH. Nezapomeňte zadat konzistentní s předchozím kódem (pomocí možnosti konzistentní kompilátoru, pragmas a tak dále) pro aktuální kompilace prostředí. Pokud kompilátor zjistí nekonzistence, vydá upozornění a identifikuje nekonzistencí, kde je to možné. Takové upozornění není nutně znamenat problém související s soubor PCH; upozorňují jednoduše je možné je v konfliktu. Následující části popisují požadavky na konzistence předkompilovaných hlaviček.  
  
### <a name="compiler-option-consistency"></a>Konzistence – možnost kompilátoru  
  
Tato tabulka uvádí možnosti kompilátoru, které může aktivovat upozornění nekonzistenci při použití předkompilovaných hlaviček:  
  
|Možnost|Název|Pravidlo|  
|------------|----------|----------|  
|/D|Zadejte konstanty a makra|Musí být stejné mezi kompilace vytvořený předkompilovaných hlaviček a aktuální kompilace. Stav definované konstanty není zaškrtnuto, ale vést k neočekávaným výsledkům může dojít, pokud vaše soubory závisí na hodnotách změněné konstanty.|  
|/E nebo /EP|Kopírovat výstup předběžného zpracování na standardní výstup|Předkompilované hlavičky s parametrem/e nebo /EP nefungují.|  
|/FR nebo /FR|Generovat informace o prohlížeči zdroje společnosti Microsoft|Možnosti /Fr a /FR platná s možností /Yu musí také nejsou v platnosti předkompilovaných hlaviček v okamžiku vytvoření. Následné kompilace, které používají předkompilovaných hlaviček také generovat informace o prohlížeči zdroje. Informace o prohlížeči je umístěn v jednom .sbr souboru a odkazují další soubory v stejným způsobem jako CodeView informace. Nejde přepsat umístění informace o prohlížeči zdroje.|  
|/ GA /GD, /GE /Gw nebo /GW|Možnosti protokolu systému Windows|Musí být stejné mezi kompilace vytvořený předkompilovaných hlaviček a aktuální kompilace. Pokud tyto možnosti se liší, projeví se zpráva s upozorněním.|  
|/Zi|Generuje kompletní informace o ladění|Pokud tato možnost je v platnosti při vytváření předkompilovaných hlaviček, můžete použít následné kompilace, které používají předkompilaci tyto informace ladění. Pokud /Zi není platit při vytváření předkompilovaných hlaviček, následných kompilace používající předkompilaci a možnost /Zi aktivovat upozornění. Informace o ladění je umístěn v aktuální objekt souboru, a lokální symboly definované v předkompilovaných hlaviček nejsou k dispozici pro ladicí program.|  
  
> [!NOTE]
>  Použití předkompilovaných hlaviček prostředků je určena pro použití pouze ve zdrojových souborech C a C++.  
  
<a name="using-precompiled-headers-in-a-project"></a>  
  
## <a name="using-precompiled-headers-in-a-project"></a>Použití předkompilovaných hlaviček v projektu  
  
Předchozí části jsou uvedeny základní informace o předkompilovaných hlaviček: /Yc a /Yu, možnost /Fp a [hdrstop –](../../preprocessor/hdrstop.md) – Direktiva pragma. V této části je popsán způsob použití ruční možnosti předkompilovaných hlaviček v projektu; končí na příklad souboru pravidel a kód, který spravuje.  
  
Jiný způsob použití ruční možnosti předkompilovaných hlaviček v projektu prostudovali mezi soubory pravidel umístěný v adresáři MFC\SRC, který se vytvoří během instalace výchozí Visual c++. Tyto soubory pravidel trvat podobný postup jeden uvedené v této části, ale větší využívat Microsoft Program údržby nástroj () makra NMAKE a nabízí větší kontrolu nad procesu sestavení.  
  
<a name="pch-files-in-the-build-process"></a>  
  
## <a name="pch-files-in-the-build-process"></a>Soubory PCH v procesu sestavení  
  
Základu kódu projektu softwaru je obvykle obsažený ve více C nebo C++ zdrojové soubory, soubory objektů, knihovny a soubory hlaviček. Obvykle souboru pravidel koordinuje kombinaci těchto prvků do spustitelného souboru. Následující obrázek znázorňuje strukturu souboru pravidel, která používá předkompilovaný hlavičkový soubor. Názvy maker NMAKE a názvy souborů v tomto diagramu jsou konzistentní s těmi, která v příkladu kódu v nalezen [ukázkový soubor pravidel pro PCH](#sample-makefile-for-pch) a [ukázkový kód pro PCH](#example-code-for-pch).  
  
Na obrázku používá tři zařízení graficky znázornit tok procesu sestavení. S názvem obdélníky představují každý soubor nebo makro; tři makra představují jeden nebo více souborů. Podbarvené oblasti představují každá kompilaci nebo odkaz akce. Šipky zobrazují, které soubory a makra jsou sloučené při kompilaci nebo proces propojení.  
  
![Soubor pravidel, která používá předkompilovaný hlavičkový soubor](../../build/reference/media/vc30ow1.gif "struktura souboru pravidel, která používá soubor předkompilovaných hlaviček")  
##### <a name="structure-of-a-makefile-that-uses-a-precompiled-header-file"></a>Struktura souboru pravidel, která používá soubor předkompilovaných hlaviček  
  
Od v horní části diagramu, STABLEHDRS i AUTONOMNÍHO jsou makra NMAKE, ve které uvedete soubory není pravděpodobně potřebovat opětovnou kompilaci. Tyto soubory jsou kompilovaná příkaz řetězec  
  
`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`  
  
jenom v případě, že předkompilovaný hlavičkový soubor (STABLE.pch) neexistuje nebo pokud provedete změny k souborům uvedeným v dvě makra. V obou případech předkompilovaný hlavičkový soubor bude obsahovat kód pouze z uvedené v makro STABLEHDRS soubory. Zobrazí seznam posledního souboru, který má být předkompilovaných v AUTONOMNÍHO makro.  
  
Soubory hlaviček nebo zdrojové soubory C nebo C++, může být soubory seznamu tyto makra. (Do jednoho souboru PCH nelze použít s moduly C a C++.) Všimněte si, že můžete použít **hdrstop –** makro zastavit předkompilaci v určitém okamžiku v rámci tohoto souboru AUTONOMNÍHO. V tématu [hdrstop –](../../preprocessor/hdrstop.md) Další informace.  
  
Pokračováním dolů diagramu, APPLIB.obj představuje kód podporu použité v posledním aplikaci. Je vytvořený z APPLIB.cpp, soubory uvedené v makro UNSTABLEHDRS a předkompilovaných kód z předkompilovaných hlaviček.  
  
MYAPP.obj představuje poslední aplikaci. Je vytvořený z MYAPP.cpp, soubory uvedené v makro UNSTABLEHDRS a předkompilovaných kód z předkompilovaných hlaviček.  
  
Nakonec se spustitelný soubor (Moje aplikace. Soubor EXE) je vytvořen pomocí propojení souborů uvedených v OBJS makro (APPLIB.obj a MYAPP.obj).  
  
<a name="sample-makefile-for-pch"></a>  
  
## <a name="sample-makefile-for-pch"></a>Ukázkový soubor pravidel pro PCH  
  
Následující makefile používá makra a! POKUD! #ELSE! Řízení toku příkazovou strukturu ENDIF zjednodušit přizpůsobilo do projektu.  
  
```NMAKE  
# Makefile : Illustrates the effective use of precompiled  
#            headers in a project  
# Usage:     NMAKE option  
# option:    DEBUG=[0|1]  
#            (DEBUG not defined is equivalent to DEBUG=0)  
#  
OBJS = myapp.obj applib.obj  
# List all stable header files in the STABLEHDRS macro.  
STABLEHDRS = stable.h another.h  
# List the final header file to be precompiled here:  
BOUNDRY = stable.h  
# List header files under development here:  
UNSTABLEHDRS = unstable.h  
# List all compiler options common to both debug and final  
# versions of your code here:  
CLFLAGS = /c /W3  
# List all linker options common to both debug and final  
# versions of your code here:  
LINKFLAGS = /NOD /ONERROR:NOEXE  
!IF "$(DEBUG)" == "1"  
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi /f  
LINKFLAGS = $(LINKFLAGS) /COD  
LIBS      = slibce  
!ELSE  
CLFLAGS   = $(CLFLAGS) /Oselg /Gs  
LINKFLAGS = $(LINKFLAGS)  
LIBS      = slibce  
!ENDIF  
myapp.exe: $(OBJS)  
    link $(LINKFLAGS) @<<  
$(OBJS), myapp, NUL, $(LIBS), NUL;  
<<  
# Compile myapp  
myapp.obj  : myapp.cpp $(UNSTABLEHDRS)  stable.pch  
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    myapp.cpp  
# Compile applib  
applib.obj : applib.cpp $(UNSTABLEHDRS) stable.pch  
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    applib.cpp  
# Compile headers  
stable.pch : $(STABLEHDRS)  
    $(CPP) $(CLFLAGS) /Yc$(BOUNDRY)    applib.cpp myapp.cpp  
```  
  
Kromě zajištění dostatečného STABLEHDRS AUTONOMNÍHO a UNSTABLEHDRS makra vidět na obrázku "Struktura z souboru pravidel, používá předkompilované hlavičky souboru" v [soubory PCH v procesu sestavení](#pch-files-in-the-build-process), tento soubor pravidel poskytuje CLFLAGS makro a LINKFLAGS makro. K zobrazení seznamu kompilátoru a linkeru možnosti, které jsou zda sestavení ladění nebo finální verzi spustitelný soubor aplikace, musíte použít tyto makra. K dispozici je také KNIHOVNY makro kde seznamu knihovny vyžaduje projektu.  
  
Souboru pravidel se používá také! POKUD! #ELSE! ENDIF ke zjištění, zda je na příkazovém řádku NMAKE definovat symbol ladění:  
  
```NMAKE  
NMAKE DEBUG=[1|0]  
```  
  
Tato funkce umožňuje musíte použít stejné makefile během vývoje a pro poslední verze vašeho programu – použití DEBUG = 0 pro konečné verze. Odpovídají následujících příkazových řádků:  
  
```NMAKE  
NMAKE   
NMAKE DEBUG=0  
```  
  
Další informace o soubory pravidel najdete v tématu [NMAKE – odkaz](../../build/nmake-reference.md). Viz také [– možnosti kompilátoru](../../build/reference/compiler-options.md) a [možnosti Linkeru](../../build/reference/linker-options.md).  
  
<a name="example-code-for-pch"></a>  
  
## <a name="example-code-for-pch"></a>Ukázkový kód pro PCH  
  
Tyto zdrojové soubory, které se používají v souboru pravidel popsaných v [soubory PCH v procesu sestavení](#pch-files-in-the-build-process) a [ukázkový soubor pravidel pro PCH](#sample-makefile-for-pch). Všimněte si, že komentáře obsahují důležité informace.  
  
```cpp  
// ANOTHER.H : Contains the interface to code that is not  
//             likely to change.  
//  
#ifndef __ANOTHER_H  
#define __ANOTHER_H  
#include<iostream>  
void savemoretime( void );  
#endif // __ANOTHER_H  
```  
  
```cpp  
// STABLE.H : Contains the interface to code that is not likely  
//            to change. List code that is likely to change   
//            in the makefile's STABLEHDRS macro.  
//  
#ifndef __STABLE_H  
#define __STABLE_H  
#include<iostream>  
void savetime( void );  
#endif // __STABLE_H  
```  
  
```cpp  
// UNSTABLE.H : Contains the interface to code that is  
//              likely to change. As the code in a header  
//              file becomes stable, remove the header file  
//              from the makefile's UNSTABLEHDR macro and list  
//              it in the STABLEHDRS macro.  
//  
#ifndef __UNSTABLE_H  
#define __UNSTABLE_H  
#include<iostream.h>  
void notstable( void );  
#endif // __UNSTABLE_H  
```  
  
```cpp
// APPLIB.CPP : This file contains the code that implements  
//              the interface code declared in the header  
//              files STABLE.H, ANOTHER.H, and UNSTABLE.H.  
//  
#include"another.h"  
#include"stable.h"  
#include"unstable.h"  
// The following code represents code that is deemed stable and  
// not likely to change. The associated interface code is  
// precompiled. In this example, the header files STABLE.H and  
// ANOTHER.H are precompiled.  
void savetime( void )  
    { cout << "Why recompile stable code?\n"; }  
void savemoretime( void )  
    { cout << "Why, indeed?\n\n"; }  
// The following code represents code that is still under  
// development. The associated header file is not precompiled.  
void notstable( void )  
    { cout << "Unstable code requires"  
            << " frequent recompilation.\n"; 
    }  
```  
  
```cpp
// MYAPP.CPP : Sample application  
//             All precompiled code other than the file listed  
//             in the makefile's BOUNDRY macro (stable.h in  
//             this example) must be included before the file  
//             listed in the BOUNDRY macro. Unstable code must  
//             be included after the precompiled code.  
//  
#include"another.h"  
#include"stable.h"  
#include"unstable.h"  
int main( void )  
{  
    savetime();  
    savemoretime();  
    notstable();  
}  
```  
    
## <a name="see-also"></a>Viz také  
[Odkaz sestavení C/C++](../../build/reference/c-cpp-building-reference.md)   
[Možnosti kompilátoru](../../build/reference/compiler-options.md)