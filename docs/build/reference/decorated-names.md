---
title: Dekorované názvy
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: d9d3db9a3db1943581e5fd603ba85777cb49b863
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423310"
---
# <a name="decorated-names"></a>Dekorované názvy

Funkce, data a objekty v programech jazyka C a C++ jsou reprezentovány interně jejich dekorované názvy. A *dekorovaného názvu* je kódovaný řetězec vytvořený kompilátorem během kompilace objektu, dat nebo definice funkce. Zaznamenává, konvence volání, typy, parametry funkce a další informace spolu s názvem. Tento název dekorace, označované také jako *pozměnění názvu*, pomáhá linkeru najít správné funkce a objekty při propojení spustitelného souboru.

Zásady vytváření názvů upravený změnily v různých verzích aplikace Visual C++ a mohou být různé také na různé cílové architektury. Chcete-li propojit správně se zdrojovými soubory, které jsou vytvořené pomocí jazyka Visual C++, C a C++ knihovny DLL a knihovny by měl být zkompilován pomocí stejné sady nástrojů kompilátoru, příznaky a Cílová architektura.

##  <a name="Using"></a> Použití dekorovaných názvů

Za normálních okolností není nutné znát upravený název napsat kód, který se zkompiluje a odkazy úspěšně. Dekorované názvy jsou interní v kompilátoru a linkeru podrobnosti implementace. Nástroje dokáže obvykle zpracovat v podobě nedekorovaný název. Upravený název je však někdy vyžaduje při zadávání názvu funkce linkeru a dalších nástrojů. Tak, aby odpovídaly přetížených funkcí jazyka C++, členové obory názvů, třídy konstruktory, destruktory a speciálních členských funkcí, je nutné zadat upravený název. Další informace o možnosti příznaky a jiné situace, které vyžadují dekorované názvy, naleznete v dokumentaci nástroje a možnosti, které používáte.

Pokud změníte název funkce, třídy, konvence volání, návratový typ nebo žádné parametry, změní se také upravený název. V takovém případě musíte získat nový upravený název a použít všude, kde je zadán upravený název.

Dekorování názvů je také důležité při připojování ke kódu napsaného v jiných programovacích jazycích, nebo pomocí jiné kompilátory. Různé kompilátory pomocí různých konvencí dekorace názvu. Pokud spustitelný soubor odkazuje na kód v jiném jazyce, musí tak, aby odpovídaly importované a exportované názvy a konvence volání věnovat zvláštní pozornost. Kód jazyka sestavení musí používat Visual C++ dekorované názvy a konvence volání propojení zdrojového kódu napsaného v jazyce Visual C++.

##  <a name="Format"></a> Formát jazyka C++ dekorovaného názvu

Upravený název pro funkci jazyka C++ obsahuje následující informace:

- Název funkce.

- Třída, že funkce je členem skupiny, pokud je členská funkce. To může zahrnovat ohraničující třídu, která obsahuje funkce třídy a tak dále.

- Obor názvů funkce patří, pokud je součást oboru názvů.

- Typy parametrů funkce.

- Konvence volání.

- Návratový typ funkce.

Funkce a třída názvy jsou kódovány ve upravený název. Zbývající část upravený název je kód, který má interní význam pouze pro kompilátor a propojovací program. Následují příklady nedekorovaných a dekorované názvy v jazyce C++.

|Nedekorovaný název|Upravený název|
|----------------------|--------------------|
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|

##  <a name="FormatC"></a> Formát c dekorovaného názvu

Formulář dekorace pro funkce C závisí na konvenci volání použít v jeho deklaraci, jak je znázorněno v následující tabulce. Toto je také dekorace formátu, který se používá, když kód jazyka C++ je deklarován mít `extern "C"` propojení. Je výchozí konvencí volání `__cdecl`. Všimněte si, že v 64bitovém prostředí, nejsou upravená funkce.

|Konvence volání|Dekorace|
|------------------------|----------------|
|`__cdecl`|Úvodní podtržítka (**_**)|
|`__stdcall`|Úvodní podtržítka (**_**) a koncové zavináč (**\@**) následovaný počtem bajtů v seznamu parametrů v desítkové soustavě|
|`__fastcall`|Úvodní a koncové zavináče (**\@**) a desetinné číslo představující počet bajtů v seznamu parametrů|
|`__vectorcall`|Dva koncové zavináče (**\@\@**) a desetinné číslo bajtů v seznamu parametrů|

##  <a name="Viewing"></a> Zobrazení dekorovaných názvů

Upravené podobě název symbolu získáte po kompilaci zdrojového souboru, který obsahuje data, objektu, nebo definice funkce nebo prototypu. Prozkoumat dekorované názvy ve svém programu, můžete použít jednu z následujících metod:

#### <a name="to-use-a-listing-to-view-decorated-names"></a>Seznam použijte k zobrazení dekorovaných názvů

1. Vytvořte seznam tím, že kompilování zdrojového souboru, který obsahuje data, objektu, nebo definice funkce nebo prototypu se [výpis typu souboru](../../build/reference/fa-fa-listing-file.md) – možnost kompilátoru nastavena na sestavení se zdrojovým kódem (**/FAS**).

   Zadejte například `cl /c /FAs example.cpp` příkazového řádku pro vývojáře se vygenerovat soubor výpisu example.asm.

2. Ve výsledném souboru výpisu najděte řádek, který začíná veřejné a končí středníkem, za nímž následuje nedekorovaný název data nebo funkce. Je upravený název symbol mezi veřejné partnerské vztahy a středník.

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>DUMPBIN – použijte k zobrazení dekorovaných názvů

1. Zobrazíte exportované symbolů v souboru .obj nebo .lib zadejte `dumpbin /symbols` `objfile` z příkazového řádku pro vývojáře.

2. Upravené podobě symbol hledejte nedekorovaný název v závorkách. Upravený název je na stejném řádku po kanál (&#124;) znak a před nedekorovaný název.

##  <a name="Undecorated"></a> Zobrazení nedekorovaných názvy

Undname.exe můžete použít k převodu na jeho nedekorovaných formulář upravený název. Tento příklad ukazuje, jak to funguje:

```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation. All rights reserved.

Undecoration of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## <a name="see-also"></a>Viz také:

[Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md)<br/>
[Používání příkazu extern pro specifikaci propojení](../../cpp/using-extern-to-specify-linkage.md)
