---
title: Třídy založené na šablonách | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b972d4552a8e41ca0dcea4ef57d48ef161ea35b9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069227"
---
# <a name="template-based-classes"></a>Třídy založené na šablonách

Tento článek vysvětluje třídy kolekce založené na šablonách zajišťující bezpečnost typů v knihovně MFC verze 3.0 nebo novější. Použití tyto šablony k vytvoření typově bezpečné kolekce je pohodlnější a pomáhá zajistit bezpečnost typů efektivnější než při použití třídy kolekcí není založen na šablony.

MFC predefines dvě kategorie založené na šablonách kolekce:

- [Jednoduché polí, seznamů a hotové třídy map](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Pole, seznamy a mapy typované ukazatele](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Třídy kolekcí jednoduchých jsou odvozeny z třídy `CObject`, takže dědí serializace, dynamické vytváření a další vlastnosti `CObject`. Třídy kolekcí typované ukazatele vyžadují zadání odvozujete od třídy, která musí být jedna z kolekcí ukazatel nešablonových předdefinovány knihovnou MFC, například `CPtrList` nebo `CPtrArray`. Nové třídy kolekce dědí z zadaná základní třída a členské funkce nové třídy slouží k vynucení bezpečnost typů zapouzdřený volání na členy základní třídy.

Další informace o šablonách C++ naleznete v tématu [šablony](../cpp/templates-cpp.md) v *referenční dokumentace jazyka C++*.

##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> Pomocí jednoduchých pole, seznamu a mapy šablon

Pokud chcete použít jednoduché kolekce šablon, budete muset vědět, jaká data můžete ukládat v těchto kolekcích a jaké parametry se mají použít v deklaracích kolekce.

###  <a name="_core_simple_array_and_list_usage"></a> Jednoduchých polí a seznam využití

Jednoduchých polí a seznam tříd [carray –](../mfc/reference/carray-class.md) a [CList –](../mfc/reference/clist-class.md), přebírají dva parametry: *typ* a `ARG_TYPE`. Tyto třídy můžete ukládat libovolného datového typu, který zadáte *typ* parametr:

- Základní C++ datové typy, jako například **int**, **char**, a **plovoucí desetinnou čárkou**

- Třídy a struktury jazyka C++

- Jiné typy, které definujete

Pro usnadnění práce a efektivitu, můžete použít *ARG_TYPE* parametr k určení typu argumentů funkce. Obvykle stanovíte *ARG_TYPE* jako odkaz na typ s názvem v *typ* parametru. Příklad:

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

První příklad deklaruje kolekci pole `myArray`, který obsahuje **int**s. Druhý příklad deklaruje kolekci seznamů `myList`, který ukládá `CPerson` objekty. Určité členské funkce tříd kolekce přijímají argumenty, jehož typ je určená *ARG_TYPE* parametr šablony. Například `Add` členské funkce třídy `CArray` přebírá *ARG_TYPE* argument:

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

###  <a name="_core_simple_map_usage"></a> Využití jednoduché mapy

Třída jednoduchých map [CMap](../mfc/reference/cmap-class.md), přebírá čtyři parametry: *klíč*, *ARG_KEY*, *hodnotu*, a *ARG_VALUE*. Stejně jako pole a seznamu třídy může ukládat třídy map libovolného datového typu. Na rozdíl od pole a seznamy, které indexování a řazení dat jsou v nich uložené, mapy přidružení klíče a hodnoty: přistupovat k hodnotě zadáním hodnoty přidružený klíč uložený v objektu map. *Klíč* parametr určuje datový typ klíče používané pro přístup k datům uloženým v objektu map. Pokud typ *klíč* je struktury nebo třídy, *ARG_KEY* parametr je obvykle odkaz na typ určený v *klíč*. *Hodnotu* parametr určuje typ položky uložené v objektu map. Pokud typ *ARG_VALUE* je struktury nebo třídy, *ARG_VALUE* parametr je obvykle odkaz na typ určený v *hodnota*. Příklad:

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

První příklad uloží `MY_STRUCT` hodnoty, přistupuje k je podle **int** klíče a vrátí přistupovat `MY_STRUCT` položky podle odkazu. Druhý příklad uloží `CPerson` hodnoty, přistupuje k je podle `CString` klíče a vrátí odkazy na použitých položek. V tomto příkladu může představovat jednoduché adresu adresáře, ve kterém můžete vyhledat osob podle příjmení.

Protože *klíč* je parametr typu `CString` a *KEY_TYPE* je parametr typu `LPCSTR`, klíče jsou uložené v mapě jako položky typu `CString` , ale jsou odkazovány v Funkce, jako například `SetAt` prostřednictvím ukazatele typu `LPCSTR`. Příklad:

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

##  <a name="_core_using_typed.2d.pointer_collection_templates"></a> Použití šablon zadán ukazatel kolekce

Použití šablon zadán ukazatel kolekce, je potřeba vědět, jaký druh dat, která může ukládat do těchto kolekcí a jaké parametry se mají použít v deklaracích kolekce.

###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a> Zadán ukazatel pole a používání seznamu

Třídy seznamu, pole zadán ukazatel a [ctypedptrarray –](../mfc/reference/ctypedptrarray-class.md) a [ctypedptrlist –](../mfc/reference/ctypedptrlist-class.md), přebírají dva parametry: *$base_class* a *typ*. Tyto třídy můžete ukládat libovolného datového typu, který zadáte *typ* parametru. Jsou odvozeny z jednoho objektu bez šablony tříd kolekcí, které ukládá ukazatele; Zadejte tento základní třídy v *$base_class*. Pro pole, použijte buď `CObArray` nebo `CPtrArray`. Pro seznamy, použijte buď `CObList` nebo `CPtrList`.

V důsledku toho při deklaraci na základě kolekce, Řekněme, že `CObList`, nová třída nejen dědí členy své základní třídy, ale také deklaruje řadu dalšího člena typově bezpečné funkce a operátory, které vám pomůžou zajistit bezpečnost typů zapouzdřením volání na členy základní třídy. Tyto encapsulations spravovat všechny nezbytné převodů. Příklad:

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

První příklad deklaruje pole s typem ukazatele `myArray`odvozenou z `CObArray`. Pole jsou uloženy a vrací ukazatele na `CPerson` objekty (kde `CPerson` je třída odvozena z `CObject`). Vám může vrstva volat všechny `CObArray` členská funkce, nebo může volat nové bezpečnost typů `GetAt` a `ElementAt` funkce nebo použijte zajišťující bezpečnost typů **[] č.** operátor.

Druhý příklad deklaruje seznam zadán ukazatel `myList`odvozenou z `CPtrList`. Seznam ukládá a vrací ukazatele na `MY_STRUCT` objekty. Na základě třídy `CPtrList` slouží k ukládání ukazatelů na objekty není odvozeno od `CObject`. `CTypedPtrList` má řadu zajišťující bezpečnost typů členské funkce: `GetHead`, `GetTail`, `RemoveHead`, `RemoveTail`, `GetNext`, `GetPrev`, a `GetAt`.

###  <a name="_core_typed.2d.pointer_map_usage"></a> Využití zadán ukazatel mapy

Třída map zadán ukazatel [ctypedptrmap –](../mfc/reference/ctypedptrmap-class.md), přijímá tři parametry: *$base_class*, *klíč*, a *hodnota*. *$Base_class* parametr určuje třídu, ze kterého se má odvodit novou třídu: `CMapPtrToWord`, `CMapPtrToPtr`, `CMapStringToPtr`, `CMapWordToPtr`, `CMapStringToOb`, a tak dále. *KLÍČ* je obdobou *klíč* v `CMap`: Určuje typ klíče, použít pro vyhledávání. *Hodnota* je obdobou *hodnotu* v `CMap`: Určuje typ objektu uložená v objektu map. Příklad:

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

První příklad je do mapy na základě `CMapPtrToPtr` – používá `CString` klíče, které jsou mapovány na ukazatele na `MY_STRUCT`. Můžete vyhledat uložený ukazatel voláním bezpečnost typů `Lookup` členskou funkci. Můžete použít **[] č.** operátor k vyhledání uložený ukazatel a přidejte ji, pokud není nalezen. A můžete postup opakovat mapy pomocí zajišťující bezpečnost typů `GetNextAssoc` funkce. Můžete také volat ostatní členské funkce třídy `CMapPtrToPtr`.

Druhý příklad je do mapy na základě `CMapStringToOb` – používá řetězec klíčů mapována na uloženou ukazatele na `CMyObject` objekty. Můžete použít stejné členy zajišťující bezpečnost typů je popsáno v předchozím odstavci, nebo můžete volat členy třídy `CMapStringToOb`.

> [!NOTE]
>  Pokud zadáte **třídy** nebo **– struktura** zadejte *hodnotu* parametr, nikoli ukazatel nebo odkaz na typ třídy nebo struktury, musí mít kopírovací konstruktor.

Další informace najdete v tématu [jak typově bezpečné kolekce](../mfc/how-to-make-a-type-safe-collection.md).

## <a name="see-also"></a>Viz také

[Kolekce](../mfc/collections.md)

