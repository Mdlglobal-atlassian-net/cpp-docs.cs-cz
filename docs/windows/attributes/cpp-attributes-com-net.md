---
title: Atributy C++ pro COM a .NET
ms.custom: index-page
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
ms.openlocfilehash: 734d82a30df3e143a6f47cb1b3eca2cd778830bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214926"
---
# <a name="c-attributes-for-com-and-net"></a>Atributy C++ pro COM a .NET

Microsoft definuje sadu C++ atributů, které zjednodušují programování v modelu COM a .NET Framework vývoj společného jazykového modulu runtime. Při zahrnutí atributů do zdrojových souborů kompilátor pracuje s knihovnami DLL zprostředkovatele pro vložení kódu nebo úpravy kódu v generovaných souborech objektů. Tyto atributy pomáhají při vytváření souborů. idl, rozhraní, knihoven typů a dalších prvků COM. V integrovaném vývojovém prostředí (IDE) jsou atributy podporovány průvodci a okno Vlastnosti.

I když atributy eliminují některé podrobné kódování potřebné pro zápis objektů COM, budete potřebovat základní informace v [modelu COM](/windows/win32/com/the-component-object-model) , aby je bylo možné nejlépe použít.

> [!NOTE]
> Pokud hledáte C++ standardní atributy, přečtěte si téma [atributy](../../cpp/attributes.md).

## <a name="purpose-of-attributes"></a>Účel atributů

Atributy, C++ které se šíří v směrech, nejsou aktuálně možné, aniž by došlo k narušení klasické struktury jazyka. Atributy povolují poskytovatelům (samostatné knihovny DLL) dynamické rozšiřování funkcí jazyka. Hlavním cílem atributů je zjednodušit vytváření komponent modelu COM, kromě zvýšení úrovně produktivity pro vývojáře komponent. Atributy lze použít pro skoro jakoukoli C++ konstrukci, jako jsou třídy, datové členy nebo členské funkce. Následuje přehled výhod poskytovaných touto novou technologií:

- Zveřejňuje známou a jednoduchou konvenci volání.

- Pomocí vloženého kódu, který je na rozdíl od maker, je rozpoznáno ladicím programem.

- Umožňuje snadné odvození ze základních tříd bez podrobností implementace zatěžujících.

- Nahrazuje velký objem kódu IDL, který je vyžadován komponentou modelu COM, s několika stručnými atributy.

Například pro implementaci jednoduché jímky událostí pro obecnou třídu ATL můžete použít atribut [event_receiver](event-receiver.md) na konkrétní třídu, jako je například `CMyReceiver`. Atribut `event_receiver` poté zkompiluje kompilátor společnosti Microsoft C++ , který vloží správný kód do souboru objektu.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

Potom můžete nastavit metody `CMyReceiver` `handler1` a `handler2` pro zpracování událostí (pomocí vnitřní [__hook](../../cpp/hook.md)funkce) ze zdroje událostí, který můžete vytvořit pomocí [event_source](event-source.md).

## <a name="basic-mechanics-of-attributes"></a>Základní mechanismy atributů

Existují tři způsoby, jak do projektu vložit atributy. Nejprve je můžete vložit do zdrojového kódu ručně. Za druhé je můžete vložit pomocí mřížky vlastností objektu v projektu. Nakonec je můžete vložit pomocí různých průvodců. Další informace o použití okna **vlastnosti** a různých průvodců naleznete v tématu [projekty sady Visual Studio – C++ ](../../build/creating-and-managing-visual-cpp-projects.md).

Stejně jako v případě, kdy je projekt sestaven, kompilátor analyzuje každý C++ zdrojový soubor a vytváří soubor objektu. Pokud však kompilátor narazí na atribut, je analyzován a syntakticky ověřen. Kompilátor potom dynamicky volá poskytovatele atributu pro vložení kódu nebo provedení dalších úprav v době kompilace. Implementace poskytovatele se liší v závislosti na typu atributu. Například atributy související s ATL jsou implementovány pomocí Atlprov. dll.

