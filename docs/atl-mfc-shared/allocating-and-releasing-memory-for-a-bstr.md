---
title: Přidělování a uvolňování pro BSTR
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
ms.openlocfilehash: 5d21134b85013f9a8ae508590f1a8db0c2e7a7e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668569"
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>Přidělování a uvolňování pro BSTR

Při vytváření `BSTR`s a předat je mezi objekty modelu COM, je nutné dejte si pozor při zpracování paměti používají, aby se zabránilo nevracení paměti. Když `BSTR` zůstane v rámci rozhraní, je nutné uvolnit jeho paměti až budete hotovi s ním. Nicméně, když `BSTR` předá mimo rozhraní přijímající objektu přebírá odpovědnost za jeho správu paměti.

Obecně platí, pravidla pro přidělení a uvolnění paměti přidělené `BSTR`s jsou následující:

- Při volání do funkce, která očekává, že `BSTR` argument, musíte přidělit paměť pro `BSTR` před voláním a vydání později. Příklad:

   [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]

- Při volání do funkce, která vrátí `BSTR`, je nutné uvolnit řetězec, sami. Příklad:

   [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]

- Pokud implementujete funkci, která se vrátí `BSTR`, přidělit řetězce, ale neuvolní je. Přijímání funkce uvolní paměť. Příklad:

   [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]

## <a name="see-also"></a>Viz také

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)<br/>
[SysAllocString](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-sysallocstring)<br/>
[SysFreeString](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-sysfreestring)

