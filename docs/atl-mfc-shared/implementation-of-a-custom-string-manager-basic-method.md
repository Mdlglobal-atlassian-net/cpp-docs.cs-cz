---
title: Implementace nástroje vlastní řetězec Manager (základní metoda) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 259f9533747b266f0be0a782cdc94c98f167d2d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implementace nástroje vlastní řetězec Manager (základní metoda)
Nejjednodušší způsob, jak přizpůsobit schéma přidělení paměti pro data řetězce se má používat zadaný ATL **CAtlStringMgr** třídy, ale poskytnutí vlastní paměti rutiny přidělení. V konstruktoru pro **CAtlStringMgr** přijímá jeden parametr: ukazatel na `IAtlMemMgr` objektu. `IAtlMemMgr` je abstraktní základní třída, která poskytuje obecné rozhraní haldě. Pomocí `IAtlMemMgr` rozhraní, **CAtlStringMgr** přiděluje, přidělí a uvolní paměť použitá k ukládání dat řetězců. Můžete buď implementace `IAtlMemMgr` rozhraní sami, nebo použijte jednu z pěti tříd manager zadaný ATL paměti. Zadaný ATL paměti správci jednoduše zabalit stávajících zařízení přidělení paměti:  
  
-   [CCRTHeap](../atl/reference/ccrtheap-class.md) zabalí standardní funkce hald CRT ([malloc –](../c-runtime-library/reference/malloc.md), [volné](../c-runtime-library/reference/free.md), a [realloc –](../c-runtime-library/reference/realloc.md))  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md) zabalí haldy Win32 zpracování, pomocí [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597), [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701), a [HeapRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366704)  
  
-   [CLocalHeap](../atl/reference/clocalheap-class.md) zabaluje rozhraní API Win32: [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723), [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730), a [LocalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)  
  
-   [CGlobalHeap](../atl/reference/cglobalheap-class.md) zabaluje rozhraní API Win32: [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574), [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579), a [GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590).  
  
-   [CComHeap](../atl/reference/ccomheap-class.md) zabalí rozhraní API modelu COM úloh Allocator: [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727), [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722), a [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)  
  
 Pro účely správy paměti řetězce, je nejvhodnější třída je `CWin32Heap` vzhledem k tomu, že se vám umožní vytvořit více nezávislých haldách. Například pokud jste chtěli použít samostatné haldě jenom pro řetězce, můžete to udělat následující:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 Používat ke správě paměti pro tento privátní řetězec správce `CString` proměnnou, vložte ukazatele pro správce jako parametr, který se `CString` konstruktor proměnné:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Správa paměti pomocí CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

