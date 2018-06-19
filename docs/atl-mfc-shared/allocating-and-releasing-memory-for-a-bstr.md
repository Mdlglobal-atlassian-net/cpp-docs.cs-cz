---
title: Přidělování a uvolňování paměti pro BSTR | Microsoft Docs
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
ms.openlocfilehash: 46ab5ae9d6f0bfa98231cbc41aa4ae0d10b89537
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358322"
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>Přidělování a uvolňování paměti pro BSTR
Při vytváření `BSTR`s a předat je mezi objekty modelu COM, musí postará v považuje paměti používají, aby se zabránilo nevracení paměti. Když `BSTR` zůstane v rámci rozhraní, je nutné uvolnit jeho paměť až skončíte s ním. Ale když `BSTR` předává mimo rozhraní, přebírá objekt přijímající odpovědnost za jeho správa paměti.  
  
 Obecně platí, pravidla pro přidělování a uvolňování paměti přidělené `BSTR`s jsou následující:  
  
-   Při volání do funkce, která očekává `BSTR` argument, musíte přidělit paměť pro `BSTR` před voláním a později ji uvolnit. Příklad:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]  
  
-   Při volání do funkce vracející `BSTR`, je nutné uvolnit řetězec, sami. Příklad:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]  
  
-   Při implementaci funkci, která vrátí `BSTR`, přidělit řetězec, ale není volné. Přijímací funkce uvolní paměť. Příklad:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Řetězce (ATL a MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)   
 [SysAllocString](https://msdn.microsoft.com/library/windows/desktop/ms221458.aspx)   
 [SysFreeString](https://msdn.microsoft.com/library/windows/desktop/ms221481.aspx)

