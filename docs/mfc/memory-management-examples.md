---
title: 'Správa paměti: Příklady'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], memory allocation
- data structures [MFC]
- arrays [MFC], allocating resources
- objects [MFC], allocating memory
- data structures [MFC], allocating memory
- examples [MFC], memory allocation
- heap allocation [MFC], examples
- memory allocation [MFC], arrays
- MFC, memory management
- struct memory allocation [MFC]
- types [MFC], memory allocation
- memory allocation [MFC], objects
- memory allocation [MFC], examples
- arrays [MFC], memory management
- frame allocation [MFC]
- memory allocation [MFC], data structures
ms.assetid: f10240f8-b698-4c83-9288-97a54318930b
ms.openlocfilehash: 3a1e647175b7b5294e672efbf234e3ae2853e411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367848"
---
# <a name="memory-management-examples"></a>Správa paměti: Příklady

Tento článek popisuje, jak knihovna MFC provádí přidělení rámce a přidělení haldy pro každý ze tří typických druhů přidělení paměti:

- [Pole bajtů](#_core_allocation_of_an_array_of_bytes)

- [Datová struktura](#_core_allocation_of_a_data_structure)

- [Objekt](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a>Přidělení pole bajtů

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>Přidělení pole bajtů v rámečku

1. Definujte pole, jak je znázorněno v následujícím kódu. Pole je automaticky odstraněna a jeho paměť je vyvolána, když proměnná pole ukončí svůj obor.

   [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>Přidělení pole bajtů (nebo jakýkoli primitivní datový typ) na haldě

1. Použijte **nový** operátor se syntaxí pole zobrazenou v tomto příkladu:

   [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>Chcete-li navrátit pole z haldy

1. Pomocí operátoru **delete** postupujte takto:

   [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a>Přidělení datové struktury

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>Přidělení datové struktury v rámci

1. Proměnnou struktury definujte takto:

   [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]

   Paměť obsazená strukturou je vyvolána při ukončení jeho oboru.

#### <a name="to-allocate-data-structures-on-the-heap"></a>Přidělení datových struktur na haldě

1. Nové **new** slouží k přidělení datových struktur na haldě a **odstranění,** abyste je navrátili, jak ukazují následující příklady:

   [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a>Přidělení objektu

#### <a name="to-allocate-an-object-on-the-frame"></a>Přidělení objektu v rámečku

1. Deklarujte objekt takto:

   [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]

   Destruktor objektu je automaticky vyvolán, když objekt ukončí svůj obor.

#### <a name="to-allocate-an-object-on-the-heap"></a>Přidělení objektu na haldě

1. Pomocí **nového** operátoru, který vrací ukazatel na objekt, přidělit objekty na haldě. Pomocí operátoru **delete** je odstraňte.

   Následující příklady haldy a `CPerson` rámce předpokládají, že konstruktor nepřijímá žádné argumenty.

   [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]

   Pokud je argument `CPerson` pro konstruktor ukazovátkem , je příkazem pro přidělení rámce: **char**

   [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]

   Příkaz pro přidělení haldy je:

   [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>Viz také

[Správa paměti: Přidělení haldy](../mfc/memory-management-heap-allocation.md)
