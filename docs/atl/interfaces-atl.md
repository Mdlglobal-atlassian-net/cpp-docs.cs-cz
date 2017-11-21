---
title: "Rozhraní (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 28fb749a705ed01b4c10d22cea0062c2f0d799c7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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

