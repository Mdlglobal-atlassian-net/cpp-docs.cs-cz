---
title: Přidělování a uvolňování pro BSTR | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- bstr
dev_langs:
- C++
helpviewer_keywords:
- BSTRs, memory allocation
- memory deallocation, string memory
- memory [C++], releasing
- memory allocation, BSTRs
- memory deallocation, BSTR memory
- strings [C++], releasing
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 355d89a3cb5817cc64512ae885a075bf44ee2a86
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465775"
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>Přidělování a uvolňování pro BSTR
Při vytváření `BSTR`s a předat je mezi objekty modelu COM, je nutné dejte si pozor při zpracování paměti používají, aby se zabránilo nevracení paměti. Když `BSTR` zůstane v rámci rozhraní, je nutné uvolnit jeho paměti až budete hotovi s ním. Nicméně, když `BSTR` předá mimo rozhraní přijímající objektu přebírá odpovědnost za jeho správu paměti.  
  
 Obecně platí, pravidla pro přidělení a uvolnění paměti přidělené `BSTR`s jsou následující:  
  
-   Při volání do funkce, která očekává, že `BSTR` argument, musíte přidělit paměť pro `BSTR` před voláním a vydání později. Příklad:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]  
  
-   Při volání do funkce, která vrátí `BSTR`, je nutné uvolnit řetězec, sami. Příklad:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]  
  
-   Pokud implementujete funkci, která se vrátí `BSTR`, přidělit řetězce, ale neuvolní je. Přijímání funkce uvolní paměť. Příklad:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)   
 [SysAllocString](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-sysallocstring)   
 [SysFreeString](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-sysfreestring)

