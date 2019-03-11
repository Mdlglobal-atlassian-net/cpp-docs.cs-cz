---
title: Částečné třídy (C + +/ CX)
ms.date: 12/30/2016
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
ms.openlocfilehash: 71df19e98192a7704d4528fe730ce79977383a9b
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740417"
---
# <a name="partial-classes-ccx"></a>Částečné třídy (C + +/ CX)

Částečné třídy je konstrukce, která podporuje scénáře, ve kterých chcete upravit část definice třídy a automatické generování kódu softwaru – například Návrhář XAML, je také upravovat kód ve stejné třídě. S použitím částečnou třídu, můžete zabránit návrháře přepsání kódu. V projektu sady Visual Studio `partial` modifikátor se použijí automaticky generovaného souboru.

## <a name="syntax"></a>Syntaxe

Chcete-li definovat částečné třídy, použijte `partial` – klíčové slovo bezprostředně před klíč třídy z jaké by byly definici běžné třídy. Klíčové slovo jako například `partial ref class` je kontextové klíčové slovo, který obsahuje prázdné znaky. V následující konstrukce jsou podporovány částečné definice.

- `class` Nebo `struct`

- `ref class` Nebo `ref struct`

- `value class` Nebo `value struct`

- `enum` Nebo `enum class`

- `ref interface`, `interface class`, `interface struct`, nebo `__interface`

- `union`

Tento příklad ukazuje částečné `ref class`:

[!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]

## <a name="contents"></a>Obsah

Definice částečné třídy může obsahovat cokoli, co může obsahovat definici úplné třídy, pokud `partial` – klíčové slovo byly vynechány. S jednou výjimkou to zahrnuje všechny platná konstrukce, jako jsou základní třídy, datové členy, členské funkce, výčty, deklarace typu friend a atributy. Vložená definice členů statických dat jsou povolené a.

Jedinou výjimkou je třída usnadnění. Například příkaz `public partial class MyInvalidClass {/* ... */};` chybu. Všechny specifikátory přístupu, které se používají v definici částečné třídy pro MyInvalidClass nemají vliv na výchozí dostupnost v definici následné částečné nebo úplné třídy pro MyInvalidClass.

Následující fragment kódu ukazuje usnadnění přístupu. V první částečná třída `Method1` je veřejné, protože jeho přístupnost je veřejná. V druhém částečné třídy `Method2` je privátní, protože třída výchozí dostupnost je privátní.

[!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]

## <a name="declaration"></a>Deklarace

Částečnou definici třídy, jako například *MyClass* je pouze deklaraci MyClass. To znamená, ho pouze název zavede *MyClass*. *MyClass* nelze použít tak, aby se vyžaduje definice třídy, například velikost znalost *MyClass* nebo pomocí základní nebo členský z *MyClass*. *MyClass* se považuje za definovat pouze když kompilátor narazí bez částečnou definicí *MyClass*.

Následující příklad ukazuje chování deklarací částečné třídy. Po deklaraci #1 *MyClass* lze použít jako v případě, že by byl zapsán jako Dopředná deklarace `ref class MyClass;`. Deklarace je ekvivalentem deklarace #1.Declaration #3 #2 je platný, protože je Dopředná deklarace třídy. Deklarace #4 není platný, ale protože

*MyClass* není plně definovaná.

Deklarace #5 nepoužívá `partial` – klíčové slovo a deklarace plně definuje *MyClass*. V důsledku toho deklarace #6 je platný.

[!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]

## <a name="number-and-ordering"></a>Počet a pořadí

Může být nula nebo více definicí částečné třídy pro každou úplnou definici třídy.

Každá částečné třídy definice třídy musí předcházet lexikálně jednu úplnou definici této třídy, ale nemusí být předcházet dopředné deklarace třídy. Pokud není žádná úplná definice třídy, pak deklarací částečné třídy lze pouze dopředné deklarace.

Všechny třídy klíče jako `class` a `struct` se musí shodovat. Například, jedná se o chybu kódu `partial class X {}; struct X {};`.

Následující příklad ukazuje počet a pořadí. Poslední částečná deklarace se nezdaří, protože třída je již definován.

[!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]

## <a name="full-definition"></a>Kompletní definici

Místě úplnou definici třídy X chování je stejné jako kdyby byly definice X měl deklarovány základních tříd, členů a tak dále, v pořadí, ve kterém byly došlo k a definované v částečné třídy. To znamená, obsah částečné třídy zacházeno, jako by byly napsány Přejme během úplné definice třídy a vyhledávání názvů a ostatní jazyka pravidla se použijí Přejme během úplné definice třídy jako obsah částečné třídy byly vytvořeny na místě

Následující dva příklady mají stejné význam platnosti a účinnosti. První příklad používá částečné třídy a v druhém příkladu se nepodporuje.

[!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]

[!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]

## <a name="templates"></a>Šablony

Částečná třída nemůže být šablona.

## <a name="restrictions"></a>Omezení

Částečné třídy nemůžou zahrnovat nad rámec jednoho překladové jednotce.

`partial` – Klíčové slovo je podporována pouze v kombinaci s `ref class` – klíčové slovo nebo `value class` – klíčové slovo.

### <a name="examples"></a>Příklady

Následující příklad definuje `Address` třídy mezi dva soubory kódu. Upraví návrháře `Address.details.h` a upravíte `Address.h`. Používá pouze definici třídy v prvním souboru `partial` – klíčové slovo.

[!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]

[!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)
