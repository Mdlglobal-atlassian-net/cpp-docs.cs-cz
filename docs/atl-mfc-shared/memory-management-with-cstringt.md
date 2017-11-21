---
title: "Správa paměti s CStringT | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringT
- ATL::CStringT
- ATL.CStringT
dev_langs: C++
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5f36e27a536ce8983baaca594b5768479b16a74d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="memory-management-with-cstringt"></a>Správa paměti s CStringT
Třída [CStringT](../atl-mfc-shared/reference/cstringt-class.md) je třída šablony používá k manipulaci s proměnlivou délkou znakových řetězců. Paměť pro uložení tyto řetězce je přidělené a vydání prostřednictvím objekt manager řetězec, který je spojené s každou instanci `CStringT`. MFC a knihovna ATL zadejte výchozí instancemi `CStringT`, volané `CString`, `CStringA`, a `CStringW`, který manipulaci s řetězci různých znakových typů. Tyto typy znaků jsou typu **Tchar –**, `char`, a `wchar_t`, v uvedeném pořadí. Tyto typy výchozí řetězec pomocí Správce řetězec, který přidělí paměť z haldy procesu (v ATL) nebo CRT haldy (v prostředí MFC). Pro typické aplikace je toto schéma přidělení paměti dostačující. Ale pro provedení náročné kód pomocí řetězce (nebo s více vlákny kódu), které správce paměti výchozí nemusí mít optimální. Toto téma popisuje, jak změnit výchozí chování správy paměti z `CStringT`, vytváření alokátorů speciálně optimalizovaná pro úlohy po ruce.  
  
-   [Implementace nástroje vlastní řetězec Manager (základní metoda)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)  
  
-   [Předcházení kolizí haldy](../atl-mfc-shared/avoidance-of-heap-contention.md)  
  
-   [Implementace nástroje vlastní řetězec Manager (rozšířené metoda)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)  
  
-   [CFixedStringT: Příklad nástroje vlastní řetězec Manager](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CustomString](../visual-cpp-samples.md)

