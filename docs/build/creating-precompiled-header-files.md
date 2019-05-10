---
title: Předkompilované soubory hlaviček
ms.date: 05/06/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 1dc6ff9de94f98a4eef3d3827bec177f22672674
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220817"
---
# <a name="precompiled-header-files"></a>Předkompilované soubory hlaviček

Když vytvoříte nový projekt v sadě Visual Studio *předkompilovaného hlavičkového souboru* s názvem "soubor pch.h" je přidána do projektu. (V dřívějších verzích sady Visual Studio byla volána soubor "stdafx.h".) Účelem souboru je ke zrychlení procesu sestavení. Žádné stabilní hlavičkové soubory, například hlavičky standardní knihovny, jako `<vector>`, by měly být zahrnuty v tomto poli. Předkompilované hlavičky je zkompilován pouze v případě, že nebo všechny soubory, které obsahuje, jsou změněny. Pokud provedete změny pouze ve zdrojovém kódu projektu, sestavení se přeskočí kompilace pro předkompilované hlavičky. 

Možnosti kompilátoru pro předkompilované záhlaví jsou [/Y](reference/y-precompiled-headers.md). Na stránkách vlastností projektu možnosti jsou umístěné v části **vlastnosti konfigurace > C/C++ > předkompilované hlavičky**. Můžete používat předkompilovaných hlaviček, a můžete zadat hlavičce název a název a Cesta výstupního souboru. 

## <a name="custom-precompiled-code"></a>Vlastní předkompilovaný kód

Pro velké projekty, které trvat déle vytvářet můžete chtít zvážit vytvoření vlastní Předkompilované soubory. Kompilátory Microsoft C a C++ poskytují možnosti pro předkompilaci kódu jakékoli jazyka C nebo C++, včetně vložený kód. Pomocí této výkonné funkce, můžete zkompilovat stabilní části kódu, uložit zkompilovaný kód do souboru a, při následných kompilací kombinovat předkompilovaný kód s kódem, který je stále ve vývoji. Každé následné kompilace je rychlejší, protože není potřeba překompilovat stabilní kód.

## <a name="when-to-precompile-source-code"></a>Kdy předkompilovat zdrojový kód

Předkompilovaný kód se hodí při vývojový cyklus zkrátit čas, kompilace, zejména v případě:

- Vždy používejte velké části kódu, který mění jen zřídka.

- Aplikace se skládá z několika modulů, které používají standardní sadu vložených souborů a stejné možnosti kompilace. V takovém případě všechny soubory k zahrnutí může být možné předem zkompilovat do jednoho předkompilované hlavičky.

První kompilace – ten, který vytvoří soubor předkompilované hlavičky (PCH), trvá o něco déle, než následující kompilace. Následné kompilace můžete pokračovat rychlejší zahrnutím předkompilovaný kód.

Můžete předkompilovat programů jazyka C a C++. V jazyce C++ programování je běžnou praxí k oddělení informace o rozhraní třídy do záhlaví souborů. Tyto soubory záhlaví mohou být součástí později programy, které používají třídy. Předkompilace tato záhlaví, můžete snížit čas, který program pro kompilaci.

> [!NOTE]
> I když každý zdrojový soubor, můžete použít pouze jeden soubor předkompilované hlavičky (pch), můžete použít více soubory v projektu.

## <a name="two-choices-for-precompiling-code"></a>Dvě možnosti pro předkompilaci kódu

Můžete předkompilovat jakékoli C nebo C++ kódu; nejste omezeni předkompilace jenom hlavičkové soubory.

Předkompilace vyžaduje plánování, ale nabízí mnohem rychlejší kompilace, pokud předkompilovat zdrojový kód než jednoduché hlavičkové soubory.

Předkompilace kódu, když víte, že použít společné soubory hlaviček sady zdrojových souborů, ale nezahrne je ve stejném pořadí, nebo pokud chcete zahrnout do vaší předkompilace zdrojového kódu.

Možnosti předkompilovaných hlaviček jsou [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](reference/yc-create-precompiled-header-file.md) a [/Yu (Použít předkompilovaný hlavičkový soubor)](reference/yu-use-precompiled-header-file.md). Použití **/Yc** k vytvoření předkompilovaných hlaviček. Při použití s nepovinným [hdrstop](../preprocessor/hdrstop.md) – Direktiva pragma, **/Yc** umožňuje předkompilovat oba hlavičkové soubory a zdrojový kód. Vyberte **/Yu** používat existující předkompilované hlavičky v existující kompilace. Můžete také použít **/FP** s **/Yc** a **/Yu** možnosti poskytují alternativní název pro předkompilované hlavičky.

