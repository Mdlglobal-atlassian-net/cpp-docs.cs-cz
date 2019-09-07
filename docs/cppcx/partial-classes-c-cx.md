---
title: Částečné třídy (C++/CX)
ms.date: 12/30/2016
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
ms.openlocfilehash: 703f12498e0f2c68448e2b3896d3d5f906aba779
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740478"
---
# <a name="partial-classes-ccx"></a>Částečné třídy (C++/CX)

Částečná třída je konstrukce, která podporuje scénáře, ve kterých upravujete jednu část definice třídy, a automatický software pro generování kódu, například Návrhář XAML, je také upravován kódem ve stejné třídě. Pomocí částečné třídy můžete zabránit návrháři v přepsání kódu. V projektu `partial` sady Visual Studio je modifikátor použit automaticky pro vygenerovaný soubor.

## <a name="syntax"></a>Syntaxe

Chcete-li definovat částečnou třídu, `partial` použijte klíčové slovo bezprostředně před klíčovou zkratkou třídy, co by jinak bylo definice normální třídy. Klíčové slovo, jako `partial ref class` je kontextové klíčové slovo, které obsahuje prázdné znaky. Částečné definice jsou podporovány v následujících konstrukcích.

- `class` Nebo `struct`

- `ref class` Nebo `ref struct`

- `value class` Nebo `value struct`

- `enum` Nebo `enum class`

- `ref interface`, `interface class`, `interface struct`nebo`__interface`

- `union`

Tento příklad ukazuje částečnou `ref class`:

[!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]

## <a name="contents"></a>Obsah

Definice částečné třídy může obsahovat cokoli, co definice celé třídy může obsahovat, pokud `partial` bylo klíčové slovo vynecháno. Jedinou výjimkou je to, že zahrnuje všechny platné konstrukce, jako jsou základní třídy, datové členy, členské funkce, výčty, deklarace typu Friend a atributy. A vložené definice statických datových členů jsou povoleny.

Jedinou výjimkou je přístupnost třídy. Například příkaz `public partial class MyInvalidClass {/* ... */};` je chyba. Všechny specifikátory přístupu, které jsou používány v definici částečné třídy pro MyInvalidClass, nemají vliv na výchozí přístupnost v následné částečné nebo úplné definici třídy pro MyInvalidClass.

Následující fragment kódu ukazuje přístupnost. V první částečné třídě je veřejná `Method1` , protože její přístupnost je veřejná. Ve druhé dílčí třídě je soukromá `Method2` , protože přístupnost výchozí třídy je soukromá.

[!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]

## <a name="declaration"></a>Deklarace

Částečná definice třídy, jako je například *MyClass* , je pouze deklarací MyClass. To znamená, že zavádí pouze název *MyClass*. *MyClass* nelze použít způsobem, který vyžaduje definici třídy, například znalost velikosti *MyClass* nebo použití základní nebo člena *MyClass*. *MyClass* je považována za určenou pouze v případě, že kompilátor narazí na nečástečnou definici *MyClass*.

Následující příklad ukazuje chování deklarace částečné třídy. Po deklaraci #1 lze použít *MyClass* , jako by byla zapsána jako dopředná `ref class MyClass;`deklarace. Deklarace #2 je ekvivalentní #1 deklarací. deklarace #3 je platná, protože se jedná o dopřednou deklaraci třídy. Deklarace #4 však není platná, protože

*MyClass* není zcela definován.

Deklarace #5 nepoužívá `partial` klíčové slovo a deklarace plně definuje *MyClass*. V důsledku toho je deklarace #6 platná.

[!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]

## <a name="number-and-ordering"></a>Počet a řazení

Pro každou úplnou definici třídy může být k dispozici nula nebo více definic dílčí třídy.

Každá definice dílčí třídy třídy musí být lexikální před jednou úplnou definicí této třídy, ale nemusí předcházet před dopředné deklarace třídy. Pokud neexistuje úplná definice třídy, deklarace částečné třídy mohou být pouze předávány deklarace.

Všechny klíče třídy, například `class` a, `struct` musí odpovídat. Například se jedná o chybu kódu `partial class X {}; struct X {};`.

Následující příklad znázorňuje číslo a řazení. Poslední částečná deklarace se nezdařila, protože třída je již definována.

[!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]

## <a name="full-definition"></a>Úplná definice

V bodě úplné definice třídy X je chování stejné, jako kdyby definice X deklarovala všechny základní třídy, členy a tak dále, v pořadí, ve kterém byly nalezeny a definovány v dílčích třídách. To znamená, že obsah dílčích tříd je považován za, i když byly zapsány v místě úplné definice třídy, a vyhledávání názvů a další jazyková pravidla jsou použita v bodě úplné definice třídy, jako by se jednalo o obsah dílčích tříd. byly zapsány na místě

Následující dva příklady kódu mají stejný význam a účinek. První příklad používá částečnou třídu a druhý příklad ne.

[!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]

[!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]

## <a name="templates"></a>Šablony

Částečná třída nemůže být šablonou.

## <a name="restrictions"></a>Omezení

Částečná třída nemůže být mimo jednu jednotku překladu.

Klíčové slovo je podporováno pouze v kombinaci `ref class` s klíčovým slovem `value class` nebo klíčovým slovem. `partial`

### <a name="examples"></a>Příklady

Následující příklad definuje `Address` třídu napříč dvěma soubory kódu. Návrhář upraví `Address.details.h` a Vy upravíte `Address.h`. Klíčové slovo se `partial` používá jenom v definici třídy v prvním souboru.

[!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]

[!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
