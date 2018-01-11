---
title: "Třídy založené na šabloně | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- type-safe collections
- CTypedPtrList class [MFC], template-based classes
- arrays [MFC], classes
- arrays [MFC], pointers
- typed pointers, collections of
- arrays [MFC], template-based
- CArray class [MFC], template-based classes
- simple template-based collections
- simple array collection classes [MFC]
- typed pointers
- collections, typed-pointer
- CList class [MFC], template-based classes
- collection classes [MFC], template-based
- CTypedPtrMap class [MFC], template-based classes
- pointers, collections of typed
- CTypedPtrArray class [MFC], template-based classes
- MFC collection classes [MFC], template-based
- template-based collection classes [MFC]
- simple list collection classes [MFC]
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2beb417bdedab6196ff6d27a387c4b61f083c4ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="template-based-classes"></a>Třídy založené na šablonách
Tento článek vysvětluje typově bezpečné kolekce na základě šablon tříd v prostředí MFC verze 3.0 a novějších. Vytvoření kolekce bezpečného typu pomocí těchto šablon je pohodlnější a pomáhá poskytovat efektivnější než při použití třídy kolekce není založené na šablonách bezpečnost typů.  
  
 MFC predefines dvou kategorií na základě šablon kolekcí:  
  
-   [Jednoduché pole, seznamu a třídy map](#_core_using_simple_array.2c_.list.2c_.and_map_templates)  
  
     `CArray`, `CList`, `CMap`  
  
-   [Pole, seznamy a mapy typované ukazatele](#_core_using_typed.2d.pointer_collection_templates)  
  
     `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`  
  
 Třídy kolekcí jednoduchých jsou odvozeny od třídy `CObject`, takže dědí serializaci, dynamických a další vlastnosti `CObject`. Třídy kolekce typové ukazatel vyžadují zadání odvozujete od třídy, která musí být jeden z předdefinovaných knihovnou MFC, jako například kolekce ukazatele objektu bez šablony `CPtrList` nebo `CPtrArray`. Nové kolekce třídy dědí ze zadané základní třídy a novou třídu členské funkce pomocí zapouzdřené volání na členy základní třídy vynutit zabezpečení typů.  
  
 Další informace o šablonách C++ najdete v tématu [šablony](../cpp/templates-cpp.md) v *referenční příručka jazyka C++*.  
  
##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>Pomocí jednoduchého pole, seznamu a mapy šablony  
 Použití šablon jednoduchá kolekce, musíte vědět, jaký typ dat můžete ukládat do těchto kolekcí a jaké parametry pro použití v deklaracích kolekce.  
  
###  <a name="_core_simple_array_and_list_usage"></a>Jednoduchých polí a seznamu využití  
 Jednoduchých polí a seznamu třídy [carray –](../mfc/reference/carray-class.md) a [CList](../mfc/reference/clist-class.md), trvat dva parametry: *typ* a `ARG_TYPE`. Tyto třídy můžete ukládat všechny datového typu, který určíte v *typ* parametr:  
  
-   Základní C++ datové typy, jako například `int`, `char`, a **float**  
  
-   Třídy a struktury C++  
  
-   Jiné typy, které definujete  
  
 Pro usnadnění práce a efektivitu, můžete použít `ARG_TYPE` parametr k určení typu argumenty funkce. Obvykle můžete zadat `ARG_TYPE` jako odkaz na typ s názvem v *typ* parametr. Příklad:  
  
 [!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]  
  
 V prvním příkladu deklaruje kolekci pole `myArray`, který obsahuje `int`s. V druhém příkladu deklaruje kolekci seznamu `myList`, který ukládá `CPerson` objekty. Některé členské funkce tříd kolekce trvat argumenty, jejichž typ je zadána `ARG_TYPE` parametr šablony. Například **přidat** funkce člena třídy `CArray` trvá `ARG_TYPE` argument:  
  
 [!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]  
  
###  <a name="_core_simple_map_usage"></a>Použití jednoduché mapy  
 Třída jednoduchých mapy [CMap](../mfc/reference/cmap-class.md), používá čtyři parametry: *klíč*, `ARG_KEY`, *hodnotu*, a `ARG_VALUE`. Stejně jako pole a seznamu třídy můžete uložit třídy map jakéhokoli datového typu. Na rozdíl od poli a seznamy, které je index a řazení dat uložených mapy přidružit klíče a hodnoty: přístup hodnotou uloženou v mapu zadáním přidružené klíče hodnotu. *Klíč* parametr určuje datový typ klíče používané pro přístup k datům uloženým v mapě. Pokud typ *klíč* je struktura nebo třídy, `ARG_KEY` parametr je obvykle odkaz na typ určený v *klíč*. *Hodnotu* parametr určuje typ položky uložené v mapě. Pokud typ `ARG_VALUE` je struktura nebo třídy, `ARG_VALUE` parametr je obvykle odkaz na typ určený v *hodnotu*. Příklad:  
  
 [!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]  
  
 První příklad úložiště `MY_STRUCT` hodnoty, je pomocí přistupuje `int` klíče a vrátí přístup `MY_STRUCT` položky odkazem. Druhý příklad úložiště `CPerson` hodnoty, je pomocí přistupuje `CString` klíčů a vrátí odkazy na používaná položky. V tomto příkladu může představovat jednoduchý adresář, ve kterém můžete vyhledat osob podle příjmení.  
  
 Protože *klíč* parametr je typu `CString` a *key_type –* parametr je typu `LPCSTR`, klíče jsou uložené v mapě jako položky typu `CString` ale se odkazuje v Funkce, jako `SetAt` prostřednictvím ukazatele typu `LPCSTR`. Příklad:  
  
 [!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]  
  
##  <a name="_core_using_typed.2d.pointer_collection_templates"></a>Pomocí šablon ukazatel s typem kolekce  
 Použití šablon ukazatel s typem kolekce, musíte vědět, jaké druhy dat můžete ukládat do těchto kolekcí a jaké parametry pro použití v deklaracích kolekce.  
  
###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a>Ukazatel s typem pole a používání seznamu  
 Ukazatel s typem pole a třídy seznamu [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) a [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md), trvat dva parametry: `BASE_CLASS` a *typu*. Tyto třídy můžete ukládat všechny datového typu, který určíte v *typ* parametr. Jsou odvozené z jednoho typu tříd kolekce objektu bez šablony, které jsou uloženy ukazatele; Zadejte této základní třídy v `BASE_CLASS`. Pro pole, použijte buď `CObArray` nebo `CPtrArray`. Pro seznamy, použijte buď `CObList` nebo `CPtrList`.  
  
 Ve skutečnosti, že po deklarování kolekce na základě `CObList`, nová třída nejen dědí členy základní třídy, ale také deklaruje číslo člena bezpečnost typů další funkce a operátory, které pomáhají zajistit bezpečnost typů zapouzdřením volání na členy základní třídy. Tyto encapsulations spravovat všechny nezbytné typ převodu. Příklad:  
  
 [!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]  
  
 V prvním příkladu deklaruje ukazatel s typem pole, `myArray`, odvozené z `CObArray`. Pole ukládá a vrátí ukazatele na `CPerson` objekty (kde `CPerson` je třída odvozená z `CObject`). Můžete volat žádný `CObArray` – členská funkce, nebo můžete volat nový typ safe `GetAt` a `ElementAt` funkce nebo použijte typ safe **[]** operátor.  
  
 V druhém příkladu deklaruje seznam ukazatel s typem `myList`, odvozené z `CPtrList`. V seznamu ukládá a vrátí ukazatele na `MY_STRUCT` objekty. Na základě třídy `CPtrList` slouží k ukládání ukazatelé na objekty není odvozen od `CObject`. `CTypedPtrList`obsahuje počet bezpečnost typů členské funkce: `GetHead`, `GetTail`, `RemoveHead`, `RemoveTail`, `GetNext`, `GetPrev`, a `GetAt`.  
  
###  <a name="_core_typed.2d.pointer_map_usage"></a>Použití Map typované ukazatele  
 Třídy map ukazatel s typem [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), přijímá tři parametry: `BASE_CLASS`, *klíč*, a *hodnotu*. `BASE_CLASS` Parametr určuje třídu, ze které jsou odvozeny nová třída: `CMapPtrToWord`, `CMapPtrToPtr`, `CMapStringToPtr`, `CMapWordToPtr`, `CMapStringToOb`a tak dále. *KLÍČ* je podobná *klíč* v `CMap`: Určuje typ klíč používaný k vyhledávání. *Hodnota* je podobná *hodnotu* v `CMap`: Určuje typ objektu, které jsou uložené v mapě. Příklad:  
  
 [!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]  
  
 V prvním příkladu je do mapy na základě **CMapPtrToPt**r – používá `CString` klíče, které jsou namapované na ukazatele na `MY_STRUCT`. Můžete vyhledat uložené ukazatel voláním bezpečnost typů `Lookup` – členská funkce. Můžete použít **[]** operátor k vyhledání uložené ukazatel a přidejte ji, pokud není nalezen. A můžete iterovat mapy pomocí bezpečnost typů `GetNextAssoc` funkce. Můžete také volat jiné členské funkce třídy `CMapPtrToPtr`.  
  
 V druhém příkladu je do mapy na základě **CMapStringToO**b – používá řetězcových klíčů, které jsou namapované na uložené ukazatele na `CMyObject` objekty. Můžete použít stejné členy bezpečnost typů popsané v předchozím odstavci, nebo můžete volat členy třídy `CMapStringToOb`.  
  
> [!NOTE]
>  Pokud zadáte **– třída** nebo `struct` zadejte *hodnotu* parametr, nikoli ukazatel nebo odkaz na typ, třídu nebo strukturu musí mít konstruktor kopírování.  
  
 Další informace najdete v tématu [jak typově bezpečné kolekce](../mfc/how-to-make-a-type-safe-collection.md).  
  
## <a name="see-also"></a>Viz také  
 [Kolekce](../mfc/collections.md)

