---
title: Předkompilované soubory hlaviček
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 6333e105a20612d6cbdf8d4b4d4abf47286c4e9b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078587"
---
# <a name="precompiled-header-files"></a>Předkompilované soubory hlaviček

Při vytváření nového projektu v aplikaci Visual Studio je do projektu přidán *předkompilovaný hlavičkový soubor* s názvem *PCH. h* . (V aplikaci Visual Studio 2017 a starší se soubor nazýval *stdafx. h*.) Účelem souboru je urychlení procesu sestavení. Zde by měly být zahrnuty všechny stabilní hlavičkové soubory, například hlavičky standardní knihovny, například `<vector>`. Předkompilovaná hlavička je kompilována pouze v případě, že je upravena nebo všechny soubory, které obsahují. Pokud provedete pouze změny ve zdrojovém kódu projektu, sestavení bude přeskočit kompilaci pro předkompilovanou hlavičku.

Možnosti kompilátoru pro předkompilované hlavičky jsou [/y](reference/y-precompiled-headers.md). Na stránkách vlastností projektu jsou možnosti umístěny v části **Vlastnosti konfigurace > předkompilovaných hlavičekC++ C/>** . Můžete zvolit, že nebudete používat předkompilované hlavičky, a můžete zadat název souboru hlaviček a cestu k výstupnímu souboru.

## <a name="custom-precompiled-code"></a>Vlastní předkompilovaný kód

U rozsáhlých projektů, které se při sestavování významně dobírají, je vhodné zvážit vytváření vlastních předkompilovaných souborů. Microsoft C a C++ kompilátory poskytují možnosti pro předkompilování kódu C nebo C++ kód, včetně vloženého kódu. Pomocí této funkce výkonu můžete kompilovat stabilní tělo kódu, ukládat zkompilovaný stav kódu v souboru a během následných kompilací kombinovat předkompilovaný kód s kódem, který je stále ve vývoji. Každá následná kompilace je rychlejší, protože stabilní kód není nutné znovu kompilovat.

## <a name="when-to-precompile-source-code"></a>Kdy předkompilovat zdrojový kód

Předkompilovaný kód je užitečný během vývoje, aby se zkrátila doba kompilace, obzvláště pokud:

- Vždy používáte velký text kódu, který se mění zřídka.

- Váš program sestává z více modulů, z nichž všechny používají standardní sadu vložených souborů a stejné možnosti kompilace. V takovém případě mohou být všechny vložené soubory předkompilovány do jedné předkompilované hlavičky.

První kompilace – ta, která vytvoří soubor předkompilované hlavičky (PCH), trvá několik bitů delší než následná kompilace. Další kompilace mohou rychleji pokračovat zahrnutím předkompilovaného kódu.

Můžete předem kompilovat C i C++ programy. V C++ programování je běžný postup, jak oddělit informace o rozhraní třídy do hlavičkových souborů. Tyto hlavičkové soubory mohou být později zahrnuty v aplikacích, které používají třídu. Po předkompilování těchto hlaviček můžete zkrátit dobu potřebnou k zkompilování programu.

> [!NOTE]
> I když můžete použít pouze jeden soubor předkompilované hlavičky (. pch) na zdrojový soubor, můžete v projektu použít více souborů. pch.

## <a name="two-choices-for-precompiling-code"></a>Dvě možnosti pro předkompilaci kódu

Můžete předkompilovat libovolný kód jazyka C C++ nebo. Nejste omezeni na předkompilování pouze hlavičkových souborů.

Předkompilace vyžaduje plánování, ale nabízí výrazně rychlejší kompilace, Pokud předkompilujete zdrojový kód jiný než jednoduché hlavičkové soubory.

Předkompilovat kód Pokud víte, že zdrojové soubory používají společné sady hlavičkových souborů, ale nezahrne je do stejného pořadí, nebo pokud chcete do předkompilace zahrnout zdrojový kód.

Možnosti předkompilovaných hlaviček jsou [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](reference/yc-create-precompiled-header-file.md) a [/Yu (použít předkompilovaný hlavičkový soubor)](reference/yu-use-precompiled-header-file.md). Pomocí **/YC** vytvořit předkompilovanou hlavičku. Při použití s volitelnou direktivou pragma [hdrstop](../preprocessor/hdrstop.md) vám **/YC** umožňuje předem kompilovat soubory hlaviček a zdrojový kód. Vyberte **/Yu** , chcete-li použít existující předkompilovanou hlavičku v existující kompilaci. Můžete také použít **/FP** s možnostmi **/YC** a **/Yu** k zadání alternativního názvu pro předkompilovanou hlavičku.