Referenční témata – možnost kompilátoru pro **/Yu** a **/Yc** popíšeme, jak získat přístup k této funkci ve vývojovém prostředí.

## <a name="precompiled-header-consistency-rules"></a>Pravidla konzistence předkompilovaných hlaviček

Soubory PCH obsahovat informace o prostředí počítače a paměti adresu informace o programu, byste měli používat jenom soubor PCH na počítači, kde se vytvořila.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Pravidla konzistence pro použití předkompilovaných hlaviček podle souborů

[/Yu](reference/yu-use-precompiled-header-file.md) – možnost kompilátoru umožňuje určit soubor PCH.

Při použití souborů PCH kompilátor předpokládá stejné prostředí kompilace – ten, který používá možnosti kompilátoru konzistentní vzhledem k aplikacím, direktivy pragma a tak dále, bylo to platit při vytvoření souboru PCH, pokud neurčíte jinak. Pokud kompilátor zjistí nekonzistence, vydá upozornění a identifikuje nekonzistencí, kde je to možné. Tato upozornění nemusí znamenat problém s souboru PCH; upozorňují jednoduše je možné je v konfliktu. V následujících částech jsou popsány na konzistenci pro soubory PCH.

### <a name="compiler-option-consistency"></a>Konzistence – možnost kompilátoru

Následující možnosti kompilátoru můžete aktivovat upozornění nekonzistence, při použití souboru PCH:

- Makra vytvořené pomocí preprocesoru (/ D) možnost musí být mezi kompilace, která vytvoří soubor PCH a aktuální kompilace. Stav definované konstanty není povolená, ale nepředvídatelné výsledky může dojít, pokud tyto změnit.

- Soubory PCH s možností /E a /EP nefungují.

- Soubory PCH musí být vytvořen pomocí obou generovat procházet informace (/ FR) možnost nebo vyloučit lokální proměnné (/ Fr) možnost předtím, než tyto možnosti lze použít následující kompilace, které používají soubor PCH.

### <a name="c-70-compatible-z7"></a>Kompatibilní s C 7.0 (/ Z7)

Pokud tato možnost je v platnosti, když se vytvoří soubor PCH, můžete použít následující kompilace, které používají soubor PCH ladicí informace.

Pokud kompatibilní s C 7.0 (/ Z7) možnost není ve skutečnosti když se vytvoří soubor PCH, následné kompilace, které používají soubor PCH a/Z7 aktivovat upozornění. Informace o ladění je umístěn v aktuálním souboru .obj, a lokální symboly definované v souboru PCH nejsou k dispozici v ladicím programu.

### <a name="include-path-consistency"></a>Zahrnout cestu konzistence

Soubor PCH neobsahuje informace o zahrnout cestu, která byla používána při vytvoření rovnou uložil. Při použití souborů PCH kompilátor vždy používá zadaná cesta zahrnutí v aktuální kompilaci.

### <a name="source-file-consistency"></a>Zdrojový soubor konzistence

Když zvolíte možnost Použít předkompilovaný hlavičkový soubor (/Yu), kompilátor ignoruje všechny direktivy preprocesoru (včetně direktivy pragma), které se zobrazí ve zdrojovém kódu, který bude předkompilována. Kompilace určené tyto direktivy preprocesoru musí být stejná jako použitý pro vytvoření souboru předkompilované hlavičky (/Yc) možnost kompilace.

### <a name="pragma-consistency"></a>Konzistence – Direktiva pragma

Direktivy pragma zpracovány při vytváření souboru PCH obvykle mít vliv na soubor, pomocí kterého se následně používá soubor PCH. `comment` a `message` direktivy pragma nemají vliv na zbytek kompilace.

Direktivy pragma vliv pouze na kód v souboru PCH; že nemají vliv na kód, který se následně použije soubor PCH:

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Direktivy pragma jsou zachovány jako součást předkompilovanou hlavičku a mít vliv na zbytek kompilaci, která používá předkompilované hlavičky:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Pravidla konzistence pro /Yc a /Yu

