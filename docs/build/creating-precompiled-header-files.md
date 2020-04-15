---
title: Předkompilované soubory hlaviček
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 158301ec3caacced1663892071b17ef2b8f8e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328675"
---
# <a name="precompiled-header-files"></a>Předkompilované soubory hlaviček

Při vytváření nového projektu v sadě Visual Studio je do projektu přidán *předkompilovaný soubor záhlaví* s názvem *pch.h.* (V sadě Visual Studio 2017 a starší se soubor nazýval *stdafx.h*.) Účelem souboru je urychlit proces sestavení. Všechny stabilní hlavičkové soubory, například `<vector>`hlavičky standardní knihovny, například , by měly být zahrnuty zde. Předkompilovaná hlavička je zkompilována pouze v případě, že je změněna nebo všechny soubory, které obsahuje. Pokud provedete pouze změny ve zdrojovém kódu projektu, sestavení přeskočí kompilaci pro předkompilované záhlaví.

Možnosti kompilátoru pro předkompilované hlavičky jsou [/Y](reference/y-precompiled-headers.md). Na stránkách vlastností projektu jsou možnosti umístěny v části **Vlastnosti konfigurace > C/C++ > předkompilované záhlaví**. Můžete se rozhodnout nepoužívat předkompilovaná záhlaví a můžete zadat název souboru záhlaví a název a cestu výstupního souboru.

## <a name="custom-precompiled-code"></a>Vlastní předkompilovaný kód

U velkých projektů, které trvat značnou dobu sestavení, můžete zvážit vytvoření vlastní předkompilované soubory. Kompilátory Microsoft C a C++ poskytují možnosti pro předkompilaci libovolného kódu Jazyka C nebo C++, včetně vřádíkového kódu. Pomocí této funkce výkonu můžete zkompilovat stabilní tělo kódu, uložit zkompilovaný stav kódu do souboru a během následných kompilací kombinovat předkompilovaný kód s kódem, který je stále ve vývoji. Každá následující kompilace je rychlejší, protože stabilní kód nemusí být znovu zkompilován.

## <a name="when-to-precompile-source-code"></a>Kdy předkompilovat zdrojový kód

Předkompilovaný kód je užitečný během vývojového cyklu, aby se zkrátila doba kompilace, zejména pokud:

- Vždy používáte velké množství kódu, který se mění zřídka.

- Program se skládá z více modulů, z nichž všechny používají standardní sadu zahrnutí souborů a stejné možnosti kompilace. V tomto případě mohou být všechny soubory zahrnutí předkompilovány do jedné předkompilované hlavičky.

První kompilace – ta, která vytvoří předkompilovaný soubor záhlaví (PCH) – trvá o něco déle než následné kompilace. Následné kompilace můžete pokračovat rychleji zahrnutím předkompilovaného kódu.

Můžete předkompilovat programy Jazyka C i C++. V programování jazyka C++ je běžnou praxí oddělit informace o rozhraní třídy do souborů hlaviček. Tyto soubory hlaviček mohou být později zahrnuty v programech, které používají třídu. Předkompilací těchto záhlaví můžete zkrátit dobu, kterou program potřebuje ke kompilaci.

> [!NOTE]
> Přestože můžete použít pouze jeden předkompilovaný soubor záhlaví (.pch) na zdrojový soubor, můžete v projektu použít více souborů PCH.

## <a name="two-choices-for-precompiling-code"></a>Dvě možnosti pro předkompilaci kódu

Můžete předkompilovat libovolný kód Jazyka C nebo C++. nejste omezeni na předkompilaci pouze souborů hlaviček.

Předkompilace vyžaduje plánování, ale nabízí výrazně rychlejší kompilace, pokud předkompilujete zdrojový kód jiný než jednoduché soubory hlaviček.

Předkompilace kódu, pokud víte, že vaše zdrojové soubory používají běžné sady souborů hlaviček, ale nezahrnují je ve stejném pořadí, nebo pokud chcete zahrnout zdrojový kód do předkompilace.

Předkompilované možnosti záhlaví jsou [/Yc (Vytvořit předkompilovaný soubor hlaviček)](reference/yc-create-precompiled-header-file.md) a [/Yu (Použít předkompilovaný soubor záhlaví).](reference/yu-use-precompiled-header-file.md) Pomocí **parametru /Yc** vytvořte předkompilované záhlaví. Při použití s volitelným [hdrstop](../preprocessor/hdrstop.md) pragma **/ Yc** umožňuje předkompilovat jak soubory hlaviček, tak zdrojový kód. Vyberte **/Yu,** chcete-li použít existující předkompilované záhlaví v existující kompilaci. Můžete také použít **/Fp** s **/Yc** a **/Yu** možnosti poskytnout alternativní název pro předkompilované záhlaví.

