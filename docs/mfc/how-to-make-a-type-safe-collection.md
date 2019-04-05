---
title: 'Postupy: Typově bezpečné kolekce'
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
ms.openlocfilehash: c8be781bad699edb8cb0be844d79802269c3e0c5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781520"
---
# <a name="how-to-make-a-type-safe-collection"></a>Postupy: Typově bezpečné kolekce

Tento článek vysvětluje, jak vytvořit kolekce bezpečného typu pro vlastní datové typy. Mezi témata patří:

- [Pomocí třídy založené na šablonách pro bezpečnost typů](#_core_using_template.2d.based_classes_for_type_safety)

- [Implementace pomocných funkcí](#_core_implementing_helper_functions)

- [Pomocí objektu bez šablony třídy kolekce](#_core_using_nontemplate_collection_classes)

Knihovny Microsoft Foundation Class poskytuje předdefinované typově bezpečné kolekce založené na šablonách jazyka C++. Protože jsou šablony, tyto třídy zajistit bezpečnost typů a snadnost použití bez přetypování typu a další práce navíc při používání objektu bez šablony třídy pro tento účel. Ukázky knihovny MFC [SHROMAŽĎOVAT](../overview/visual-cpp-samples.md) ukazuje použití třídy kolekcí založených na šablony v aplikaci MFC. Obecně platí použijte tyto třídy pokaždé, když napíšete kód nové kolekce.

##  <a name="_core_using_template.2d.based_classes_for_type_safety"></a> Pomocí třídy založené na šablonách pro bezpečnost typů

#### <a name="to-use-template-based-classes"></a>Použít třídy založené na šablonách

1. Deklarujte proměnnou typu třídy kolekce. Příklad:

   [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. Volejte členské funkce objektu kolekce. Příklad:

   [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. V případě potřeby implementovat [pomocné funkce](../mfc/reference/collection-class-helpers.md) a [serializeelements –](../mfc/reference/collection-class-helpers.md#serializeelements). Informace o implementaci těchto funkcí najdete v tématu [implementace pomocných funkcí](#_core_implementing_helper_functions).

Tento příklad ukazuje deklaraci seznamu celých čísel. První parametr v kroku 1 je typ dat uložených jako prvky v seznamu. Druhý parametr určuje, jak se data být předávané a vracené z členské funkce třídy kolekce, jako například `Add` a `GetAt`.

##  <a name="_core_implementing_helper_functions"></a> Implementace pomocných funkcí

Třídy kolekce založené na šablonách `CArray`, `CList`, a `CMap` pomocí pěti globální pomocných funkcí, které můžete přizpůsobit podle potřeb vaší kolekce odvozené třídy. Informace o těchto funkcích pomocné rutiny najdete v tématu [pomocné rutiny třídy kolekce](../mfc/reference/collection-class-helpers.md) v *odkaz knihovny MFC*. Implementace funkce serializace je nezbytné pro většinu použití kolekce založené na šablonách třídy.

###  <a name="_core_serializing_elements"></a> Serializace prvků

`CArray`, `CList`, A `CMap` třídy volání `SerializeElements` elementy kolekce do úložiště nebo číst z archivu.

Výchozí implementace `SerializeElements` pomocnou funkci neodpovídá bitové operace zápisu z objektů do archivu nebo bitové operace čtení z archivu do objektů, v závislosti na tom, zda se ukládají objekty do nebo načíst z archivu. Přepsat `SerializeElements` Pokud tato akce není vhodné.

Pokud vaše kolekce ukládá objekty odvozené z `CObject` a použít `IMPLEMENT_SERIAL` – makro v implementaci třídy elementu kolekce, můžete využít výhod funkce serializace, které jsou integrované do `CArchive` a `CObject`:

[!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

Vložení přetížené operátory pro `CArchive` volání `CObject::Serialize` (nebo přepsání této funkce) pro každý `CPerson` objektu.

##  <a name="_core_using_nontemplate_collection_classes"></a> Pomocí objektu bez šablony třídy kolekce

Knihovna MFC také podporuje třídy kolekcí nepředchází funkce MFC verze 1.0. Tyto třídy nejsou založené na šablonách. Je možné tak, aby obsahovala data z podporovaných typů `CObject*`, `UINT`, `DWORD`, a `CString`. Tyto předdefinované kolekce lze použít (například `CObList`) pro uložení kolekce všechny objekty odvozené z `CObject`. Knihovna MFC poskytuje také další předdefinované kolekce pro primitivní typy, jako `UINT` a ukazatele void (`void`*). Obecně platí ale často je užitečné k definování vlastní kolekce bezpečného typu držet objekty konkrétnější třídy a odvozené. Všimněte si, že tím se kolekce tříd nejsou založené na šablonách představuje víc práce než při použití třídy založené na šabloně.

Existují dva způsoby vytvoření typově bezpečné kolekce s kolekcemi objektu bez šablony:

1. Pomocí kolekcí nešablonových typu přetypování v případě potřeby. Toto je snadnější přístup.

1. Jsou odvozeny z a rozšířit nešablonových typově bezpečné kolekce.

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>Použití objektu bez šablony kolekcí přetypování typu

1. Použijte jednu z objektu bez šablony třídy, jako například `CWordArray`, přímo.

   Například můžete vytvořit `CWordArray` a přidejte do ní všechny 32bitové hodnoty a pak je načíst. Není nic dalšího dělat. Stačí použít předdefinované funkce.

   Můžete také použít předdefinovanou kolekci jako `CObList`, pro všechny objekty odvozené z `CObject`. A `CObList` kolekce je definována pro uchování ukazatele na `CObject`. Při získání objektu, ze seznamu, bude pravděpodobně nutné přetypovat na správný typ. od výsledku `CObList` vrátí ukazatele na funkce `CObject`. Například pokud ukládáte `CPerson` objekty v `CObList` kolekce, je nutné přetypovat element načtená jako ukazatel na `CPerson` objektu. Následující příklad používá `CObList` kolekci pro uchování `CPerson` objekty:

   [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   Tento postup pomocí předdefinované kolekce typu a podle potřeby přetypování může být vhodný pro mnoho kolekcí, které potřebujete. Pokud potřebujete další funkce nebo další bezpečnost typů, použití třídy založené na šablonách, nebo použijte následující postup.

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>Odvodit a rozšířit nešablonových typově bezpečné kolekce

1. Odvození od některého ze třídy předdefinovaného nešablonových vlastní třídu kolekce.

   Pokud odvozujete vaší třídy, můžete přidat funkce obálky typově bezpečné a poskytuje tak zajišťující bezpečnost typů rozhraní pro existující funkce.

   Například, pokud odvozené ze seznamu seznam `CObList` pro uložení `CPerson` objekty, můžete například přidat funkce obálky `AddHeadPerson` a `GetHeadPerson`, jak je znázorněno níže.

   [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   Tyto funkce obálky poskytují typově bezpečný způsob, jak přidat a načíst `CPerson` objekty odvozené seznamu. Vidíte, že pro `GetHeadPerson` funkce, se jednoduše zapouzdření přetypování typu.

   Můžete také přidat nové funkce definováním nových funkcí, které rozšiřují možnosti kolekce, spíše než pouhé obtečení stávajících funkcí v obálky typově bezpečné. Například článek [odstraňování všech objektů v kolekcích CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md) popisuje funkci, kterou chcete odstranit všechny objekty obsažené v seznamu. Tato funkce může být přidán do odvozené třídy jako členskou funkci.

## <a name="see-also"></a>Viz také:

[Kolekce](../mfc/collections.md)