Při použití předkompilované hlavičky vytvořené pomocí /Yc a /Yu kompilátor porovná aktuální kompilace prostředí tak, aby ten, který existoval, když jste vytvořili soubor PCH. Nezapomeňte zadat prostředí konzistentní s předchozím histogramem (pomocí možnosti kompilátoru konzistentní vzhledem k aplikacím, direktivy pragma a tak dále) pro aktuální kompilaci. Pokud kompilátor zjistí nekonzistence, vydá upozornění a identifikuje nekonzistencí, kde je to možné. Tato upozornění není nutně znamenat problém s souboru PCH; upozorňují jednoduše je možné je v konfliktu. Následující části popisují požadavky na konzistence předkompilovaných hlaviček.

### <a name="compiler-option-consistency"></a>Konzistence – možnost kompilátoru

Tato tabulka shrnuje možnosti kompilátoru, které můžou aktivovat upozornění nekonzistence, při použití předkompilované hlavičky:

|Možnost|Name|Pravidlo|
|------------|----------|----------|
|/D|Definovat konstanty a makra|Musí být mezi kompilace, která vytvořili předkompilované hlavičky a aktuální kompilace. Stav definované konstanty není povolená, ale nepředvídatelné výsledky může dojít, pokud soubory závisí na hodnotách konstant změněné.|
|/E nebo /EP|Zkopírujte výstup předzpracování do standardního výstupu|Předkompilované hlavičky s možností /E nebo /EP nefungují.|
|/FR nebo /FR|Generovat informace o Microsoft Prohlížeč zdroje|/Fr a /FR možnosti platná s možností/YU musí také nebyla v platnosti v okamžiku vytvoření předkompilované hlavičky. Další soubory, které používají předkompilované hlavičky také generovat informace o prohlížeči zdroje. Informace o prohlížeči je umístěn v souboru .sbr jednoho a odkazují jiné soubory stejným způsobem jako informace CodeView. Nejde přepsat umístění prohlížeč zdroje informací.|
|/ GA, /GD, /GE, /Gw nebo /GW|Možnosti protokolu Windows|Musí být mezi kompilace, která vytvořili předkompilované hlavičky a aktuální kompilace. Pokud tyto možnosti se liší, výsledky se zpráva s upozorněním.|
|/Zi|Generovat kompletní informaci o ladění|Pokud tato možnost je v platnosti při vytváření předkompilované hlavičky, můžete použít následující soubory, které používají předkompilaci ladicí informace. Pokud /Zi není používána při vytváření předkompilované hlavičky, následné kompilace, které používají předkompilaci a možnost/zi aktivovat upozornění. Informace o ladění je umístěn v aktuálním objektu souboru a místní symboly definované v předkompilované hlavičce nejsou k dispozici v ladicím programu.|

> [!NOTE]
>  Předkompilované hlavičky zařízení je určena pro použití pouze ve zdrojových souborech jazyka C a C++.

## <a name="using-precompiled-headers-in-a-project"></a>Použití předkompilovaných hlaviček v projektu

Předchozí části jsou uvedeny základní informace o předkompilované hlavičky: /Yc a /Yu, možnost/fp a [hdrstop](../preprocessor/hdrstop.md) direktivy pragma. Tato část popisuje způsob pro použití ruční možnosti předkompilovaných hlaviček v projektu. končí příklad souboru pravidel a kód, který spravuje.

Pro další postup pro použití ruční možnosti předkompilovaných hlaviček v projektu studovat mezi soubory pravidel v adresáři MFC\SRC, který se vytvoří během instalace výchozí sady Visual Studio. Tyto soubory pravidel trvat podobný přístup je uvedené v této části, ale větší využití maker Microsoft Program údržby Utility (NMAKE) a nabízí větší kontrolu nad procesu sestavení.

## <a name="pch-files-in-the-build-process"></a>Soubory PCH v procesu sestavení

