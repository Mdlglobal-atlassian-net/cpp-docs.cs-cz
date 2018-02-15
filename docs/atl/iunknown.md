---
title: IUnknown | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 46f1a1581df6c57b96063916802cfd26722d2ac1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="iunknown"></a>IUnknown
[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) je základní rozhraní každého rozhraní modelu COM.  Toto rozhraní definuje tři metody: [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521), [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379), a [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317). [QueryInterface –](http://msdn.microsoft.com/library/windows/desktop/ms682521) umožňuje uživateli rozhraní požádejte objekt ukazatel na jiné jeho rozhraní. [Addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379) a [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317) implementovat na rozhraní při počítání referencí.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM](../atl/introduction-to-com.md)   
 [IUnknown a dědičnost rozhraní](http://msdn.microsoft.com/library/windows/desktop/ms692713)

