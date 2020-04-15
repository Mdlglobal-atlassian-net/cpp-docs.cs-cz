---
title: Implementace kolekce založené na standardní knihovně c++
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: e80ce5e7bbc6b9c6be1615dad1ea43c18e03eb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319440"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implementace kolekce založené na standardní knihovně c++

Knihovna ATL poskytuje rozhraní, `ICollectionOnSTLImpl` které umožňuje rychle implementovat rozhraní kolekce založené na standardní knihovně jazyka C++ na objektech. Chcete-li pochopit, jak tato třída funguje, budete pracovat prostřednictvím jednoduchý příklad (níže), který používá tuto třídu k implementaci kolekce jen pro čtení zaměřené na klienty automatizace.

Ukázkový kód je ze [vzorku ATLCollections](../overview/visual-cpp-samples.md).

K dokončení tohoto postupu:

- [Generovat nový jednoduchý objekt](#vccongenerating_an_object).

- [Upravte soubor IDL](#vcconedit_the_idl) pro generované rozhraní.

- [Vytvořte pět typedefs](#vcconstorage_and_exposure_typedefs) popisující, jak jsou uloženy položky kolekce a jak budou vystaveny klientům prostřednictvím rozhraní COM.

- [Vytvořte dvě typedefs pro kopírování tříd zásad](#vcconcopy_classes).

- [Vytvořte typedefs pro čítač výčtu a kolekce implementace](#vcconenumeration_and_collection).

- [Upravte kód c++ generovaný průvodcem tak, aby používal příkaz typedef kolekce](#vcconedit_the_generated_code).

- [Přidejte kód k naplnění kolekce](#vcconpopulate_the_collection).

## <a name="generating-a-new-simple-object"></a><a name="vccongenerating_an_object"></a>Generování nového jednoduchého objektu

Vytvořte nový projekt a zajistěte, aby bylo zaškrtnuto políčko Atributy v části Nastavení aplikace. Dialogové okno Přidat třídu knihovny ATL a Průvodce `Words`přidáním jednoduchého objektu můžete vygenerovat s názvem Jednoduchý objekt . Ujistěte se, že `IWords` je generováno duální rozhraní volané. Objekty generované třídy budou použity k reprezentaci kolekce slov (to znamená řetězce).

## <a name="editing-the-idl-file"></a><a name="vcconedit_the_idl"></a>Úprava souboru IDL

Nyní otevřete soubor IDL a přidejte `IWords` tři vlastnosti potřebné k přeměně na rozhraní kolekce jen pro čtení, jak je znázorněno níže:

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

Toto je standardní formulář pro rozhraní kolekce jen pro čtení navržené s ohledem na klienty automatizace. Očíslované komentáře v této definici rozhraní odpovídají níže uvedenépoznámky:

1. Rozhraní kolekce jsou obvykle duální, `_NewEnum` protože `IDispatch::Invoke`klienti automatizace přistupuje k vlastnosti prostřednictvím . Klienti automatizace však přístup k zbývající metody prostřednictvím vtable, takže duální rozhraní jsou vhodnější dispinterfaces.

1. Pokud duální rozhraní nebo dispinterface nebude prodloužena za běhu (to znamená, `IDispatch::Invoke`že nebude poskytovat další metody nebo vlastnosti prostřednictvím ), měli byste použít **nonextensible** atribut pro vaši definici. Tento atribut umožňuje klientům automatizace provádět úplné ověření kódu v době kompilace. V tomto případě by rozhraní nemělo být rozšířeno.

1. Správné DISPID je důležité, pokud chcete, aby klienti automatizace mohli používat tuto vlastnost. (Všimněte si, že v DISPID_NEWENUM je pouze jedno podtržítko.)

1. Můžete zadat libovolnou hodnotu jako `Item` DISPID vlastnosti. Však `Item` obvykle používá DISPID_VALUE, aby byla výchozí vlastnost kolekce. To umožňuje klientům automatizace odkazovat na vlastnost bez pojmenování explicitně.

1. Datový typ použitý pro vrácenou `Item` hodnotu vlastnosti je typ položky uložené v kolekci, pokud jde o klienty COM. Rozhraní vrací řetězce, takže byste měli použít standardní typ řetězce COM, BSTR. Data můžete uložit interně v jiném formátu, jak se brzy zobrazí.

1. Hodnota použitá pro DISPID `Count` vlastnosti je zcela libovolná. Neexistuje žádný standardní DISPID pro tuto vlastnost.

## <a name="creating-typedefs-for-storage-and-exposure"></a><a name="vcconstorage_and_exposure_typedefs"></a>Vytváření typedefs pro úložiště a expozici

Jakmile je definováno rozhraní kolekce, musíte se rozhodnout, jak budou data uložena a jak budou data vystavena prostřednictvím čítače výčtu.

Odpovědi na tyto otázky mohou být poskytnuty ve formě několika typedefs, které můžete přidat v horní části souboru záhlaví pro nově vytvořenou třídu:

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

V takovém případě uložíte data jako **std::vector** **std::string**s. **std::vector** je třída kontejneru standardní knihovny jazyka C++, která se chová jako spravované pole. **std::string** je třída řetězce standardní knihovny jazyka C++. Tyto třídy usnadňují práci s kolekcí řetězců.

Vzhledem k tomu, že podpora jazyka je důležité pro úspěch `_NewEnum` tohoto rozhraní, čítač výčtu vrácené vlastnost musí podporovat `IEnumVARIANT` rozhraní. Toto je pouze rozhraní výčtu rozuměl Visual Basic.

## <a name="creating-typedefs-for-copy-policy-classes"></a><a name="vcconcopy_classes"></a>Vytváření typedefs pro třídy zásad kopírování

Typedefs, které jste vytvořili dosud poskytují všechny informace, které potřebujete k vytvoření další typedefs pro třídy kopírování, které budou použity čítače výčtu a kolekce:

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

V tomto příkladu můžete `GenericCopy` použít vlastní třídu definovanou v VCUE_Copy.h a VCUE_CopyString.h ze vzorku [ATLCollections.](../overview/visual-cpp-samples.md) Tuto třídu můžete použít v jiném kódu, ale možná `GenericCopy` budete muset definovat další specializace pro podporu datových typů používaných ve vlastních kolekcích. Další informace naleznete v tématu [TŘÍDY zásad kopírování žoonálu .](../atl/atl-copy-policy-classes.md)

## <a name="creating-typedefs-for-enumeration-and-collection"></a><a name="vcconenumeration_and_collection"></a>Vytváření typedefs pro výčet a kolekci

Nyní všechny parametry šablony nezbytné `CComEnumOnSTL` `ICollectionOnSTLImpl` pro specialitu a třídy pro tuto situaci byly poskytnuty ve formě typedefs. Chcete-li zjednodušit použití specializací, vytvořte další dva typedefs, jak je znázorněno níže:

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

Nyní `CollectionType` je synonymem pro `ICollectionOnSTLImpl` specializaci, `IWords` která implementuje rozhraní definované dříve `IEnumVARIANT`a poskytuje čítač výčtu, který podporuje .

## <a name="editing-the-wizard-generated-code"></a><a name="vcconedit_the_generated_code"></a>Úprava kódu generovaného průvodcem

Nyní musíte `CWords` odvozovat z implementace `CollectionType` rozhraní reprezentované typedef spíše než `IWords`, jak je znázorněno níže:

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

## <a name="adding-code-to-populate-the-collection"></a><a name="vcconpopulate_the_collection"></a>Přidání kódu k naplnění kolekce

Jediná věc, která zůstává, je naplnit vektor daty. V tomto jednoduchém příkladu můžete přidat několik slov do kolekce v konstruktoru pro třídu:

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

Nyní můžete kód otestovat s klientem podle vašeho výběru.

## <a name="see-also"></a>Viz také

[Sbírky a čítače výčtu](../atl/atl-collections-and-enumerators.md)<br/>
[Ukázka atlcollections](../overview/visual-cpp-samples.md)<br/>
[Třídy zásad kopírování atl](../atl/atl-copy-policy-classes.md)
