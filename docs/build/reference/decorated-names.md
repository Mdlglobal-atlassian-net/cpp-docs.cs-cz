---
title: Dekorované názvy
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: f6d81029d20d9aaca96ff184f48e94a9ce35d56e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320506"
---
# <a name="decorated-names"></a>Dekorované názvy

Funkce, data a objekty v programech C a C++ jsou interně reprezentovány jejich dekorované názvy. *Upravený název* je kódovaný řetězec vytvořený kompilátorem během kompilace objektu, dat nebo definice funkce. Zaznamenává konvence volání, typy, parametry funkce a další informace spolu s názvem. Tento název dekorace, označované také jako *název mangling*, pomáhá propojovací program najít správné funkce a objekty při propojování spustitelný soubor.

Dekorované konvence pojmenování se změnily v různých verzích sady Visual Studio a může se také lišit v různých cílových architekturách. Chcete-li správně propojit se zdrojovými soubory vytvořenými pomocí sady Visual Studio, c a c++ knihovny a knihovny by měly být kompilovány pomocí stejné sady nástrojů kompilátoru, příznaky a cílovou architekturu.

> [!NOTE]
> Knihovny vytvořené v sadě Visual Studio 2015 můžou spotřebovávat aplikace vytvořené pomocí Sady Visual Studio 2017 nebo Visual Studia 2019.

## <a name="using-decorated-names"></a><a name="Using"></a>Použití dekorovaných názvů

Za normálních okolností není třeba znát upravený název psát kód, který kompiluje a odkazy úspěšně. Dekorované názvy jsou podrobnosti implementace vnitřní kompilátoru a propojovacího systému. Nástroje obvykle zpracovat název v jeho nevyzdobené podobě. Upravený název je však někdy vyžadován, když zadáte název funkce propropojovacího systému a další nástroje. Chcete-li například porovnat přetížené funkce jazyka C++, členy oborů názvů, konstruktory tříd, destruktory a speciální členské funkce, musíte zadat upravený název. Podrobnosti o příznaky možnosti a další situace, které vyžadují dekorované názvy, naleznete v dokumentaci k nástrojům a možnostem, které používáte.

Pokud změníte název funkce, třídu, konvence volání, návratový typ nebo libovolný parametr, změní se také upravený název. V takovém případě musíte získat nový upravený název a použít jej všude, kde je zadán dekorovaný název.

Název dekorace je také důležité při propojení s kódem napsaný v jiných programovacích jazycích nebo pomocí jiných kompilátorů. Různé kompilátory používají různé konvence dekorace názvu. Pokud váš spustitelný soubor odkazuje na kód napsaný v jiném jazyce, je třeba věnovat zvláštní pozornost vyváženému a importovanému jménu a konvencím volání. Kód jazyka sestavení musí používat msvc dekorované názvy a konvence volání pro propojení se zdrojovým kódem napsaným pomocí MSVC.

## <a name="format-of-a-c-decorated-name"></a><a name="Format"></a>Formát dekorovaného názvu c++

Upravený název funkce jazyka C++ obsahuje následující informace:

- Název funkce.

- Třída, která je členem funkce, pokud je členská funkce. To může zahrnovat třídu, která obklopuje třídu, která obsahuje funkci a tak dále.

- Obor názvů, do který funkce patří, pokud je součástí oboru názvů.

- Typy parametrů funkce.

- Konvence volání.

- Návratový typ funkce.

Názvy funkcí a tříd jsou kódovány v dekorovaném názvu. Zbytek upravený název je kód, který má vnitřní význam pouze pro kompilátor a propojovací program. Následují příklady neupravených a dekorovaných názvů c++.

|Upravený název|Upravený název|
|----------------------|--------------------|
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|

## <a name="format-of-a-c-decorated-name"></a><a name="FormatC"></a>Formát c dekorovaného názvu

Forma dekorace pro funkci C závisí na konvence volání použité v jeho prohlášení, jak je znázorněno v následující tabulce. Toto je také formát dekorace, který se používá `extern "C"` při c++ kód je deklarován mít propojení. Výchozí konvence volání `__cdecl`je . Všimněte si, že v 64bitovém prostředí nejsou funkce dekorovány.

|Konvenci|Dekorace|
|------------------------|----------------|
|`__cdecl`|Úvodní podtržítko (**_**)|
|`__stdcall`|Úvodní podtržítko (**_**)**\@** a koncové za znaménko ( ) následované počtem bajtů v seznamu parametrů v desítkové mase|
|`__fastcall`|Proklad a koncové**\@** na znaménka ( ) následované desítkovým číslem představujícím počet bajtů v seznamu parametrů|
|`__vectorcall`|Dva koncové na**\@** znaménka ( ) následované desetinným počtem bajtů v seznamu parametrů|

## <a name="viewing-decorated-names"></a><a name="Viewing"></a>Zobrazení dekorovaných jmen

Po kompilaci zdrojového souboru, který obsahuje data, objekt nebo definici funkce nebo prototyp, můžete získat dekorovaný tvar názvu symbolu. Chcete-li prozkoumat dekorované názvy v programu, můžete použít jednu z následujících metod:

#### <a name="to-use-a-listing-to-view-decorated-names"></a>Použití výpisu k zobrazení dekorovaných názvů

1. Vygenerujte výpis kompilací zdrojového souboru, který obsahuje definici dat, objektu nebo funkce nebo prototyp u [možnosti kompilátoru Typu souboru výpisu](fa-fa-listing-file.md) nastavenou na sestavení se zdrojovým kódem (**/FA**).

   Zadejte `cl /c /FAs example.cpp` například na příkazovém řádku vývojáře a vygenerujte soubor výpisu, example.asm.

2. Ve výsledném souboru výpisu najděte řádek, který začíná na PUBLIC a zakončuje středník následovaný upravenými daty nebo názvem funkce. Symbol mezi PUBLIC a středníkem je upravený název.

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>Použití funkce DUMPBIN k zobrazení dekorovaných názvů

1. Exportované symboly zobrazíte v souboru OBJ `dumpbin /symbols` `objfile` nebo LIB, zadejte na příkazovém řádku vývojáře.

2. Chcete-li najít zdobený tvar symbolu, vyhledejte upravený název v závorce. Upravený název je na stejném řádku, za znakem kanálu (&#124;) a před upraveným názvem.

## <a name="viewing-undecorated-names"></a><a name="Undecorated"></a>Zobrazení nevyzdobených názvů

Pomocí programu undname.exe můžete převést upravený název na neupravený formulář. Tento příklad ukazuje, jak to funguje:

```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation. All rights reserved.

Undecoration of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## <a name="see-also"></a>Viz také

[Další nástroje pro sestavení msvc](c-cpp-build-tools.md)<br/>
[Používání příkazu extern pro specifikaci propojení](../../cpp/using-extern-to-specify-linkage.md)
