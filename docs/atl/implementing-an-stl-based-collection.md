---
title: Implementace kolekce založené na knihovně Standard jazyka C++
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: 90583f34c9e9fb500bb48fdbd3c1a17d343d865f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292918"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implementace kolekce založené na knihovně Standard jazyka C++

Knihovna ATL poskytuje `ICollectionOnSTLImpl` rozhraní, které umožňují rychle implementovat rozhraní kolekcí založených na standardní knihovny C++ na objekty. Vysvětlení fungování této třídy, bude fungovat přes jednoduchý příklad (dole), který používá tuto třídu pro implementaci kolekce jen pro čtení zaměřené na klientům automatizace.

Ukázkový kód je z [ATLCollections ukázka](../visual-cpp-samples.md).

K dokončení tohoto postupu provedete následující:

- [Generovat nový jednoduchý objekt](#vccongenerating_an_object).

- [Upravte soubor IDL](#vcconedit_the_idl) generované rozhraní.

- [Vytvořit pět – definice TypeDef](#vcconstorage_and_exposure_typedefs) popisující, jak jsou kolekce položek uložených a jak bude vystavena klientům prostřednictvím rozhraní modelu COM.

- [Vytvořte dvě definice typů pro kopírování třídy zásady](#vcconcopy_classes).

- [Vytváření definic TypeDef pro implementace výčet a kolekce](#vcconenumeration_and_collection).

- [Upravit kód C++ generované v průvodci pomocí kolekce typedef](#vcconedit_the_generated_code).

- [Přidejte kód pro naplnění kolekce](#vcconpopulate_the_collection).

##  <a name="vccongenerating_an_object"></a> Generuje se nový jednoduchý objekt

Vytvořte nový projekt, zajištění, že není zaškrtnuto políčko atributy v části Nastavení aplikace. Použijte dialogové okno Přidat třídu knihovny ATL a přidat Simple Object Wizard k vygenerování jednoduchý objekt s názvem `Words`. Ujistěte se, že duální rozhraní s názvem `IWords` je generován. Objekty generované třídy se používá k reprezentování kolekce slov (tedy řetězce).

##  <a name="vcconedit_the_idl"></a> Úpravy souboru IDL

Nyní, otevřete soubor IDL a přidejte tři vlastnosti, které jsou nezbytné k zapnutí `IWords` do rozhraní kolekce jen pro čtení, jak je znázorněno níže:

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

Toto je standardní formulář pro rozhraní kolekce jen pro čtení s klientům automatizace v úvahu. Číslovaných komentářů v této definici rozhraní odpovídají na následující poznámky:

1. Jsou obvykle duální rozhraní pro kolekce, protože přistupuje ke klientům automatizace `_NewEnum` vlastnost prostřednictvím `IDispatch::Invoke`. Ale automatizace klienti mají přístup k zbývající metody prostřednictvím tabulku vtable, takže duální rozhraní jsou upřednostňovány vůči odesílacích rozhraních.

1. Pokud rozhraní dual nebo dispinterface nebude možné rozšířit v době běhu (to znamená, nebude poskytovat další metody nebo vlastnosti prostřednictvím `IDispatch::Invoke`), byste měli použít **nerozšiřitelnou kategorii** atribut do definice. Tento atribut umožňuje klientům automatizace k provedení ověření úplného kódu v době kompilace. V takovém případě by neměly rozšířit rozhraní.

1. Je důležité, pokud chcete klientům automatizace moct tuto vlastnost použít správný identifikátor DISPID. (Všimněte si, že pouze jeden znak podtržení v konstantu DISPID_NEWENUM.)

1. Můžete zadat jakoukoli hodnotu jako hodnota DISPID z `Item` vlastnost. Ale `Item` DISPID_VALUE obvykle používá k němu výchozí vlastnost kolekce. To umožňuje klientům automatizace odkazovat na vlastnost bez pojmenování explicitně.

1. Datový typ používaný pro vrácenou hodnotu `Item` vlastnost má typ položky uložená v kolekci, pokud jsou klienti modelu COM obavy. Rozhraní vrátí hodnotu řetězce, proto byste měli použít standardní řetězec typu modelu COM, BSTR. Data můžete interně uložit v jiném formátu, jak brzy zjistíte.

1. Hodnota použitá identifikátorem DISPID `Count` je zcela libovolné vlastnosti. Neexistuje žádný standardní DISPID pro tuto vlastnost.

##  <a name="vcconstorage_and_exposure_typedefs"></a> Vytvoření definice TypeDef pro úložiště a ohrožení

Po definování rozhraní kolekce musíte rozhodnout, jak budou data uložená a jak budou data přístupné prostřednictvím enumerátor.

Ve formuláři počtu – definice TypeDef, které můžete přidat v horní části souboru hlaviček pro nově vytvořené třídy lze zadat odpovědi na tyto otázky:

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

V takovém případě se uloží data jako **std::vector** z **std::string**s. **std::Vector** je třídou kontejneru standardní knihovny C++, který se chová jako spravovaného pole. **std::String** je třída řetězec standardní knihovny C++. Tyto třídy umožňují snadno pracovat s kolekcí řetězců.

Podpora jazyka Visual Basic je důležité pro úspěch toto rozhraní, enumerátor vrácené `_NewEnum` musí podporovat vlastnost `IEnumVARIANT` rozhraní. Toto je čítač pouze rozhraní srozumitelné pro Visual Basic.

##  <a name="vcconcopy_classes"></a> Vytváření definic TypeDef pro třídy zásady kopírování

Definice TypeDef, které jste vytvořili zatím poskytují všechny informace, které potřebujete k vytvoření dalších – definice TypeDef pro kopie třídy, které budou používat výčet a kolekce:

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

V tomto příkladu můžete použít vlastní `GenericCopy` třídy definované v VCUE_Copy.h a VCUE_CopyString.h z [ATLCollections](../visual-cpp-samples.md) vzorku. Tuto třídu můžete použít v jiném kódu, ale budete muset definovat další specializace `GenericCopy` pro podporu datové typy používané ve své vlastní kolekce. Další informace najdete v tématu [třídy zásady kopírování ATL](../atl/atl-copy-policy-classes.md).

##  <a name="vcconenumeration_and_collection"></a> Vytvoření definice TypeDef pro výčet a kolekce

Nyní všechny parametry šablony nezbytné se specializují `CComEnumOnSTL` a `ICollectionOnSTLImpl` třídy v této situaci byly zadány ve formě – definice TypeDef. Pro zjednodušení používání odborností, vytvořte dva další definice TypeDef, jak je znázorněno níže:

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

Nyní `CollectionType` je synonymum pro specializaci `ICollectionOnSTLImpl` , který implementuje `IWords` rozhraní definovali dříve a poskytuje enumerátor, který podporuje `IEnumVARIANT`.

##  <a name="vcconedit_the_generated_code"></a> Úprava kódu generované průvodcem

Nyní musí být odvozen `CWords` od implementace rozhraní reprezentována `CollectionType` typedef spíše než `IWords`, jak je znázorněno níže:

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

##  <a name="vcconpopulate_the_collection"></a> Přidání kódu k naplnění kolekce

Jediné, co, která zůstává je k naplnění vektoru s daty. V tomto jednoduchém příkladu můžete přidat pár slov do kolekce v konstruktoru pro třídu:

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

Teď můžete otestovat kód s klientem nástroje podle vašeho výběru.

## <a name="see-also"></a>Viz také:

[Kolekce a výčty](../atl/atl-collections-and-enumerators.md)<br/>
[Ukázka ATLCollections](../visual-cpp-samples.md)<br/>
[Třídy zásady kopírování ATL](../atl/atl-copy-policy-classes.md)
