---
title: Implementace z vlastního správce řetězců (základní způsob)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: 4e3ffcdcd034fea81734aaeb87e4c33d81647f66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537810"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implementace z vlastního správce řetězců (základní způsob)

Nejjednodušší způsob, jak přizpůsobit schéma přidělení paměti pro data řetězce se má používat zadaný ATL `CAtlStringMgr` třídy, ale poskytnout vlastní paměti rutiny přidělení. Konstruktor pro `CAtlStringMgr` přijímá jeden parametr: ukazatel `IAtlMemMgr` objektu. `IAtlMemMgr` je abstraktní základní třída, která poskytuje obecné rozhraní pro haldu. Použití `IAtlMemMgr` rozhraní, `CAtlStringMgr` přiděluje, znovu alokuje a uvolní paměť pro ukládání dat řetězců. Můžete buď implementovat `IAtlMemMgr` rozhraní sami, nebo použijte jednu z pěti třídy správce paměti poskytované ATL. Správce paměti poskytované ATL jednoduše zabalit existující zařízení přidělení paměti:

- [Ccrtheap –](../atl/reference/ccrtheap-class.md) zabalí standardních funkcí haldy CRT ([malloc](../c-runtime-library/reference/malloc.md), [bezplatné](../c-runtime-library/reference/free.md), a [realloc](../c-runtime-library/reference/realloc.md))

- [CWin32Heap](../atl/reference/cwin32heap-class.md) zabalí zpracování haldy Win32, pomocí [HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc), [HeapFree](/windows/desktop/api/heapapi/nf-heapapi-heapfree), a [HeapRealloc](/windows/desktop/api/heapapi/nf-heapapi-heaprealloc)

- [Clocalheap –](../atl/reference/clocalheap-class.md) zabaluje rozhraní API Win32: [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc), [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree), a [LocalRealloc](/windows/desktop/api/winbase/nf-winbase-localrealloc)

- [Cglobalheap –](../atl/reference/cglobalheap-class.md) zabaluje rozhraní API Win32: [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc), [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree), a [GlobalRealloc](/windows/desktop/api/winbase/nf-winbase-globalrealloc).

- [Ccomheap –](../atl/reference/ccomheap-class.md) zabalí rozhraní API modelu COM úloh Allocator: [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree), a [CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

Pro účely správy paměti řetězce, je nejužitečnější třídy `CWin32Heap` vzhledem k tomu, že umožňuje vytvořit více nezávislých haldy. Například Kdybyste chtěli použít samostatné haldy pouze pro řetězce, může provedete následující:

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

Používat ke správě paměti pro tohoto správce soukromého řetězce `CString` proměnnou, předejte ukazatel manager jako parametr `CString` konstruktor proměnné:

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>Viz také

[Správa paměti pomocí CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

