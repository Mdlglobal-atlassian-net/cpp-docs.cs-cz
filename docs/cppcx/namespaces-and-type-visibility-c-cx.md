---
title: Obory názvů a viditelnost typů (C + +/ CX)
ms.date: 12/30/2016
ms.assetid: cbc01a3a-3b69-4ded-9c42-ecbf0fd0a00e
ms.openlocfilehash: e9efc207fe0ed49fecf30366d265019e7a3ee009
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440518"
---
# <a name="namespaces-and-type-visibility-ccx-"></a>Obory názvů a viditelnost typů (C + +/ CX)

Obor názvů je standardní C++ konstrukci pro seskupení typů, které mají související funkce a pro předcházení kolizi názvů v knihovnách. Systém typů prostředí Windows Runtime vyžaduje, že všechny veřejné typy Windows Runtime, včetně těch, které ve svém vlastním kódu, musí být deklarovány v oboru názvů v oboru názvů. Veřejné typy, které jsou deklarovány v globálním oboru nebo vnořit do jiné třídy způsobí chybu kompilace.

Soubor .winmd musí mít stejný název, který má kořenový obor názvů. Například třída, která má název A.B.C.MyClass dá vytvořit instance pouze v případě, že je definována v souboru metadat, který je pojmenován A.winmd a A.B.winmd nebo A.B.C.winmd. Název spustitelného souboru nemusí odpovídat názvu souboru .winmd.

## <a name="type-visibility"></a>Viditelnost typů

V oboru názvů, typy Windows Runtime – na rozdíl od standardních typů C++ – mít přístup k privátní nebo veřejné. Ve výchozím nastavení je privátní přístupnost. Veřejný typ je viditelný pro metadata a je proto lze použít z aplikace a komponenty, které může být napsán v jiných jazycích než C++. Pravidla pro viditelné typy jsou obecně více omezující než pravidla pro neviditelné typy, protože viditelné typy nelze vystavit konceptů specifických pro C++, které nejsou podporovány v jazycích .NET nebo JavaScript.

> [!NOTE]
> Metadata je pouze využívána v době běhu jazyky rozhraní .NET a JavaScript. Když se do jiné aplikace jazyka C++ nebo součást mluví C++ aplikace nebo komponenty – to zahrnuje Windows součásti, které jsou napsány v jazyce C++ – bez běhové spotřeby metadat je povinný.

## <a name="member-accessibility-and-visibility"></a>Usnadnění přístupu člena a viditelnost

V privátním referenční třída, rozhraní nebo delegáta jsou emitovány žádní členové k metadatům, i v případě, že mají přístupnost public. Ve třídách public ref můžete řídit viditelnost členů v metadatech nezávisle na jejich přístupnost ve zdrojovém kódu. Stejně jako v standardním jazyce C++ se vztahují principu nejnižších možných oprávnění; Nenastavujte členové viditelné v metadatech Pokud je nezbytně nutné.

Pomocí následující modifikátory přístupu můžete řídit viditelnost metadat a usnadnění zdrojového kódu.

||||
|-|-|-|
|Modifikátor|Význam|Vygenerován pro metadata?|
|private|Výchozí dostupnost. Stejný význam jako v standardním jazyce C++.|Ne|
|protected|Stejný význam jako v standardním jazyce C++ se v rámci aplikace nebo komponenty a v metadatech.|Ano|
|public|Stejný význam jako v standardním jazyce C++.|Ano|
|`public protected` - nebo - `protected public`|Chráněné usnadnění v metadatech, veřejné v rámci aplikace nebo komponenty.|Ano|
|`protected private` Nebo `private protected`|Nejsou viditelné v metadatech; chráněné usnadnění přístupu v rámci aplikace nebo komponenty.||
|`internal` Nebo `private public`|Člen je veřejný v rámci aplikace nebo komponenty, ale není viditelný v metadatech.|Ne|

## <a name="windows-runtime-namespaces"></a>Obory názvů Windows Runtime

Rozhraní Windows API se skládá z typů, které jsou deklarovány v Windows::\* obory názvů. Tyto obory názvů jsou vyhrazené pro Windows a typy nelze přidat k nim. V **prohlížeče objektů**, zobrazí se tyto obory názvů v souboru windows.winmd. Dokumentaci o těchto oborech názvů najdete v tématu [rozhraní Windows API](https://msdn.microsoft.com/library/windows/apps/br211377).

## <a name="ccx-namespaces"></a>C + +/ CX obory názvů

C + +/ CX definují určité typy v těchto oborech názvů jako součást projekce systém typů prostředí Windows Runtime.

|||
|-|-|
|**Namespace**|**Popis**|
|default|Obsahuje předdefinované číselné a char16 typy. Tyto typy jsou v rozsahu každého oboru názvů a `using` příkaz nikdy není vyžadováno.|
|Platforma|Obsahuje primárně veřejné typy, které odpovídají typy Windows Runtime, jako `Array<T>`, `String`, `Guid`, a `Boolean`. Také zahrnuje typy specializované pomocné rutiny, jako `Platform::Agile<T>` a `Platform::Box<T>`.|
|Platform::Collections –|Obsahuje třídy konkrétní kolekci, které implementují rozhraní Windows Runtime kolekce `IVector`, `IMap`, a tak dále. Tyto typy jsou definovány v souboru hlaviček, collection.h není v platform.winmd.|
|Platform::details –|Obsahuje typy, které se používají v kompilátoru a nejsou určena ke zveřejnění.|

## <a name="see-also"></a>Viz také

[Systém typů (C++/CX)](../cppcx/type-system-c-cx.md)