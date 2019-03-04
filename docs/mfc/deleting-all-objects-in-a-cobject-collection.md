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
ms.openlocfilehash: 95d4cec61b230df5a019655617a25b1dc309cde4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257966"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Smazání všech objektů v kolekcích CObject

Tento článek vysvětluje, jak odstranit všechny objekty v kolekci (bez odstranění samotného objektu kolekce).

Chcete-li odstranit všechny objekty v kolekci `CObject`s (nebo objekty odvozené z `CObject`), použijte jednu z iterace technik popsaných v článku [přístup ke všem členům kolekce](../mfc/accessing-all-members-of-a-collection.md) odstranit jednotlivé objekty v Zapněte.

> [!CAUTION]
>  Je možné sdílet objektů v kolekcích. To znamená, že kolekce uchovává ukazatel na objekt, ale jiné části programu, může mít také odkazy na stejný objekt. Musíte být pozor, abyste odstranění objektu, který je sdílen, dokud nedokončí všechny části pomocí objektu.

Tento článek ukazuje, jak odstranit objekty:

- [Seznam](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [Pole](#_core_to_delete_all_elements_in_an_array)

- [Mapy](#_core_to_delete_all_elements_in_a_map)

#### <a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>  Chcete-li odstranit všechny objekty do seznamu ukazatele na třídy CObject

1. Použití `GetHeadPosition` a `GetNext` k iteraci v rámci seznamu.

1. Použití **odstranit** operátor každý objekt odstranit, protože se zjistil v iteraci.

1. Volání `RemoveAll` funkce odeberte všechny prvky ze seznamu po odstranění objekty přidružené k těmto prvkům.

Následující příklad ukazuje, jak odstranit všechny objekty ze seznamu `CPerson` objekty. Každý objekt v seznamu je ukazatel `CPerson` objekt, který byl původně přidělen na haldě.

[!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

Poslední volání funkce `RemoveAll`, je členská funkce seznamu, která odebere všechny prvky ze seznamu. Členská funkce `RemoveAt` odebere jeden element.

Všimněte si, že rozdíl mezi odstranění prvku objektu a odebrání samotného elementu. Odstranění prvku ze seznamu pouze odebere odkaz v seznamu na objekt. Objekt v paměti stále existuje. Při odstranění objektu se přestane existovat a jeho paměti je uvolněn. Proto je potřeba odebrat element ihned po elementu objekt byl smazán tak, aby v seznamu se nebude pokoušet přístup k objektům, které už existují.

#### <a name="_core_to_delete_all_elements_in_an_array"></a>  Chcete-li odstranit všechny prvky v poli

1. Použití `GetSize` a celočíselné hodnoty indexu pro iteraci polem.

1. Použití **odstranit** operátor odstranit každý prvek, protože se zjistil v iteraci.

1. Volání `RemoveAll` funkce odeberte všechny prvky z pole poté, co byla odstraněna.

   Kód k odstranění všech prvků pole je následujícím způsobem:

   [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

Jak se v seznamu příkladu výše, můžete volat `RemoveAll` odebrat všechny elementy v matici nebo `RemoveAt` odebrat jednotlivý prvek.

#### <a name="_core_to_delete_all_elements_in_a_map"></a> Chcete-li odstranit všechny elementy v objektu map

1. Použití `GetStartPosition` a `GetNextAssoc` k iteraci v rámci pole.

1. Použití **odstranit** operátor odstranit klíč a hodnotu pro každý prvek na mapě, podle dochází v iteraci.

1. Volání `RemoveAll` funkce odeberte všechny prvky z mapy po se odstranily.

   Kód k odstranění všech prvků `CMap` kolekce je následujícím způsobem. Každý prvek v mapě má řetězec jako klíč a `CPerson` objektu (odvozený od `CObject`) jako hodnotu.

   [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

Můžete volat `RemoveAll` odebrat všechny elementy v objektu map nebo `RemoveKey` odebrat jednotlivý element se zadaným klíčem.

## <a name="see-also"></a>Viz také:

[Přístup ke všem členům kolekce](../mfc/accessing-all-members-of-a-collection.md)
