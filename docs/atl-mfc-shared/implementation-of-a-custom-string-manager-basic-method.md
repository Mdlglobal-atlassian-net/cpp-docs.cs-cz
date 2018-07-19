---
title: Implementace z vlastního správce řetězců (základní způsob) | Dokumentace Microsoftu
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
ms.openlocfilehash: c393489b8b4d0353ae37a21132f66e0618b3b794
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884581"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implementace z vlastního správce řetězců (základní způsob)
Nejjednodušší způsob, jak přizpůsobit schéma přidělení paměti pro data řetězce se má používat zadaný ATL `CAtlStringMgr` třídy, ale poskytnout vlastní paměti rutiny přidělení. Konstruktor pro `CAtlStringMgr` přijímá jeden parametr: ukazatel `IAtlMemMgr` objektu. `IAtlMemMgr` je abstraktní základní třída, která poskytuje obecné rozhraní pro haldu. Použití `IAtlMemMgr` rozhraní, `CAtlStringMgr` přiděluje, znovu alokuje a uvolní paměť pro ukládání dat řetězců. Můžete buď implementovat `IAtlMemMgr` rozhraní sami, nebo použijte jednu z pěti třídy správce paměti poskytované ATL. Správce paměti poskytované ATL jednoduše zabalit existující zařízení přidělení paměti:  
  
-   [Ccrtheap –](../atl/reference/ccrtheap-class.md) zabalí standardních funkcí haldy CRT ([malloc](../c-runtime-library/reference/malloc.md), [bezplatné](../c-runtime-library/reference/free.md), a [realloc](../c-runtime-library/reference/realloc.md))  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md) zabalí zpracování haldy Win32, pomocí [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597), [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701), a [HeapRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366704)  
  
-   [Clocalheap –](../atl/reference/clocalheap-class.md) zabaluje rozhraní API Win32: [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723), [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730), a [LocalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)  
  
-   [Cglobalheap –](../atl/reference/cglobalheap-class.md) zabaluje rozhraní API Win32: [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574), [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579), a [GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590).  
  
-   [Ccomheap –](../atl/reference/ccomheap-class.md) zabalí rozhraní API modelu COM úloh Allocator: [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727), [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722), a [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)  
  
 Pro účely správy paměti řetězce, je nejužitečnější třídy `CWin32Heap` vzhledem k tomu, že umožňuje vytvořit více nezávislých haldy. Například Kdybyste chtěli použít samostatné haldy pouze pro řetězce, může provedete následující:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 Používat ke správě paměti pro tohoto správce soukromého řetězce `CString` proměnnou, předejte ukazatel manager jako parametr `CString` konstruktor proměnné:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Správa paměti pomocí CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

