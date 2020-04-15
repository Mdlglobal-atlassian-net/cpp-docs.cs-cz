---
title: Smazání všech objektů v kolekcích CObject
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], deleting in collections
- objects in CObject collections, deleting
- CObject class [MFC], deleting in collection
- collection classes [MFC], deleting all objects
- CObject class collection
- objects in CObject collections
- collection classes [MFC], shared objects
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
ms.openlocfilehash: 303b8a566a730c5abd06d51fb7977174e19a6435
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370541"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Smazání všech objektů v kolekcích CObject

Tento článek vysvětluje, jak odstranit všechny objekty v kolekci (bez odstranění samotného objektu kolekce).

Chcete-li odstranit všechny objekty v kolekci `CObject`s `CObject`(nebo objektů odvozených z ) použijte jednu z iterace techniky popsané v článku [Přístup k všem členům kolekce](../mfc/accessing-all-members-of-a-collection.md) odstranit každý objekt v pořadí.

> [!CAUTION]
> Objekty v kolekcích lze sdílet. To znamená, že kolekce udržuje ukazatel na objekt, ale jiné části programu může mít také ukazatele na stejný objekt. Musíte být opatrní, abyste neodstranili objekt, který je sdílen, dokud nebudou všechny součásti dokončeny pomocí objektu.

Tento článek ukazuje, jak odstranit objekty v:

- [Seznam](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [Pole](#_core_to_delete_all_elements_in_an_array)

- [Mapa](#_core_to_delete_all_elements_in_a_map)

#### <a name="to-delete-all-objects-in-a-list-of-pointers-to-cobject"></a><a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>Odstranění všech objektů v seznamu ukazatelů na Objekt CObject

1. Pomocí `GetHeadPosition` `GetNext` a iterát prostřednictvím seznamu.

1. Pomocí operátoru **delete** odstraňte každý objekt, jak je zjištěn v iteraci.

1. Volání `RemoveAll` funkce odebrat všechny prvky ze seznamu po objekty spojené s těmito prvky byly odstraněny.

Následující příklad ukazuje, jak odstranit všechny `CPerson` objekty ze seznamu objektů. Každý objekt v seznamu je `CPerson` ukazatel na objekt, který byl původně přidělen na haldě.

[!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

Poslední volání funkce `RemoveAll`, je členská funkce seznamu, která odebere všechny prvky ze seznamu. Členská `RemoveAt` funkce odebere jeden prvek.

Všimněte si rozdílu mezi odstraněním objektu prvku a odebráním samotného prvku. Odebrání prvku ze seznamu pouze odebere odkaz seznamu na objekt. Objekt stále existuje v paměti. Když odstraníte objekt, přestane existovat a jeho paměť je vyvolána. Proto je důležité odebrat prvek ihned po odstranění objektu prvku tak, aby seznam nebude pokoušet o přístup k objektům, které již neexistují.

#### <a name="to-delete-all-elements-in-an-array"></a><a name="_core_to_delete_all_elements_in_an_array"></a>Odstranění všech prvků v poli

1. Pomocí `GetSize` a celé číslo index hodnoty iterace prostřednictvím pole.

1. Pomocí operátoru **delete** odstraňte každý prvek, jak je zjištěn v iteraci.

1. Volání `RemoveAll` funkce odebrat všechny prvky z pole po jejich odstranění.

   Kód pro odstranění všech prvků pole je následující:

   [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

Stejně jako v příkladu `RemoveAll` výše, můžete volat odebrat všechny prvky v poli nebo `RemoveAt` odebrat jednotlivý prvek.

#### <a name="to-delete-all-elements-in-a-map"></a><a name="_core_to_delete_all_elements_in_a_map"></a>Odstranění všech prvků v mapě

1. Použijte `GetStartPosition` `GetNextAssoc` a iterate prostřednictvím pole.

1. Pomocí operátoru **delete** odstraňte klíč nebo hodnotu pro každý prvek mapy, jak je zjištěn v iteraci.

1. Volání `RemoveAll` funkce odebrat všechny prvky z mapy poté, co byly odstraněny.

   Kód pro odstranění všech prvků `CMap` kolekce je následující. Každý prvek v mapě má řetězec jako `CPerson` klíč a `CObject`objekt (odvozený z) jako hodnotu.

   [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

Můžete volat `RemoveAll` odebrat všechny prvky `RemoveKey` v mapě nebo odebrat jednotlivý prvek se zadaným klíčem.

## <a name="see-also"></a>Viz také

[Přístup ke všem členům kolekce](../mfc/accessing-all-members-of-a-collection.md)
