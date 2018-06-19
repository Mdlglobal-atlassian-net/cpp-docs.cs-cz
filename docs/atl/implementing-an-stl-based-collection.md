---
title: Implementace kolekci na základě knihovny C++ Standard | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14a09f54598b525346a65b56a335711f114878cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359672"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implementace kolekci na základě knihovny C++ Standard
Poskytuje ATL `ICollectionOnSTLImpl` rozhraní, které vám umožňují rychle implementovat rozhraní pro kolekce na základě standardní knihovna C++ na vašich objektů. Abyste pochopili, jak tato třída funguje, bude fungovat přes jednoduchý (dole) příklad, který používá tuto třídu pro implementaci kolekce jen pro čtení zaměřené na klienty automatizace.  
  
 Ukázkový kód je z [ATLCollections ukázka](../visual-cpp-samples.md).  
  
 K dokončení tohoto postupu budete:  
  
-   [Vygenerovat nový jednoduchý objekt](#vccongenerating_an_object).  
  
-   [Upravte soubor IDL](#vcconedit_the_idl) generovaného rozhraní.  
  
-   [Vytváření definic TypeDef pět](#vcconstorage_and_exposure_typedefs) popisující, jak jsou uložené položky kolekce a jak budou vystavené klientům prostřednictvím rozhraní modelu COM.  
  
-   [Vytvořit dvě definice TypeDef pro kopírování zásad třídy](#vcconcopy_classes).  
  
-   [Vytváření definic TypeDef pro implementace enumerátor a kolekce](#vcconenumeration_and_collection).  
  
-   [Upravit generované v průvodci kódu C++ pro použití typedef kolekce](#vcconedit_the_generated_code).  
  
-   [Přidání kódu k vyplnění kolekce](#vcconpopulate_the_collection).  
  
##  <a name="vccongenerating_an_object"></a> Generování nového jednoduchého objektu  
 Vytvořte nový projekt, zajistíte, že není zaškrtnuto políčko atributy v části Nastavení aplikace. Pomocí dialogového okna knihovny ATL přidat třídu a přidejte Simple Object Wizard k vygenerování jednoduchého objektu s názvem `Words`. Ujistěte se, že volá rozhraní dual `IWords` se vygeneruje. Objekty generovaná třída se používá k reprezentování kolekce slova (řetězce).  
  
##  <a name="vcconedit_the_idl"></a> Úpravy souboru IDL  
 Nyní otevřete soubor IDL a přidejte tři vlastnosti, které jsou nezbytné, chcete-li `IWords` do rozhraní kolekci určenou jen pro čtení, jak je uvedeno níže:  
  
 [!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]  
  
 Toto je standardní formulář pro kolekci určenou jen pro čtení rozhraní navržené s klienty automatizace v paměti. Číslované komentáře v této definici rozhraní odpovídají komentáře níže:  
  
1.  Rozhraní pro kolekce jsou obvykle dva, protože přistupuje k klienti automatizace `_NewEnum` vlastnost prostřednictvím **volání metody IDispatch::Invoke**. Ale automatizace mohou klienti získat přístup zbývající metody prostřednictvím vtable, takže duální rozhraní, je vhodnější odesílající rozhraní.  
  
2.  Pokud nebude rozšířit duální rozhraní a odesílající rozhraní za běhu (to znamená, nebudou zajišťovat další metody nebo vlastnosti prostřednictvím **volání metody IDispatch::Invoke**), byste měli použít **nonextensible –** atribut svou definici. Tento atribut umožňuje klientům automatizace ověření úplného kódu v době kompilace. V takovém případě by neměla být rozšířena rozhraní.  
  
3.  Správné DISPID je důležité, pokud chcete, aby klienti automatizace, abyste mohli pomocí této vlastnosti. (Všimněte si, že pouze jeden podtržítka v **DISPID_NEWENUM**.)  
  
4.  Můžete zadat jakoukoli hodnotu ve v z **položky** vlastnost. Ale **položky** se většinou používá **DISPID_VALUE** Chcete-li výchozí vlastnost kolekce. To umožňuje klientům automatizace odkazovat na vlastnost bez pojmenování jej explicitně.  
  
5.  Datový typ používaný pro vrácenou hodnotu **položky** vlastnost je typ položky uložené v kolekci, pokud jsou klienti COM obavy. Rozhraní vrátí řetězce, takže byste měli používat standardní řetězec typu modelu COM, `BSTR`. Data můžete interně uložit do jiného formátu, jak se krátce zobrazí.  
  
6.  Hodnota použitá DISPID z **počet** je zcela libovolné vlastnosti. Neexistuje žádné standardní DISPID pro tuto vlastnost.  
  
##  <a name="vcconstorage_and_exposure_typedefs"></a> Vytváření definic TypeDef pro úložiště a ohrožení  
 Po definování rozhraní kolekce musíte rozhodnout, jak se data uloží, a jak se zveřejní data prostřednictvím enumerátor.  
  
 Ve formuláři počtu definice TypeDef, které můžete přidat do horní části hlavičkový soubor pro vaše nově vytvořené třídy lze zadat odpovědi na tyto otázky:  
  
 [!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]  
  
 V takovém případě se uloží data jako **std::vector** z **std::string**s. **std::Vector** je standardní knihovna C++ kontejneru třída, která se chová jako spravované pole. **std::String** je standardní knihovna C++ řetězec třída. Tyto třídy snadno pracovat s kolekcí řetězců.  
  
 Podpora jazyka Visual Basic je nezbytné k provedení úspěšné tohoto rozhraní, enumerátor vrácený `_NewEnum` musí podporovat vlastnost **IEnumVARIANT** rozhraní. Toto je pouze enumerátor rozhraní rozumí jazyka Visual Basic.  
  
##  <a name="vcconcopy_classes"></a> Vytváření pro třídy zásady kopírování – definice TypeDef  
 Definice TypeDef, které jste vytvořili, pokud poskytují všechny informace, které je třeba vytvořit další definice TypeDef pro kopírování třídy, které se použijí tak, že enumerátor a kolekce:  
  
 [!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]  
  
 V tomto příkladu můžete použít vlastní `GenericCopy` třídy definované v VCUE_Copy.h a VCUE_CopyString.h z [ATLCollections](../visual-cpp-samples.md) ukázka. Tuto třídu můžete použít v jiném kódu, ale budete muset definovat další specializací `GenericCopy` pro podporu typy dat používaných v vlastní kolekce. Další informace najdete v tématu [třídy ATL kopie zásady](../atl/atl-copy-policy-classes.md).  
  
##  <a name="vcconenumeration_and_collection"></a> Vytváření definic TypeDef pro výčet a kolekce  
 Nyní všechny parametry šablony nezbytné se specializují `CComEnumOnSTL` a `ICollectionOnSTLImpl` třídy v tomto případě byly zadány ve tvaru – definice TypeDef. Pro zjednodušení použití odborností, vytvořte dva další definice TypeDef, jak je uvedeno níže:  
  
 [!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]  
  
 Nyní `CollectionType` se jedná o synonymum specializace `ICollectionOnSTLImpl` , která implementuje `IWords` rozhraní definovaného dříve a poskytuje enumerátor, který podporuje **IEnumVARIANT**.  
  
##  <a name="vcconedit_the_generated_code"></a> Úpravy kódu vygenerované průvodcem  
 Nyní musí být odvozeny `CWords` od implementace rozhraní reprezentována `CollectionType` typedef místo `IWords`, jak je uvedeno níže:  
  
 [!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]  
  
##  <a name="vcconpopulate_the_collection"></a> Přidání kódu k naplnění kolekce  
 Jediné, co zůstane je k naplnění vektoru s daty. V tomto jednoduchém příkladu můžete přidat několik slov ke kolekci v konstruktoru pro třídu:  
  
 [!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]  
  
 Nyní můžete otestovat kód s klienta podle vašeho výběru.  
  
## <a name="see-also"></a>Viz také  
 [Kolekce a výčty](../atl/atl-collections-and-enumerators.md)   
 [Ukázka ATLCollections](../visual-cpp-samples.md)   
 [Třídy zásady kopírování ATL](../atl/atl-copy-policy-classes.md)

