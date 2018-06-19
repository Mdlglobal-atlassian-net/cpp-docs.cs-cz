---
title: IUnknown | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c02018ee3cefb1b98c2df850d44578cf3a092c64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355836"
---
# <a name="iunknown"></a>IUnknown
[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) je základní rozhraní každého rozhraní modelu COM.  Toto rozhraní definuje tři metody: [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521), [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379), a [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317). [QueryInterface –](http://msdn.microsoft.com/library/windows/desktop/ms682521) umožňuje uživateli rozhraní požádejte objekt ukazatel na jiné jeho rozhraní. [Addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379) a [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317) implementovat na rozhraní při počítání referencí.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM](../atl/introduction-to-com.md)   
 [IUnknown a dědičnost rozhraní](http://msdn.microsoft.com/library/windows/desktop/ms692713)

