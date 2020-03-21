---
title: Dekorované názvy
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: 3389b5466bf4a2a48c5e36b01da6818a523fec6f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077353"
---
# <a name="decorated-names"></a>Dekorované názvy

Funkce, data a objekty v jazyce C a C++ programy jsou interně zastoupeny jejich dekorovanými názvy. *Dekorovaný název* je kódovaný řetězec, který kompilátor vytvořil během kompilace objektu, data nebo definice funkce. Zaznamenává konvence volání, typy, parametry funkcí a další informace společně s názvem. Tato dekorace názvů, označovaná také jako *pojmenování názvů*, pomáhá linkeru najít správné funkce a objekty při propojení spustitelného souboru.

Upravené zásady vytváření názvů se v různých verzích sady Visual Studio změnily a můžou se také lišit v různých cílových architekturách. Aby bylo možné správně propojit se zdrojovými soubory vytvořenými pomocí sady Visual C++ Studio, C a knihoven DLL a knihoven, je nutné kompilovat pomocí stejné sady nástrojů kompilátoru, příznaků a cílové architektury.

> [!NOTE]
> Knihovny vytvořené pomocí sady Visual Studio 2015 mohou být spotřebovány aplikacemi vytvořenými pomocí sady Visual Studio 2017 nebo sady Visual Studio 2019.

##  <a name="using-decorated-names"></a><a name="Using"></a>Používání dekorovaných názvů

Za normálních okolností nemusíte znát dekorovaný název, aby bylo možné napsat kód, který bude kompilovat a propojení úspěšné. Dekorované názvy jsou podrobně implementovány pro kompilátor a linker. Nástroje obvykle zpracovávají název v neupravené podobě. Dekorované jméno se ale někdy vyžaduje při zadání názvu funkce linkeru a dalších nástrojů. Například pro spárování přetížených C++ funkcí, členů oborů názvů, konstruktorů tříd, destruktorů a speciálních členských funkcí je nutné zadat dekorované jméno. Podrobnosti o příznacích možností a dalších situacích, které vyžadují dekorované názvy, najdete v dokumentaci k nástrojům a možnostem, které používáte.

Změníte-li název funkce, třídu, konvenci volání, návratový typ nebo libovolný parametr, upravený název se také změní. V takovém případě musíte získat nový dekorovaný název a použít ho všude, kde je zadaný upravený název.

Dekorace názvů je také důležité při propojení s kódem napsaným v jiných programovacích jazycích nebo pomocí jiných kompilátorů. Různé kompilátory používají různé konvence pro dekorace názvů. Pokud vaše spustitelné odkazy na kód napsané v jiném jazyce, musí být provedena zvláštní péče, aby odpovídala exportovaným a importovaným názvům a konvencím volání. Kód jazyka sestavení musí používat MSVC dekorované názvy a konvence volání pro propojení ke zdrojovému kódu napsanému pomocí MSVC.

##  <a name="format-of-a-c-decorated-name"></a><a name="Format"></a>Formát C++ dekorovaného názvu

Dekorované názvy C++ funkce obsahují následující informace:

- Název funkce

- Třída, pro kterou je funkce členem, pokud se jedná o členskou funkci. To může zahrnovat třídu, která obklopuje třídu, která obsahuje funkci, a tak dále.

- Obor názvů, do kterého funkce patří, pokud je součástí oboru názvů.

- Typy parametrů funkce.

- Konvence volání.

- Návratový typ funkce.

Názvy funkcí a tříd jsou v dekorované názvu kódovány. Zbytek dekorovaného názvu je kód, který má vnitřní význam pouze pro kompilátor a linker. Níže jsou uvedeny příklady nedekorované a dekorované C++ názvy.

|Nedekorovaný název|Dekorovaný název|
|----------------------|--------------------|
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|

##  <a name="format-of-a-c-decorated-name"></a><a name="FormatC"></a>Formát dekorované názvy jazyka C

Forma dekorace pro funkci jazyka C závisí na konvenci volání používané v jeho deklaraci, jak je znázorněno v následující tabulce. Toto je také formát dekorace, který se používá, C++ když je kód deklarován pro `extern "C"` propojení. Výchozí konvence volání je `__cdecl`. Všimněte si, že v 64ovém prostředí nejsou funkce dekorované.

|Konvence volání|Dekorace|
|------------------------|----------------|
|`__cdecl`|Počáteční podtržítko ( **_** )|
|`__stdcall`|Počáteční podtržítko ( **_** ) a koncové znaménko ( **\@** ) následované počtem bajtů v seznamu parametrů v desítkové soustavě|
|`__fastcall`|Úvodní a koncové znaménko ( **\@** ) následované desítkovým číslem reprezentujícím počet bajtů v seznamu parametrů|
|`__vectorcall`|Dva na konci znaménka ( **\@\@** ) následovaný desítkovým počtem bajtů v seznamu parametrů|

##  <a name="viewing-decorated-names"></a><a name="Viewing"></a>Zobrazení dekorovaných názvů

Po zkompilování zdrojového souboru, který obsahuje definici dat, objektu nebo definice funkce nebo prototypu, lze získat upravený tvar názvu symbolu. K prohlédnutí dekorací názvů v programu můžete použít jednu z následujících metod:

#### <a name="to-use-a-listing-to-view-decorated-names"></a>Použití seznamu k zobrazení dekorované názvy

1. Vygenerujte výpis kompilací zdrojového souboru, který obsahuje data, objekt nebo definici funkce nebo prototyp s možností kompilátoru [typ souboru výpisu](fa-fa-listing-file.md) nastavenou na sestavení se zdrojovým kódem ( **/FAS**).

   Zadejte například `cl /c /FAs example.cpp` do příkazového řádku pro vývojáře pro vygenerování souboru výpisu, například ASM.

2. Ve výsledném souboru výpisu Najděte řádek, který začíná VEŘEJNÝm, a ukončí středník následovaný nedekorovanými daty nebo názvem funkce. Symbol mezi VEŘEJNÝm a středníkem je upravený název.

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>Použití DUMPBIN k zobrazení dekorované názvy

1. Chcete-li zobrazit exportované symboly v souboru. obj nebo. lib, zadejte do příkazového řádku pro vývojáře `dumpbin /symbols` `objfile`.

2. Chcete-li najít upravený tvar symbolu, vyhledejte nedekorovaný název v závorkách. Dekorovaný název je na stejném řádku, za znakem kanálu (&#124;) a před nedekorovaným názvem.

##  <a name="viewing-undecorated-names"></a><a name="Undecorated"></a>Zobrazení nedekorovaných názvů

Pomocí UNDNAME. exe můžete převést dekorovaný název na jeho nedekorovaný formulář. Tento příklad ukazuje, jak to funguje:

```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation. All rights reserved.

Undecoration of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## <a name="see-also"></a>Viz také

[Další nástroje pro sestavení MSVC](c-cpp-build-tools.md)<br/>
[Používání příkazu extern pro specifikaci propojení](../../cpp/using-extern-to-specify-linkage.md)