Kódové základny softwarového projektu je obvykle součástí více C nebo C++ zdrojové soubory, soubory objektů, knihovny a soubory hlaviček. Soubor pravidel obvykle koordinuje kombinaci těchto prvků do spustitelného souboru. Následující obrázek znázorňuje strukturu souboru pravidel, která používá soubor předkompilované hlavičky. Názvy maker NMAKE a názvy souborů v tomto diagramu jsou konzistentní s těmi v příkladu kódu v [ukázkový soubor pravidel pro PCH](#sample-makefile-for-pch) a [ukázkový kód pro PCH](#example-code-for-pch).

Na obrázku používá tři graficky zařízení kvůli znázornění toku procesu sestavení. S názvem obdélníky představují všechny soubory nebo makra. tři makra představují jeden nebo více souborů. Vystínovanou oblasti představují všechny kompilace nebo odkaz akce. Šipky zobrazují, které soubory a makra jsou zkombinované během kompilace nebo proces propojení.

![Struktura souboru pravidel, která používá soubor předkompilované hlavičky](media/vc30ow1.gif "strukturu souboru pravidel, která používá soubor předkompilované hlavičky") <br/>
Struktura souboru pravidel, která používá soubor předkompilované hlavičky

Od horní části diagramu STABLEHDRS a AUTONOMNÍHO jsou makra NMAKE, ve kterých je seznam souborů není pravděpodobně potřebovat opětovnou kompilaci. Tyto soubory jsou kompilovány pomocí řetězec příkazu

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

jenom v případě, že soubor předkompilované hlavičky (STABLE.pch) neexistuje nebo pokud provedete změny souborů uvedených v dvě makra. V obou případech bude obsahovat soubor předkompilované hlavičky kódu pouze z uvedené v makru STABLEHDRS soubory. Vypsat poslední soubor, který chcete, aby předkompilované v makru AUTONOMNÍHO.

Soubory, můžete seznam v těchto maker mohou být soubory hlaviček nebo zdrojové soubory jazyka C nebo C++. (Jeden soubor PCH nelze použít s moduly lineární C a C++.) Všimněte si, že můžete použít **hdrstop** – makro předkompilace v určitém okamžiku v souboru AUTONOMNÍHO zastavit. Zobrazit [hdrstop](../preprocessor/hdrstop.md) Další informace.

Pokračování dolů diagramu, APPLIB.obj představuje kód podpory, který používá v konečné aplikace. Je vytvořený z APPLIB.cpp, soubory uvedené v makru UNSTABLEHDRS a předkompilovaný kód z předkompilované hlavičky.

MYAPP.obj představuje poslední aplikace. Je vytvořený z MYAPP.cpp, soubory uvedené v makru UNSTABLEHDRS a předkompilovaný kód z předkompilované hlavičky.

A konečně spustitelný soubor (MYAPP. Propojování souborů uvedených v makru OBJS (APPLIB.obj a MYAPP.obj) vytvoří (EXE).

## <a name="sample-makefile-for-pch"></a>Ukázkový soubor pravidel pro PCH

Následující soubor pravidel používá makra a! POKUD! #ELSE! ENDIF řízení toku příkazovou strukturu pro zjednodušení adaptaci do projektu.

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

Kromě STABLEHDRS AUTONOMNÍHO a UNSTABLEHDRS makra je znázorněno na obrázku "Struktura z souboru pravidel, používá předkompilovaný soubor hlaviček" [soubory PCH v procesu sestavení](#pch-files-in-the-build-process), poskytuje tento soubor pravidel – makro CLFLAGS a LINKFLAGS makra. Tato makra je nutné použít k zobrazení seznamu kompilátoru a možnosti linkeru, které se vztahují, zda sestavení ladění nebo konečné verze spustitelného souboru aplikace. K dispozici je také – makro LIBS kde seznamu knihoven váš projekt vyžaduje.

Souboru pravidel se používá také! POKUD! #ELSE! ENDIF ke zjištění, zda můžete definovat symbol ladění NMAKE příkazového řádku:

```NMAKE
NMAKE DEBUG=[1|0]
```

Tato funkce umožňuje můžete použít stejný soubor pravidel během vývoje a finální verze programu – použití DEBUG = 0 pro konečné verze. Příkazovém řádku následující příkazy jsou ekvivalentní:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Další informace o soubory pravidel najdete v tématu [NMake – odkaz](reference/nmake-reference.md). Viz také [– možnosti kompilátoru MSVC](reference/compiler-options.md) a [možnosti Linkeru MSVC](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Ukázkový kód pro PCH

Následující zdrojové soubory se používají v souboru pravidel popsaných v [soubory PCH v procesu sestavení](#pch-files-in-the-build-process) a [ukázkový soubor pravidel pro PCH](#sample-makefile-for-pch). Všimněte si, že komentáře obsahují důležité informace.

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

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](reference/c-cpp-building-reference.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
