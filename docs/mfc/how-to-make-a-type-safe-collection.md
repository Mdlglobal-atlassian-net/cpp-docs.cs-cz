---
title: 'Postupy: Příprava typově bezpečné kolekce'
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections [MFC]
- serializing collection-class elements [MFC]
- collection classes [MFC], type safety
- SerializeElements function [MFC]
- collection classes [MFC], template-based
- serialization [MFC], collection classes
- collection classes [MFC], deriving from nontemplate
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
ms.openlocfilehash: 1901100996a776244b57efe0951795ceec3c630a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377264"
---
# <a name="how-to-make-a-type-safe-collection"></a>Postupy: Příprava typově bezpečné kolekce

Tento článek vysvětluje, jak vytvořit kolekce bezpečné pro typ pro vlastní datové typy. Témata:

- [Použití tříd založených na šabloně pro bezpečnost typů](#_core_using_template.2d.based_classes_for_type_safety)

- [Implementace pomocné funkce](#_core_implementing_helper_functions)

- [Použití tříd kolekce bez šablony](#_core_using_nontemplate_collection_classes)

Knihovna tříd Microsoft Foundation poskytuje předdefinované kolekce bezpečné typ ové na základě šablon jazyka C++. Vzhledem k tomu, že se jedná o šablony, pomáhají tyto třídy zajistit bezpečnost typů a snadné použití bez přetypování typu a další práce, které se podílejí na použití třídy bez šablony pro tento účel. Ukázka knihovny MFC [collect](../overview/visual-cpp-samples.md) demonstruje použití tříd kolekce založené na šabloně v aplikaci knihovny MFC. Obecně platí, že tyto třídy používejte při každém psaní kódu nové kolekce.

## <a name="using-template-based-classes-for-type-safety"></a><a name="_core_using_template.2d.based_classes_for_type_safety"></a>Použití tříd založených na šabloně pro bezpečnost typů

#### <a name="to-use-template-based-classes"></a>Použití tříd založených na šabloně

1. Deklarujte proměnnou typu třídy kolekce. Příklad:

   [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. Volání členské funkce objektu kolekce. Příklad:

   [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. V případě potřeby implementujte [pomocné funkce](../mfc/reference/collection-class-helpers.md) a [SerializeElements](../mfc/reference/collection-class-helpers.md#serializeelements). Informace o implementaci těchto funkcí naleznete v [tématu Implementace pomocné funkce](#_core_implementing_helper_functions).

Tento příklad ukazuje deklaraci seznamu celých čísel. První parametr v kroku 1 je typ dat uložených jako prvky seznamu. Druhý parametr určuje, jak mají být data předána a vrácena z `Add` členských `GetAt`funkcí třídy kolekce, například a .

## <a name="implementing-helper-functions"></a><a name="_core_implementing_helper_functions"></a>Implementace pomocné funkce

Třídy `CArray`kolekce založené `CList`na `CMap` šabloně , a použít pět globální pomocné funkce, které můžete přizpůsobit podle potřeby pro odvozené kolekce třídy. Informace o těchto pomocných funkcích naleznete v tématu [Pomocníky třídy kolekce](../mfc/reference/collection-class-helpers.md) v *referenční příručce knihovny MFC*. Implementace funkce serializace je nezbytná pro většinu použití tříd kolekce založených na šabloně.

### <a name="serializing-elements"></a><a name="_core_serializing_elements"></a>Serializace prvků

`CArray`Volání `CList`, `CMap` a `SerializeElements` třídy pro uložení prvků kolekce do archivu nebo jejich čtení z archivu.

Výchozí implementace `SerializeElements` pomocné funkce provádí bitový zápis z objektů do archivu nebo bitové čtení z archivu do objektů v závislosti na tom, zda jsou objekty uloženy nebo načteny z archivu. Přepište, `SerializeElements` pokud tato akce není vhodná.

Pokud vaše kolekce ukládá `CObject` objekty odvozené z a použít `IMPLEMENT_SERIAL` makro při implementaci třídy elementkolekce, můžete `CArchive` `CObject`využít funkce serializace integrované do a :

[!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

Přetížené operátory vložení `CArchive` pro `CObject::Serialize` volání (nebo přepsání této `CPerson` funkce) pro každý objekt.

## <a name="using-nontemplate-collection-classes"></a><a name="_core_using_nontemplate_collection_classes"></a>Použití tříd kolekce nešablon

Knihovna MFC také podporuje třídy kolekce zavedené knihovnou MFC verze 1.0. Tyto třídy nejsou založeny na šablonách. Lze je použít k zobrazení dat `CObject*` `UINT`podporovaných typů , , `DWORD`a `CString`. Tyto předdefinované kolekce (například) `CObList`můžete použít k uložení kolekcí `CObject`všech objektů odvozených z . Knihovna MFC také poskytuje další předdefinované `UINT` kolekce pro uložení`void`primitivních typů, jako jsou ukazatele a ukazatele void ( *). Obecně je však často užitečné definovat vlastní kolekce bezpečné typ uchovávat objekty konkrétnější třídy a jeho deriváty. Všimněte si, že tím s třídy kolekce není založena na šablony je více práce než pomocí třídy založené na šabloně.

Existují dva způsoby, jak vytvořit kolekce bezpečné ho typu s kolekcemi bez šablon:

1. Použijte kolekce nontemplate, v případě potřeby s přetypování typu. To je jednodušší přístup.

1. Odvodit a rozšířit kolekci bez typu šablony.

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>Použití kolekcí bez šablon s přetypováním typů

1. Použijte jednu z nešablonových `CWordArray`tříd, například , přímo.

   Můžete například vytvořit `CWordArray` a přidat libovolné 32bitové hodnoty a pak je načíst. Už není co dělat. Stačí použít předdefinované funkce.

   Můžete také použít předdefinovanou kolekci, například `CObList`, `CObject`k uložení všech objektů odvozených z . Kolekce `CObList` je definována pro `CObject`uložení ukazatelů na . Při načtení objektu ze seznamu bude pravděpodobně muset přetypovat `CObList` výsledek na správný `CObject`typ, protože funkce vrátí ukazatele na . Například pokud ukládáte `CPerson` objekty v `CObList` kolekci, budete muset přetypovat `CPerson` načtený prvek jako ukazatel na objekt. Následující příklad používá `CObList` kolekci `CPerson` k uložení objektů:

   [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   Tento postup použití předdefinované ho typu kolekce a odlévání podle potřeby může být vhodné pro mnoho potřeb kolekce. Pokud potřebujete další funkce nebo větší bezpečnost typů, použijte třídu založenou na šabloně nebo postupujte podle následujícího postupu.

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>Odvození a rozšíření kolekce bez šablony typu bezpečné

1. Odvodit vlastní třídu kolekce z jedné z předdefinovaných tříd nešablony.

   Při odvození třídy můžete přidat funkce obálky bezpečné typ poskytnout typ bezpečné rozhraní pro existující funkce.

   Pokud jste například `CObList` odvodili `CPerson` seznam z objektu pro `AddHeadPerson` `GetHeadPerson`uložení objektů, můžete přidat funkce obálky a , jak je znázorněno níže.

   [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   Tyto funkce obálky poskytují typově bezpečný `CPerson` způsob přidání a načtení objektů z odvozeného seznamu. Můžete vidět, že `GetHeadPerson` pro funkci, jste prostě zapouzdření typu odlévání.

   Můžete také přidat nové funkce definováním nové funkce, které rozšiřují možnosti kolekce spíše než jen zabalení existující funkce v typu bezpečné obálky. Například článek [Odstranění všech objektů v kolekci CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md) popisuje funkci pro odstranění všech objektů obsažených v seznamu. Tato funkce může být přidána do odvozené třídy jako členská funkce.

## <a name="see-also"></a>Viz také

[Kolekce](../mfc/collections.md)
