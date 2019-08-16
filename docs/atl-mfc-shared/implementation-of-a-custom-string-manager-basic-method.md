---
title: Implementace vlastního správce řetězců (základní metoda)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: 92c1c46f5251980f9cefb55e052e9aff395e0e60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491316"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implementace vlastního správce řetězců (základní metoda)

Nejjednodušší způsob, jak přizpůsobit schéma přidělování paměti pro řetězcová data, je použití třídy poskytované `CAtlStringMgr` knihovnou ATL, ale poskytuje vlastní rutiny přidělování paměti. Konstruktor pro `CAtlStringMgr` přijímá jeden parametr: ukazatel `IAtlMemMgr` na objekt. `IAtlMemMgr`je abstraktní základní třída, která poskytuje obecné rozhraní pro haldu. `IAtlMemMgr` Pomocí rozhraní `CAtlStringMgr` , přidělí, znovu přidělí a uvolní paměť, která se používá k ukládání řetězcových dat. `IAtlMemMgr` Rozhraní můžete buď implementovat sami, nebo můžete použít jednu z pěti tříd správce paměti poskytovaných knihovnou ATL. Správci paměti poskytnutých knihovnou ATL jednoduše zabalí existující zařízení pro přidělování paměti:

- [CCRTHeap](../atl/reference/ccrtheap-class.md) Zabalí standardní funkce haldy CRT ([](../c-runtime-library/reference/malloc.md): pole, [Free](../c-runtime-library/reference/free.md)a [realokace](../c-runtime-library/reference/realloc.md)).

- [CWin32Heap](../atl/reference/cwin32heap-class.md) Zabalí popisovač haldy Win32 s použitím [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc), [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree)a [HeapRealloc](/windows/win32/api/heapapi/nf-heapapi-heaprealloc) .

- [CLocalHeap](../atl/reference/clocalheap-class.md) Zabalí rozhraní API systému Win32: [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc), [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree)a [LocalReAlloc](/windows/win32/api/winbase/nf-winbase-localrealloc)

- [CGlobalHeap](../atl/reference/cglobalheap-class.md) Zabalí rozhraní API systému Win32: [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc), [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)a [GlobalRealloc](/windows/win32/api/winbase/nf-winbase-globalrealloc).

- [CComHeap](../atl/reference/ccomheap-class.md) Zabalí rozhraní API pro přidělování úloh COM: [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)a [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

Pro účely správy paměti řetězců je `CWin32Heap` nejužitečnější třída, protože umožňuje vytvořit více nezávislých hald. Například pokud jste chtěli použít samostatnou haldu pouze pro řetězce, můžete provést následující:

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

Chcete-li použít tohoto správce privátních řetězců ke správě `CString` paměti pro proměnnou, předejte ukazatel na správce jako parametr `CString` do konstruktoru proměnné:

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>Viz také:

[Správa paměti pomocí CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