Následující obrázek ukazuje vztah mezi kompilátorem a poskytovatelem atributu.

![Komunikace atributů komponenty](../media/vccompattrcomm.gif "Komunikace atributů komponenty")

> [!NOTE]
> Použití atributů nemění obsah zdrojového souboru. Jediným časem, kdy je kód generovaného atributu viditelný, je během ladění relace. Kromě toho můžete pro každý zdrojový soubor v projektu vygenerovat textový soubor, který zobrazí výsledky náhrady atributu. Další informace o tomto postupu naleznete v tématu [/FX (sloučení vloženého kódu)](../../build/reference/fx-merge-injected-code.md) a [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).

Podobně jako C++ u většiny konstrukcí mají atributy sadu vlastností, které definují jejich správné použití. Tato vlastnost je označována jako kontext atributu a je řešena v tabulce kontextu atributů pro každý odkaz na atribut. Například atribut typu [Coclass](coclass.md) lze použít pouze pro existující třídu nebo strukturu, a to na rozdíl od atributu [cpp_quote](cpp-quote.md) , který může být vložen kamkoli do C++ zdrojového souboru.

## <a name="building-an-attributed-program"></a>Sestavení programu s atributy

Po umístění vizuálních C++ atributů do zdrojového kódu můžete chtít, aby kompilátor společnosti Microsoft C++ vytvořil pro vás knihovnu typů a soubor. idl. Následující možnosti linkeru vám pomůžou při sestavování souborů. tlb a. idl:

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

Některé projekty obsahují více nezávislých souborů. idl. Slouží k vytvoření dvou nebo více souborů. tlb a volitelně k jejich svázání do bloku prostředků. Tento scénář není v současné době podporován ve C++vizuálu.

Kromě toho vizuální C++ linker vypíše všechny informace o atributu související s IDL do jediného souboru MIDL. Neexistuje žádný způsob, jak vygenerovat dvě knihovny typů z jednoho projektu.

## <a name="attribute-contexts"></a><a name="contexts"></a>Kontexty atributů

C++atributy je možné popsat pomocí čtyř základních polí: cíl, na který se dá použít (**platí pro**), pokud se dají opakovat nebo ne (**Opakovat**), požadované přítomnosti ostatních atributů (**povinné atributy**) a nekompatibility s jinými atributy (**neplatné atributy**). Tato pole jsou uvedena v doprovodné tabulce v referenčním tématu každého atributu. Každé z těchto polí je popsáno níže.

### <a name="applies-to"></a>Platí pro

Toto pole popisuje různé C++ prvky jazyka, které jsou platnými cíli pro zadaný atribut. Například pokud atribut v poli **platí pro** určuje "Class", znamená to, že atribut lze použít pouze na právní C++ třídu. Pokud je atribut použit na členskou funkci třídy, výsledkem by byla chyba syntaxe.

Další informace naleznete v tématu [atributy podle použití](attributes-by-usage.md).

### <a name="repeatable"></a>REPEATABLE

Toto pole uvádí, zda lze atribut opakovaně použít na stejný cíl. Většinu atributů nelze opakovat.

### <a name="required-attributes"></a>Požadované atributy

Toto pole obsahuje seznam atributů, které musí být přítomny (tj. použité na stejný cíl) pro správné fungování zadaného atributu. Pro atribut, který má pro toto pole nějaké položky, není běžné.

### <a name="invalid-attributes"></a>Neplatné atributy

Toto pole obsahuje seznam dalších atributů, které nejsou kompatibilní se zadaným atributem. Pro atribut, který má pro toto pole nějaké položky, není běžné.

## <a name="in-this-section"></a>V tomto oddílu

[Nejčastější dotazy k programování s atributy](attribute-programming-faq.md)<br/>
[Atributy podle skupin](attributes-by-group.md)<br/>
[Atributy podle použití](attributes-by-usage.md)<br/>
[Abecedně řazená referenční dokumentace k atributům](attributes-alphabetical-reference.md)