Referenční témata k možnostem kompilátoru pro **/Yu** a **/YC** projednávají, jak přistupovat k této funkci ve vývojovém prostředí.

## <a name="precompiled-header-consistency-rules"></a>Pravidla konzistence předkompilovaných hlaviček

Vzhledem k tomu, že soubory PCH obsahují informace o prostředí počítače a také informace o paměti k programu, měli byste použít pouze soubor PCH v počítači, kde byl vytvořen.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Pravidla konzistence pro použití předkompilovaných hlaviček podle souborů

Možnost kompilátoru [/Yu](reference/yu-use-precompiled-header-file.md) umožňuje určit, který soubor PCH se má použít.

Použijete-li soubor PCH, kompilátor předpokládá stejné prostředí kompilace – jeden, který používá konzistentní možnosti kompilátoru, direktivy pragma a tak dále, které byly použity při vytváření souboru PCH, pokud neurčíte jinak. Pokud kompilátor zjistí nekonzistenci, vydá upozornění a určí nekonzistenci tam, kde je to možné. Taková upozornění nemusí nutně značit problém se souborem PCH; jednoduše upozorňují na možné konflikty. Požadavky na konzistenci pro soubory PCH jsou popsány v následujících částech.

### <a name="compiler-option-consistency"></a>Konzistence možností kompilátoru

Následující možnosti kompilátoru mohou při použití souboru PCH aktivovat upozornění na nekonzistenci:

- Makra vytvořená pomocí možnosti preprocesoru (/D) musí být stejná mezi kompilací, která vytvořila soubor PCH a aktuální kompilací. Stav definovaných konstant není zaškrtnuto, ale pokud se tato změna projeví, může dojít k nepředvídatelným výsledkům.

- Soubory PCH nefungují s možnostmi/E a/EP.

- Soubory PCH je třeba vytvořit pomocí možnosti generovat informace o procházení (/FR) nebo vyloučit místní proměnné (/FR) předtím, než budou následující kompilace, které používají soubor PCH, moci tyto možnosti použít.

### <a name="c-70-compatible-z7"></a>Kompatibilní s C 7,0 (/Z7)

Pokud je tato možnost platná při vytvoření souboru PCH, další kompilace, které používají soubor PCH, mohou použít ladicí informace.

Pokud možnost kompatibilní s C 7,0 (/Z7) není v platnosti, když je vytvořen soubor PCH, další kompilace, které používají soubor PCH a/Z7, aktivuje upozornění. Ladicí informace jsou umístěny v aktuálním souboru. obj a místní symboly definované v souboru PCH nejsou k dispozici ladicímu programu.

### <a name="include-path-consistency"></a>Zahrnout konzistenci cest

Soubor PCH neobsahuje informace o cestě include, která byla při vytváření platná. Použijete-li soubor PCH, kompilátor vždy použije cestu include určenou v aktuální kompilaci.

### <a name="source-file-consistency"></a>Konzistence zdrojového souboru

Když zadáte možnost použít předkompilovaný hlavičkový soubor (/Yu), kompilátor ignoruje všechny direktivy preprocesoru (včetně direktiv pragma), které se zobrazí ve zdrojovém kódu, který bude předkompilován. Kompilace určená jako tyto direktivy preprocesoru musí být stejná jako kompilace použitá pro možnost vytvořit soubor předkompilované hlavičky (/Yc).

### <a name="pragma-consistency"></a>Pragma – konzistence

Direktivy pragma zpracované během vytváření souboru PCH obvykle ovlivňují soubor, se kterým se následně používá soubor PCH. Direktivy pragma `comment` a `message` neovlivňují zbývající část kompilace.

Tyto direktivy pragma ovlivňují pouze kód v rámci souboru PCH; neovlivňují kód, který následně používá soubor PCH:

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Tyto direktivy pragma se uchovávají jako součást předkompilované hlavičky a ovlivňují zbytek kompilace, která používá předkompilovanou hlavičku:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Pravidla konzistence pro /Yc a /Yu

