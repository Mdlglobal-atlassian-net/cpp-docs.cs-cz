---
title: 'Správa paměti: Příklady | Microsoft Docs'
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
ms.openlocfilehash: 84bc2ce7c084f2951d63eee546df3bf70a2ba1fe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347188"
---
# <a name="memory-management-examples"></a>Správa paměti: Příklady
Tento článek popisuje, jak MFC provádí rámce přidělení a přidělení haldy pro každou z typických tři druhy přidělení paměti:  
  
-   [Pole bajtů](#_core_allocation_of_an_array_of_bytes)  
  
-   [Datová struktura](#_core_allocation_of_a_data_structure)  
  
-   [Objekt](#_core_allocation_of_an_object)  
  
##  <a name="_core_allocation_of_an_array_of_bytes"></a> Přidělení pole bajtů  
  
#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>Přidělit pole bajtů na rámečku  
  
1.  Pole definujte, jak je uvedeno v následujícím kódu. Pole se automaticky odstraní a jeho paměť uvolnit při proměnné pole ukončí její obor.  
  
     [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]  
  
#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>Přidělit pole bajtů (nebo kterýkoli typ primitivní datové) v haldě  
  
1.  Použití **nové** operátor s pole syntaxi uvedenou v tomto příkladu:  
  
     [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]  
  
#### <a name="to-deallocate-the-arrays-from-the-heap"></a>Chcete-li navrátit pole z haldy  
  
1.  Použití **odstranit** operátor následujícím způsobem:  
  
     [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]  
  
##  <a name="_core_allocation_of_a_data_structure"></a> Přidělení datová struktura  
  
#### <a name="to-allocate-a-data-structure-on-the-frame"></a>Přidělit datová struktura rámec  
  
1.  Definujte proměnnou struktura takto:  
  
     [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]  
  
     Paměť obsazena strukturu je uvolnit, když ho ukončí její obor.  
  
#### <a name="to-allocate-data-structures-on-the-heap"></a>Přidělit datové struktury v haldě  
  
1.  Použití **nové** přidělit datové struktury v haldě a **odstranit** se zrušit přidělení, jak ukazují následující příklady:  
  
     [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]  
  
##  <a name="_core_allocation_of_an_object"></a> Přidělení objektu  
  
#### <a name="to-allocate-an-object-on-the-frame"></a>Přidělit objektu na rámečku  
  
1.  Objekt deklarujte následujícím způsobem:  
  
     [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]  
  
     Destruktoru objektu se automaticky vyvolá, když objekt ukončí její obor.  
  
#### <a name="to-allocate-an-object-on-the-heap"></a>Přidělit objekt v haldě  
  
1.  Použití **nové** operátor, který vrací ukazatel na objekt, přidělit objekty v haldě. Použití **odstranit** operátor je odstranit.  
  
     Následující příklady haldy a rámce předpokládat, že `CPerson` konstruktor nezadávaly žádné argumenty.  
  
     [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]  
  
     Pokud argument pro `CPerson` konstruktor je ukazatel na `char`, je příkaz pro přidělení rámce:  
  
     [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]  
  
     Příkaz pro přidělení haldy je:  
  
     [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Správa paměti: Přidělení haldy](../mfc/memory-management-heap-allocation.md)