Možnost kompilátoru referenční témata pro **/Yu** a **/Yc** diskutovat o tom, jak získat přístup k této funkci ve vývojovém prostředí.

## <a name="precompiled-header-consistency-rules"></a>Pravidla konzistence předkompilovaných hlaviček

Vzhledem k tomu, že soubory PCH obsahují informace o prostředí počítače a informace o adrese paměti o programu, měli byste použít pouze soubor PCH v počítači, kde byl vytvořen.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Pravidla konzistence pro použití předkompilovaných hlaviček podle souborů

Možnost kompilátoru [/Yu](reference/yu-use-precompiled-header-file.md) umožňuje určit, který soubor PCH má být používán.

Při použití souboru PCH kompilátor předpokládá stejné prostředí kompilace – takové, které používá konzistentní možnosti kompilátoru, pragmas a tak dále – které platilo při vytváření souboru PCH, pokud neurčíte jinak. Pokud kompilátor zjistí nekonzistenci, vydá upozornění a identifikuje nekonzistenci, kde je to možné. Tato upozornění nemusí nutně znamenat problém se souborem PCH; jednoduše vás varují před možnými konflikty. Požadavky na konzistenci souborů PCH jsou popsány v následujících částech.

### <a name="compiler-option-consistency"></a>Konzistence možnosti kompilátoru

Následující možnosti kompilátoru mohou při použití souboru PCH vyvolat upozornění na nekonzistenci:

- Makra vytvořená pomocí možnosti Preprocesor (/D) musí být stejná mezi kompilací, která vytvořila soubor PCH, a aktuální kompilací. Stav definovaných konstant není zaškrtnuto, ale může dojít k nepředvídatelným výsledkům, pokud se tyto změny změní.

- PCH soubory nefungují s /E a /EP možnosti.

- Soubory PCH musí být vytvořeny buď pomocí možnosti Generovat informace o procházení (/FR), nebo pomocí možnosti Vyloučit místní proměnné (/Fr) před tím, než mohou následující kompilace, které používají soubor PCH, tyto možnosti použít.

### <a name="c-70-compatible-z7"></a>Kompatibilní s C 7.0 (/Z7)

Pokud tato možnost platí při vytvoření souboru PCH, následné kompilace, které používají soubor PCH můžete použít informace o ladění.

Pokud c 7.0-Kompatibilní (/Z7) volba není v platnosti při vytvoření souboru PCH, následné kompilace, které používají soubor PCH a /Z7 aktivovat upozornění. Informace o ladění jsou umístěny v aktuálním souboru OBJ a místní symboly definované v souboru PCH nejsou k dispozici ladicímu programu.

### <a name="include-path-consistency"></a>Zahrnout konzistenci cesty

Soubor PCH neobsahuje informace o cestě zahrnutí, která byla v platnosti při jeho vytvoření. Při použití souboru PCH kompilátor vždy používá cestu zahrnutí zadanou v aktuální kompilaci.

### <a name="source-file-consistency"></a>Konzistence zdrojového souboru

Když zadáte možnost Použít předkompilovaný soubor záhlaví (/Yu), kompilátor ignoruje všechny direktivy preprocesoru (včetně pragmů), které se zobrazí ve zdrojovém kódu, který bude předkompilován. Kompilace určená těmito direktivami preprocesoru musí být stejná jako kompilace použitá pro možnost Vytvořit předkompilovaný soubor záhlaví (/Yc).

### <a name="pragma-consistency"></a>Konzistence Pragma

Pragmas zpracované při vytváření souboru PCH obvykle ovlivňují soubor, se kterým je soubor PCH následně použit. A `comment` `message` pragmas nemají vliv na zbytek kompilace.

Tyto pragmas ovlivnit pouze kód v souboru PCH; nemají vliv na kód, který následně používá soubor PCH:

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Tyto pragmas jsou zachovány jako součást předkompilované hlavičky a ovlivňují zbytek kompilace, která používá předkompilované záhlaví:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Pravidla konzistence pro /Yc a /Yu