Použijete-li předkompilovanou hlavičku vytvořenou pomocí/YC nebo/Yu, kompilátor porovná aktuální prostředí kompilace se souborem, který existoval při vytvoření souboru PCH. Nezapomeňte zadat prostředí konzistentní s předchozí (s použitím konzistentních parametrů kompilátoru, direktiv pragma a tak dále) pro aktuální kompilaci. Pokud kompilátor zjistí nekonzistenci, vydá upozornění a určí nekonzistenci tam, kde je to možné. Taková upozornění nemusí nutně označovat problém se souborem PCH; jednoduše upozorňují na možné konflikty. V následujících částech jsou vysvětlené požadavky na konzistenci pro předkompilované hlavičky.

### <a name="compiler-option-consistency"></a>Konzistence možností kompilátoru

Tato tabulka uvádí možnosti kompilátoru, které mohou při použití předkompilované hlavičky aktivovat upozornění na nekonzistenci:

|Možnost|Název|Pravidlo|
|------------|----------|----------|
|/D|Definovat konstanty a makra|Musí být stejné mezi kompilací, která vytvořila předkompilovanou hlavičku a aktuální kompilaci. Stav definovaných konstant není zaškrtnuto, ale může dojít k nepředvídatelným výsledkům, pokud jsou soubory závislé na hodnotách změněných konstant.|
|/E nebo/EP|Kopírovat výstup preprocesoru do standardního výstupu|Předkompilované hlavičky nefungují s možností/E nebo/EP.|
|/FR nebo/FR|Generování informací o prohlížeči zdrojového kódu Microsoftu|Aby byly možnosti/fr a/FR platné s možností/Yu, musí být také v platnosti, když byla vytvořena Předkompilovaná hlavička. Další kompilace, které používají předkompilovanou hlavičku, generují také informace o prohlížeči zdrojového kódu. Informace o prohlížeči jsou umístěny v jednom souboru. sbr a jsou odkazovány jinými soubory stejným způsobem jako informace CodeView. Umístění informací o zdrojovém prohlížeči nelze přepsat.|
|/GA,/GD,/GE,/GW nebo/GW|Možnosti protokolu Windows|Musí být stejné mezi kompilací, která vytvořila předkompilovanou hlavičku a aktuální kompilaci. Pokud se tyto možnosti liší, zobrazí se zpráva s upozorněním.|
|/Zi|Generování kompletních ladicích informací|Pokud je tato možnost platná, když je vytvořena Předkompilovaná hlavička, mohou další kompilace, které používají předkompilování, používat tyto informace o ladění. Pokud/ZI není v platnosti, když je vytvořena Předkompilovaná hlavička, další kompilace, které používají předkompilování a možnost/Zi, aktivují upozornění. Ladicí informace jsou umístěny v aktuálním souboru objektu a místní symboly definované v předkompilované hlavičce nejsou k dispozici ladicímu programu.|

> [!NOTE]
>  Zařízení předkompilovaných hlaviček je určeno pro použití pouze v jazyce C C++ a ve zdrojových souborech.

## <a name="using-precompiled-headers-in-a-project"></a>Použití předkompilovaných hlaviček v projektu

Předchozí části obsahují přehled předkompilovaných hlaviček:/Yc a/Yu, možnost/FP a direktivu pragma [hdrstop](../preprocessor/hdrstop.md) . Tato část popisuje metodu pro použití ručních předkompilovaných možností hlaviček v projektu. končí s příkladem souboru pravidel a kódu, který spravuje.

Pro další přístup k použití možností ručního předkompilovaných hlaviček v projektu, prostudujte jeden ze souborů pravidel umístěných v adresáři MFC\SRC, který je vytvořen při výchozím nastavení sady Visual Studio. Tyto soubory pravidel přebírají podobný přístup k těm, které jsou uvedené v této části, ale mají větší použití maker nástroje pro údržbu programu společnosti Microsoft (NMAKE) a nabízejí lepší kontrolu nad procesem sestavení.

## <a name="pch-files-in-the-build-process"></a>Soubory PCH v procesu sestavení

