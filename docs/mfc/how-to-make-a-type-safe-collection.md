---
title: 'Postupy: Příprava typově bezpečné kolekce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- type-safe collections [MFC]
- serializing collection-class elements [MFC]
- collection classes [MFC], type safety
- SerializeElements function [MFC]
- collection classes [MFC], template-based
- serialization [MFC], collection classes
- collection classes [MFC], deriving from nontemplate
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cbcdeec6e39e104625d1b5d47c494915a821d38
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930030"
---
# <a name="how-to-make-a-type-safe-collection"></a>Postupy: Příprava typově bezpečné kolekce
Tento článek vysvětluje, jak chcete-li kolekce bezpečného typu pro vlastní datové typy. Témata zahrnují:  
  
-   [Pomocí třídy založené na šabloně pro zabezpečení typů](#_core_using_template.2d.based_classes_for_type_safety)  
  
-   [Implementace pomocných funkcí](#_core_implementing_helper_functions)  
  
-   [Pomocí objektu bez šablony třídy kolekce](#_core_using_nontemplate_collection_classes)  
  
 Knihovny Microsoft Foundation Class poskytuje předdefinované kolekce bezpečného typu na základě šablon C++. Protože jsou šablony, tyto třídy zajišťuje bezpečnost typů a snadné použití bez přetypování typu a dalších další práci zahrnutých v použití třídy objektu bez šablony pro tento účel. Ukázka MFC [SHROMAŽĎOVAT](../visual-cpp-samples.md) demonstruje použití v aplikaci MFC – třídy kolekce na základě šablon. Obecně platí použijte tyto třídy při každém vytvoření nového kódu kolekce.  
  
##  <a name="_core_using_template.2d.based_classes_for_type_safety"></a> Pomocí třídy založené na šabloně pro zabezpečení typů  
  
#### <a name="to-use-template-based-classes"></a>Použít na základě šablon třídy  
  
1.  Deklarujte proměnnou – třída typu kolekce. Příklad:  
  
     [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]  
  
2.  Zavolejte členské funkce objektu kolekce. Příklad:  
  
     [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]  
  
3.  V případě potřeby implementace [podpůrné funkce](../mfc/reference/collection-class-helpers.md) a [serializeelements –](../mfc/reference/collection-class-helpers.md#serializeelements). Informace o implementaci těchto funkcí najdete v tématu [implementace pomocných funkcí](#_core_implementing_helper_functions).  
  
 Tento příklad ukazuje deklaraci seznam celých čísel. První parametr v kroku 1 je typ dat uložených jako prvky v seznamu. Druhý parametr určuje, jak se data předaný a vrácená z členské funkce kolekce třídy, jako například `Add` a `GetAt`.  
  
##  <a name="_core_implementing_helper_functions"></a> Implementace pomocných funkcí  
 Třídy kolekcí založených na šabloně `CArray`, `CList`, a `CMap` použít pět globální pomocných funkcí, které můžete přizpůsobit podle potřeby pro třídy odvozené kolekce. Informace o těchto pomocných funkcí najdete v tématu [pomocné rutiny třídy kolekce](../mfc/reference/collection-class-helpers.md) v *odkaz knihovny MFC*. Implementace funkce serializace je potřebný u většiny použití třídy kolekcí založených na šablonu.  
  
###  <a name="_core_serializing_elements"></a> Serializace prvků  
 `CArray`, `CList`, A `CMap` třídy volání `SerializeElements` elementy z kolekce k uložení nebo číst z archivu.  
  
 Výchozí implementaci `SerializeElements` pomocné funkce nemá bitové zápisu z objekty do archivu nebo bitové pro objekty, v závislosti na tom, jestli jsou objekty uložené ve čtení z archivu nebo načíst z archivu. Přepsání `SerializeElements` Pokud tato akce není vhodná.  
  
 Pokud kolekce obsahuje objekty, které jsou odvozené z `CObject` a použít `IMPLEMENT_SERIAL` makro implementace třídy elementu kolekce, můžete využít výhod funkcí serializace integrované v `CArchive` a `CObject`:  
  
 [!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]  
  
 Vložení přetížené operátory `CArchive` volání `CObject::Serialize` (nebo přepsání této funkce) pro každý `CPerson` objektu.  
  
##  <a name="_core_using_nontemplate_collection_classes"></a> Pomocí objektu bez šablony třídy kolekce  
 MFC podporuje také kolekce tříd zavedených se MFC verze 1.0. Tyto třídy nejsou založené na šablonách. Lze tak, aby obsahovala data z podporovaných typů `CObject*`, `UINT`, `DWORD`, a `CString`. Můžete použít tyto předdefinované kolekce (například `CObList`) pro uložení kolekce všech objektů, které jsou odvozené z `CObject`. MFC poskytuje také jiné předdefinované kolekce pro primitivní typy, jako `UINT` a void ukazatele (`void`*). Obecně platí ale je často užitečné k definování vlastní kolekce bezpečného typu pro uložení objektů konkrétnější třída a odvozené. Všimněte si, že není to s třídy kolekcí založených na šablonách je další práci než použití třídy na základě šablon.  
  
 Existují dva způsoby vytvoření kolekce bezpečného typu objektu bez šablony kolekcím:  
  
1.  Pomocí objektu bez šablony kolekcí, typ přetypování v případě potřeby. Toto je snadnější přístup.  
  
2.  Odvozena od a rozšířit typově bezpečné kolekce objektu bez šablony.  
  
#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>Použití objektu bez šablony kolekcí pro přetypování typu  
  
1.  Použijte jednu z objektu bez šablony třídy, jako například `CWordArray`, přímo.  
  
     Například můžete vytvořit `CWordArray` a přidávat do něj všechny hodnoty 32bitová verze a potom je znovu načíst. Není co udělat další. Předdefinované funkce právě používáte.  
  
     Můžete také použít předdefinovanou kolekci, například `CObList`, pro všechny objekty odvozené z `CObject`. A `CObList` kolekce je definována pro uložení ukazatele na `CObject`. Pokud načítáte objekt ze seznamu, bude pravděpodobně nutné výsledek, který má správný typ. od přetypovat `CObList` funkce vrátí ukazatele na `CObject`. Pokud ukládáte například `CPerson` objekty v `CObList` kolekce, máte přetypovat element načtené být ukazatel na `CPerson` objektu. Následující příklad používá `CObList` kolekce k uchování `CPerson` objekty:  
  
     [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]  
  
     Tento postup pomocí předdefinované kolekce typu a podle potřeby přetypování může být pro řadu potřeb kolekce. Pokud potřebujete další funkce nebo další bezpečnost typů, použití třídy založené na šablonách, nebo použijte následující postup.  
  
#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>Odvození a rozšířit typově bezpečné kolekce objektu bez šablony  
  
1.  Z jednoho z předdefinovaných objektu bez šablony třídy odvodíte třídě kolekce.  
  
     Pokud odvodíte třídu, můžete přidat funkce zajišťující bezpečnost typů obálku zajistit bezpečnost typů rozhraní pro existující funkce.  
  
     Například, pokud odvozené ze seznamu seznam `CObList` pro uložení `CPerson` objekty, můžete přidat funkce obálky `AddHeadPerson` a `GetHeadPerson`, jak je uvedeno níže.  
  
     [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]  
  
     Tyto funkce obálky zajistit bezpečnost typů způsob, jak přidat a načíst `CPerson` ze seznamu odvozené objekty. Můžete uvidíte, že pro `GetHeadPerson` funkce, jsou jednoduše zapouzdřením typ přetypování.  
  
     Definování nových funkcí, které rozšiřují možnosti kolekce spíše než jenom zabalení stávajících funkcí v bezpečnost typů obálky můžete také přidat nové funkce. Například v článku [odstraňování všech objektů v kolekcích CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md) popisuje funkce, která se odstranit všechny objekty obsažené v seznamu. Tato funkce nebylo možné přidat do odvozené třídy jako členské funkce.  
  
## <a name="see-also"></a>Viz také  
 [Kolekce](../mfc/collections.md)