Při použití předkompilované hlavičky vytvořené pomocí /Yc nebo /Yu kompilátor porovná aktuální prostředí kompilace s prostředím, které existovalo při vytváření souboru PCH. Nezapomeňte zadat prostředí konzistentní s předchozí (pomocí konzistentní možnosti kompilátoru, pragmas a tak dále) pro aktuální kompilaci. Pokud kompilátor zjistí nekonzistenci, vydá upozornění a identifikuje nekonzistenci, kde je to možné. Tato upozornění nemusí nutně znamenat problém se souborem PCH; jednoduše vás varují před možnými konflikty. V následujících částech jsou vysvětleny požadavky na konzistenci pro předkompilované hlavičky.

### <a name="compiler-option-consistency"></a>Konzistence možnosti kompilátoru

V této tabulce jsou uvedeny možnosti kompilátoru, které mohou při použití předkompilované hlavičky vyvolat upozornění na nekonzistenci:

|Možnost|Name (Název)|Pravidlo|
|------------|----------|----------|
|/d|Definování konstant a maker|Musí být stejný mezi kompilací, která vytvořila předkompilované záhlaví a aktuální kompilace. Stav definovaných konstant není zaškrtnuto, ale může dojít k nepředvídatelným výsledkům, pokud vaše soubory závisí na hodnotách změněných konstant.|
|/E nebo /EP|Kopírování výstupu preprocesoru do standardního výstupu|Předkompilované hlavičky nefungují s parametrem /E nebo /EP.|
|/Fr nebo /FR|Generovat informace o zdrojovém prohlížeči Microsoft|Pro /Fr a /FR možnosti platné s /Yu možnost, musí být také v platnosti při vytvoření předkompilované záhlaví. Následné kompilace, které používají předkompilované záhlaví také generovat informace zdrojového prohlížeče. Informace o prohlížeči jsou umístěny v jednom souboru .sbr a jsou odkazovány jinými soubory stejným způsobem jako informace CodeView. Umístění informací zdrojového prohlížeče nelze přepsat.|
|/GA, /GD, /GE, /Gw nebo /GW|Možnosti protokolu systému Windows|Musí být stejný mezi kompilací, která vytvořila předkompilované záhlaví a aktuální kompilace. Pokud se tyto možnosti liší, zobrazí se varovná zpráva.|
|/Zi|Generovat úplné informace o ladění|Pokud tato možnost platí při vytvoření předkompilované hlavičky, následné kompilace, které používají předkompilaci můžete použít, že ladění informace. Pokud /Zi není v platnosti při vytvoření předkompilované záhlaví, následné kompilace, které používají předkompilaci a /Zi možnost aktivovat upozornění. Informace o ladění jsou umístěny v aktuálním souboru objektu a místní symboly definované v předkompilované hlavičce nejsou k dispozici ladicímu programu.|

> [!NOTE]
> Předkompilované záhlaví zařízení je určena pouze pro použití ve zdrojových souborech C a C++.

## <a name="using-precompiled-headers-in-a-project"></a>Použití předkompilovaných hlaviček v projektu

Předchozí části představují přehled předkompilovaných záhlaví: /Yc a /Yu, /Fp možnost a [hdrstop](../preprocessor/hdrstop.md) pragma. Tato část popisuje metodu pro použití ručně předkompilované záhlaví možnosti v projektu; končí příklad makefile a kód, který spravuje.

Pro jiný přístup k použití ruční předkompilované záhlaví možnosti v projektu, prostudujte jeden z makefiles umístěných v adresáři Knihovny MFC\SRC, který je vytvořen během výchozího nastavení sady Visual Studio. Tyto makefiles mít podobný přístup k tomu, který je uveden v této části, ale větší využití Microsoft Program Maintenance Utility (NMAKE) makra a nabízejí větší kontrolu procesu sestavení.

## <a name="pch-files-in-the-build-process"></a>Soubory PCH v procesu sestavení