Základ kódu softwarového projektu je obvykle obsažen ve více jazycích C nebo C++ zdrojové soubory, soubory objektů, knihovny a soubory hlaviček. Soubor pravidel obvykle koordinuje kombinaci těchto prvků do spustitelného souboru. Následující obrázek ukazuje strukturu souboru pravidel, která používá soubor předkompilované hlavičky. Názvy maker NMAKE a názvy souborů v tomto diagramu jsou konzistentní s hodnotami v ukázkovém kódu, který najdete v [ukázkovém souboru pravidel pro PCH](#sample-makefile-for-pch) a [ukázkovém kódu pro PCH](#example-code-for-pch).

Obrázek používá tři zařízení diagramatické k zobrazení toku procesu sestavení. Pojmenované obdélníky znázorňují jednotlivé soubory nebo makra; tři makra reprezentují jeden nebo více souborů. Šedivé oblasti reprezentují každou akci kompilace nebo propojení. Šipky ukazují, které soubory a makra jsou kombinovány během kompilace nebo propojování procesů.

![Struktura souboru pravidel, který používá předkompilovaný hlavičkový soubor](media/vc30ow1.gif "Struktura souboru pravidel, který používá předkompilovaný hlavičkový soubor") <br/>
Struktura souboru pravidel, který používá předkompilovaný hlavičkový soubor

Počínaje horním okrajem diagramu jsou STABLEHDRS i BOUNDRY makra NMAKE, ve kterých vypíšete soubory, které pravděpodobně nepotřebují opětovnou kompilaci. Tyto soubory jsou kompilovány pomocí řetězce příkazu

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

pouze v případě, že soubor předkompilované hlavičky (stabilní. pch) neexistuje nebo pokud provedete změny v souborech uvedených v těchto dvou makrech. V obou případech bude předkompilovaný hlavičkový soubor obsahovat pouze kód ze souborů uvedených v makru STABLEHDRS. Vypíše poslední soubor, který chcete předkompilovaný v makru BOUNDRY.

Soubory, které jsou uvedeny v těchto makrech, mohou být hlavičkové soubory C++ nebo soubory C nebo zdrojové soubory. (Jeden soubor PCH nelze použít s C i C++ moduly.) Všimněte si, že můžete použít makro **hdrstop** k zastavení předkompilace v určitém bodě v souboru BOUNDRY. Další informace najdete v tématu [hdrstop](../preprocessor/hdrstop.md) .

Po pokračování diagramu APPLIB. obj představuje kód podpory použitý v konečné aplikaci. Je vytvořen z APPLIB. cpp, souborů uvedených v makru UNSTABLEHDRS a předkompilovaný kód z předkompilované hlavičky.

MYAPP. obj představuje vaši konečnou aplikaci. Vytvoří se z aplikace MYAPP. cpp, ze souborů uvedených v makru UNSTABLEHDRS a předkompilovaný kód z předkompilované hlavičky.

Nakonec spustitelný soubor (MYAPP. EXE) je vytvořen propojením souborů uvedených v makru OBJS (APPLIB. obj a MYAPP. obj).

## <a name="sample-makefile-for-pch"></a>Ukázkový soubor pravidel pro PCH

Následující soubor pravidel používá makra a! Pokud,! JINAK! ENDIF – struktura příkazů pro řízení toku pro zjednodušení přizpůsobení projektu.

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
LINKFLAGS = /nologo
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi
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

Kromě maker STABLEHDRS, BOUNDRY a UNSTABLEHDRS zobrazených na obrázku "struktura souboru pravidel, která používá soubor předkompilované hlavičky" v [souborech PCH v procesu sestavení](#pch-files-in-the-build-process), poskytuje tento soubor pravidel makro CLFLAGS a makro LINKFLAGS. Tato makra je nutné použít k vypsání možností kompilátoru a linkeru, které se použijí, pokud vytváříte ladicí nebo finální verzi spustitelného souboru aplikace. K dispozici je také makro knihovny, kde můžete zobrazit seznam knihoven, které váš projekt vyžaduje.

Soubor pravidel také používá! Pokud,! JINAK! ENDIF k detekci, zda definujete symbol ladění na příkazovém řádku NMAKE:

```NMAKE
NMAKE DEBUG=[1|0]
```

Tato funkce umožňuje použít stejný soubor pravidel během vývoje a pro finální verze programu – pro finální verze použijte DEBUG = 0. Následující příkazové řádky jsou ekvivalentní:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Další informace o souborových souborů naleznete v tématu [Referenční příručka NMAKE](reference/nmake-reference.md). Viz také [Možnosti kompilátoru MSVC](reference/compiler-options.md) a [Možnosti linkeru MSVC](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Ukázkový kód pro PCH

Následující zdrojové soubory se používají v souboru pravidel popsaným v [souborech PCH v procesu sestavení](#pch-files-in-the-build-process) a [ukázkovém souboru pravidel pro PCH](#sample-makefile-for-pch). Všimněte si, že komentáře obsahují důležité informace.

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
#include<iostream>
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
using namespace std;
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

[Referenční zdroje k sestavení programu v jazyce C/C++](reference/c-cpp-building-reference.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
