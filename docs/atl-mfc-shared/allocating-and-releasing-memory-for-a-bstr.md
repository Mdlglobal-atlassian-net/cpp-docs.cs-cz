---
title: Přidělování a uvolňování paměti pro BSTR
ms.date: 11/04/2016
f1_keywords:
- bstr
helpviewer_keywords:
- BSTRs, memory allocation
- memory deallocation, string memory
- memory [C++], releasing
- memory allocation, BSTRs
- memory deallocation, BSTR memory
- strings [C++], releasing
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
ms.openlocfilehash: a7a82acff959d18dcadd3a2c8516a20d60a617d3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491402"
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>Přidělování a uvolňování paměti pro BSTR

Když vytváříte `BSTR`s a předáváte je mezi objekty COM, musíte se postarat o ošetření paměti, kterou používají, aby se předešlo nevracení paměti. `BSTR` Když zůstane v rámci rozhraní, musíte po dokončení práce uvolnit jeho paměť. Když se ale z `BSTR` rozhraní předává, přijímající objekt odpovídá jeho správě paměti.

Obecně platí, že pravidla pro přidělování a uvolňování paměti přidělená pro `BSTR`s jsou následující:

- Při volání funkce, která očekává `BSTR` argument, je nutné přidělit paměť `BSTR` pro před voláním a následně uvolnit. Příklad:

   [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]

- Při volání funkce, která vrací `BSTR`, je nutné řetězec uvolnit sami. Příklad:

   [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]

- Při implementaci funkce, která vrací `BSTR`, přidělte řetězec, ale neuvolní ho. Přijímání funkce uvolní paměť. Příklad:

   [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]

## <a name="see-also"></a>Viz také:

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)<br/>
[Případě](/windows/win32/api/oleauto/nf-oleauto-sysallocstring)<br/>
[SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)
