---
title: 'Správa paměti: Příklady | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05e2a39f94eeefa264a9e93623f4ff7c6b2f2e91
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080453"
---
# <a name="memory-management-examples"></a>Správa paměti: Příklady

Tento článek popisuje, jak provádí MFC rámec přidělení a přidělení haldy pro všechny tři typické druhy přidělení paměti:

- [Pole bajtů](#_core_allocation_of_an_array_of_bytes)

- [Datová struktura](#_core_allocation_of_a_data_structure)

- [Objekt](#_core_allocation_of_an_object)

##  <a name="_core_allocation_of_an_array_of_bytes"></a> Přidělení pole bajtů

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>Přidělit pole bajtů na rámec

1. Definování pole, jak je znázorněno v následujícím kódu. Pole se automaticky odstraní a jeho paměť uvolněno při ukončení jeho rozsah proměnné pole.

   [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>Přidělení na haldě pole bajtů (nebo jakýkoli primitivní datový typ)

1. Použití **nové** operátorem pomocí syntaxe pole v tomto příkladu:

   [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>Chcete-li uvolnit pole z haldy

1. Použití **odstranit** operátor následujícím způsobem:

   [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]

##  <a name="_core_allocation_of_a_data_structure"></a> Přidělování struktury dat

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>Přidělit do datové struktury v rámci

1. Definujte proměnnou struktury následujícím způsobem:

   [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]

   Paměť obsazena struktury je uvolněn při ukončení její obor.

#### <a name="to-allocate-data-structures-on-the-heap"></a>Přidělit datové struktury v haldě

1. Použití **nové** přidělit datové struktury v haldě a **odstranit** se uvolnit, jak je znázorněno v následujících příkladech:

   [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]

##  <a name="_core_allocation_of_an_object"></a> Přidělení objektu

#### <a name="to-allocate-an-object-on-the-frame"></a>Chcete-li přidělit objekt v rámci

1. Deklarujte objekt takto:

   [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]

   Destruktor objektu je automaticky vyvolána při ukončení objekt její obor.

#### <a name="to-allocate-an-object-on-the-heap"></a>Chcete-li přidělit objekt na haldě

1. Použití **nové** operátor, který vrací ukazatel na objekt, k přidělení objektů na haldě. Použití **odstranit** operátor je odstranit.

   Následující příklady haldy a snímků se předpokládá, že `CPerson` konstruktor nepřijímá žádné argumenty.

   [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]

   Pokud argument `CPerson` konstruktor je ukazatel na **char**, je příkaz pro přidělení rámce:

   [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]

   Příkaz pro přidělení haldy je:

   [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>Viz také

[Správa paměti: Přidělení haldy](../mfc/memory-management-heap-allocation.md)