Základ kódu softwarového projektu je obvykle obsažen ve více zdrojových souborech C nebo C++, objektových souborech, knihovnách a souborech hlaviček. Makefile obvykle koordinuje kombinaci těchto prvků do spustitelného souboru. Následující obrázek znázorňuje strukturu makefile, který používá předkompilovaný soubor záhlaví. Názvy maker NMAKE a názvy souborů v tomto diagramu jsou konzistentní s názvy v ukázkovém kódu nalezeném v [ukázkovém souboru pro PCH](#sample-makefile-for-pch) a [ukázkový kód pro PCH](#example-code-for-pch).

Obrázek používá tři diagramová zařízení k zobrazení toku procesu sestavení. Pojmenované obdélníky představují každý soubor nebo makro; tři makra představují jeden nebo více souborů. Stínované oblasti představují každou akci kompilace nebo propojení. Šipky ukazují, které soubory a makra jsou kombinovány během kompilace nebo procesu propojování.

![Struktura makefile, který používá předkompilovaný soubor záhlaví](media/vc30ow1.gif "Struktura makefile, který používá předkompilovaný soubor záhlaví") <br/>
Struktura makefile, který používá předkompilovaný soubor záhlaví

Počínaje v horní části diagramu, oba STABLEHDRS a BOUNDRY jsou NMAKE makra, ve kterém seznam souborů není pravděpodobné, že bude potřebovat rekompilaci. Tyto soubory jsou kompilovány příkazový řetězec

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

pouze v případě, že předkompilovaný soubor hlaviček (STABLE.pch) neexistuje nebo pokud provedete změny souborů uvedených ve dvou makrech. V obou případech bude předkompilovaný soubor záhlaví obsahovat kód pouze ze souborů uvedených v makru STABLEHDRS. Seznam posledního souboru, který chcete předkompilovat, v makru BOUNDRY.

Soubory, které v těchto marech uvádíte, mohou být soubory hlaviček nebo zdrojové soubory Jazyka C nebo C++. (Jeden soubor PCH nelze použít s moduly C i C++.) Všimněte si, že můžete použít **makro hdrstop** zastavit předkompilaci v určitém okamžiku v souboru BOUNDRY. Další informace naleznete v [tématu hdrstop.](../preprocessor/hdrstop.md)

Pokračování dolů diagramu, APPLIB.obj představuje kód podpory používané v konečné aplikaci. Je vytvořen z APPLIB.cpp, soubory uvedené v makru UNSTABLEHDRS a předkompilovaný kód z předkompilované hlavičky.

MYAPP.obj představuje vaši konečnou přihlášku. Je vytvořen z MYAPP.cpp, soubory uvedené v makru UNSTABLEHDRS a předkompilovaný kód z předkompilované hlavičky.

Nakonec spustitelný soubor (MYAPP. EXE) je vytvořen propojením souborů uvedených v makru OBJS (APPLIB.obj a MYAPP.obj).

## <a name="sample-makefile-for-pch"></a>Ukázkový soubor pravidel pro PCH

Následující makefile používá makra a ! Pokud! Jiného! Endif tok řídicí struktury pro zjednodušení jeho přizpůsobení projektu.

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

Kromě makra STABLEHDRS, BOUNDRY a UNSTABLEHDRS znázorněných na obrázku "Struktura makefile, který používá předkompilovaný soubor záhlaví" v [souborech PCH v procesu sestavení](#pch-files-in-the-build-process), tento makefile poskytuje makro CLFLAGS a makro LINKFLAGS. Tato makra je nutné použít k zobrazení seznamu možností kompilátoru a propojovacího programu, které platí bez ohledu na to, zda vytváříte ladicí nebo konečnou verzi spustitelného souboru aplikace. K dispozici je také makro LIBS, kde zobrazíte seznam knihoven, které projekt vyžaduje.

Makefile také používá! Pokud! Jiného! ENDIF pro zjištění, zda definujete symbol LADĚNÍ na příkazovém řádku NMAKE:

```NMAKE
NMAKE DEBUG=[1|0]
```

Tato funkce umožňuje použít stejný makefile během vývoje a pro konečné verze programu – použijte DEBUG = 0 pro konečné verze. Následující příkazové řádky jsou rovnocenné:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Další informace o makefiles naleznete v tématu [NMAKE Reference](reference/nmake-reference.md). Viz také [možnosti kompilátoru MSVC](reference/compiler-options.md) a [Možnosti propojovacího nástroje MSVC](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Ukázkový kód pro PCH

Následující zdrojové soubory se používají v makefile popsané v [PCH soubory v procesu sestavení](#pch-files-in-the-build-process) a [ukázkový makefile pro PCH](#sample-makefile-for-pch). Všimněte si, že komentáře obsahují důležité informace.

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

[Odkaz sestavení C/C++](reference/c-cpp-building-reference.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
