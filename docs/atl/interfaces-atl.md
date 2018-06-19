---
title: Rozhraní (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0db5a79f187cb0fe320bf67aace751a5d4c537d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359311"
---
# <a name="interfaces-atl"></a>Rozhraní (ATL)
Rozhraní je způsob, ve kterém objekt poskytuje jeho funkce vnějším světem. V modelu COM je rozhraní tabulku ukazatelé (např. C++ vtable) na funkce, které jsou implementované objektu. V tabulce představuje rozhraní, a metody tohoto rozhraní jsou funkce, na které odkazuje. Objekt můžou zpřístupnit tolik rozhraní zvolí.  
  
 Každé rozhraní je založen na základní rozhraní modelu COM, [IUnknown](../atl/iunknown.md). Metody **IUnknown** procházení do jiných rozhraní vystavené objektu.  
  
 Každé rozhraní je rovněž rozhraní je jedinečné ID (IID). Tato jedinečnosti usnadňuje podporu rozhraní správy verzí. Nová verze rozhraní je jednoduše je nové rozhraní s novou IID.  
  
> [!NOTE]
>  Jsou předdefinované identifikátory IID pro standardní rozhraní COM a OLE.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM](../atl/introduction-to-com.md)   
 [COM – objekty a rozhraní](http://msdn.microsoft.com/library/windows/desktop/ms690343)

