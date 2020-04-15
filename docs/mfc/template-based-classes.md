---
title: Třídy založené na šablonách
ms.date: 11/04/2016
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
ms.openlocfilehash: 29f5f815b62835aedbca1f79b797f826ea53d83b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370460"
---
# <a name="template-based-classes"></a>Třídy založené na šablonách

Tento článek vysvětluje třídy kolekce založené na šablonách v knihovně MFC verze 3.0 a novějších. Použití těchto šablon k vytvoření kolekcí bezpečných pro daný typ je pohodlnější a pomáhá zajistit bezpečnost typů efektivněji než pomocí tříd kolekce, které nejsou založeny na šablonách.

Knihovna MFC předdefinuje dvě kategorie kolekcí založených na šablonách:

- [Jednoduché třídy polí, seznamu a mapy](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Pole, seznamy a mapy zadaných ukazatelů](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Jednoduché třídy kolekce jsou všechny `CObject`odvozeny z třídy , takže dědí `CObject`serializaci, dynamické vytváření a další vlastnosti . Třídy kolekce zadaného ukazatele vyžadují zadání třídy, ze které je odvozeno – což musí být `CPtrList` jedna `CPtrArray`z kolekcí nepředdefinovaných knihovnou MFC, například nebo . Vaše nová třída kolekce dědí ze zadané základní třídy a členské funkce nové třídy používají zapouzdřená volání členů základní třídy k vynucení bezpečnosti typů.

For more information about C++ templates, see [Templates](../cpp/templates-cpp.md) in the *C++ Language Reference*.

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>Použití jednoduchých šablon polí, seznamů a map

Chcete-li použít jednoduché šablony kolekce, musíte vědět, jaký druh dat můžete uložit v těchto kolekcích a jaké parametry použít v deklaracích kolekce.

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a>Jednoduché použití pole a seznamu

Jednoduché třídy pole a seznamu, [CArray](../mfc/reference/carray-class.md) a [CList](../mfc/reference/clist-class.md) `ARG_TYPE`, mají dva parametry: *TYPE* a . Tyto třídy mohou ukládat libovolný datový typ, který zadáte v parametru *TYPE:*

- Základní datové typy jazyka C++, například **int**, **char**a **float**

- Struktury a třídy Jazyka C++

- Další typy, které definujete

Pro pohodlí a efektivitu můžete použít parametr *ARG_TYPE* k určení typu argumentů funkce. Obvykle zadáte *ARG_TYPE* jako odkaz na typ, který jste pojmenovali v parametru *TYPE.* Příklad:

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

První příklad deklaruje `myArray`kolekci pole , která obsahuje **int**s. Druhý příklad deklaruje `myList`kolekci `CPerson` seznamu , která ukládá objekty. Některé členské funkce tříd kolekce přebírají argumenty, jejichž typ je určen parametrem *ARG_TYPE* šablony. Například `Add` členská funkce `CArray` třídy přebírá *ARG_TYPE* argument:

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a>Jednoduché využití mapy

Jednoduchá třída [mapy, CMap](../mfc/reference/cmap-class.md), má čtyři parametry: *KEY*, *ARG_KEY*, *VALUE*a *ARG_VALUE*. Stejně jako třídy pole a seznamu mohou třídy mapy ukládat libovolný datový typ. Na rozdíl od polí a seznamů, které indexují a objednávají data, která ukládají, mapy přidružují klíče a hodnoty: K hodnotě uložené v mapě máte přístup zadáním přidruženého klíče hodnoty. Parametr *KEY* určuje datový typ klíčů použitých pro přístup k datům uloženým v mapě. Pokud je typem *key* struktura nebo třída, *ARG_KEY* parametr je obvykle odkaz na typ zadaný v *klíči*. Parametr *VALUE* určuje typ položek uložených v mapě. Pokud je typem *ARG_VALUE* struktura nebo třída, *ARG_VALUE* parametr je obvykle odkaz na typ zadaný v *poli HODNOTA*. Příklad:

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

První příklad `MY_STRUCT` ukládá hodnoty, přistupuje k nim `MY_STRUCT` **pomocí int** klíče a vrátí přístup k položkám odkazem. Druhý příklad `CPerson` ukládá hodnoty, přistupuje k nim pomocí `CString` klíčů a vrací odkazy na přístupné položky. Tento příklad může představovat jednoduchý adresář, ve kterém vyhledáte osoby podle příjmení.

Vzhledem k *tomu, že parametr KEY* je typu `CString` a *KEY_TYPE* parametr je typu `LPCSTR`, jsou klíče uloženy v mapě jako položky typu, `CString` ale jsou odkazovány ve funkcích, jako `SetAt` je například prostřednictvím ukazatelů typu `LPCSTR`. Příklad:

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a>Použití šablon kolekce typed-pointer

Chcete-li použít šablony kolekce zadaného ukazatele, musíte vědět, jaké druhy dat můžete uložit v těchto kolekcích a jaké parametry použít v deklaracích kolekce.

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a>Použití pole a seznamu typed-pointer

Třídy pole a seznam typed-pointer, [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) a [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md), mají dva parametry: *BASE_CLASS* a *TYPE*. Tyto třídy můžete uložit libovolný datový typ, který zadáte v *type* parametr. Jsou odvozeny z jedné z tříd kolekce nontemplate, která ukládá ukazatele; tuto základní třídu zadáte v *BASE_CLASS*. Pro pole použijte `CObArray` buď `CPtrArray`nebo . Pro seznamy `CObList` použijte `CPtrList`buď nebo .

Ve skutečnosti při deklarování kolekce `CObList`na základě, řekněme , nová třída nejen dědí členy své základní třídy, ale také deklaruje řadu dalších funkcí typu bezpečné členy a operátory, které pomáhají poskytovat bezpečnost typů zapouzdření volání členy základní třídy. Tyto zapouzdření spravovat všechny potřebné převod typu. Příklad:

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

První příklad deklaruje pole `myArray`typed-pointer `CObArray`, odvozené z . Pole ukládá a vrací `CPerson` ukazatele na `CPerson` objekty (kde `CObject`je třída odvozená od). Můžete volat `CObArray` libovolnou člennou funkci nebo můžete `GetAt` volat `ElementAt` nový typ-safe a funkce nebo použít typově bezpečný **[ ]** operátor.

Druhý příklad deklaruje seznam `myList`typed-pointer `CPtrList`, odvozený z . Seznam ukládá a vrací `MY_STRUCT` ukazatele na objekty. Třída založená `CPtrList` na slouží k ukládání ukazatelů na objekty, které nejsou odvozeny od `CObject`. `CTypedPtrList`má řadu typově bezpečných `GetHead`členských `GetTail`funkcí: `GetNext` `GetPrev`, `GetAt`, `RemoveHead`, `RemoveTail`, , a .

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a>Použití mapy s typem ukazatele

Třída mapy typed-pointer, [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), má tři parametry: *BASE_CLASS*, *KEY*a *VALUE*. Parametr *BASE_CLASS* určuje třídu, ze které má `CMapPtrToWord` `CMapPtrToPtr`být `CMapStringToPtr` `CMapWordToPtr`odvozena nová třída: , , , `CMapStringToOb`, a tak dále. *KEY* je analogický `CMap` *klíč* v : Určuje typ klíče používaného pro vyhledávání. *HODNOTA* je obdobou *VALUE* VALUE `CMap`v : Určuje typ objektu uloženého v mapě. Příklad:

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

Prvním příkladem je mapa `CMapPtrToPtr` založená `CString` na – používá klávesy mapované na ukazatele na `MY_STRUCT`. Uložený ukazatel můžete vyhledat voláním členské `Lookup` funkce bezpečného typu. Pomocí operátoru **[ ]** můžete vyhledat uložený ukazatel a přidat jej, pokud není nalezen. A můžete iterate mapy pomocí funkce `GetNextAssoc` typu bezpečné. Můžete také volat další členské `CMapPtrToPtr`funkce třídy .

Druhým příkladem je mapa `CMapStringToOb` založená na – používá řetězcové `CMyObject` klávesy mapované na uložené ukazatele na objekty. Můžete použít stejné členy bezpečné typ popsané v předchozím odstavci, nebo `CMapStringToOb`můžete volat členy třídy .

> [!NOTE]
> Pokud zadáte typ **třídy** nebo **struktury** pro parametr *VALUE,* nikoli ukazatel nebo odkaz na typ, třída nebo struktura musí mít konstruktor copy.

Další informace naleznete v [tématu Jak vytvořit kolekci bezpečného pro daný typ](../mfc/how-to-make-a-type-safe-collection.md).

## <a name="see-also"></a>Viz také

[Kolekce](../mfc/collections.md)
