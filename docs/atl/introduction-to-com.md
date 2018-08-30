---
title: Úvod do modelu COM | Dokumentace Microsoftu
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a408ecb1a96aab284a4ac8c7cdd59909ed7c0ea
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216520"
---
# <a name="introduction-to-com"></a>Úvod do modelu COM
COM je základní "object model" na jaké ovládací prvky ActiveX a OLE jsou vytvořeny. COM umožňuje vystavit funkčnost pro jiné komponenty a k hostování aplikací. Definuje, jak samotného objektu zpřístupňuje i jak toto ohrožení funguje napříč procesy a v sítích. COM také definuje životního cyklu objektu.  
  
 Základní rozhraní COM jsou tyto koncepty:  
  
-   [Rozhraní](../atl/interfaces-atl.md) – mechanismus, pomocí kterého objekt zpřístupňuje jeho funkce.  
  
-   [IUnknown](../atl/iunknown.md) – základní rozhraní, na kterém jsou všechny ostatní založené. Implementuje počítání odkazů a interface dotazování mechanismy zpracování nástrojem modelu COM.  
  
-   [Počítání odkazů](../atl/reference-counting.md) – technika, podle kterého objektu (nebo přísně rozhraní) rozhodne, když již nejsou déle používány a je proto zdarma k odebrání samotné.  
  
-   [QueryInterface](../atl/queryinterface.md) – metoda používá k dotazování na objekt pro dané rozhraní.  
  
-   [Zařazování](../atl/marshaling.md) – mechanismus, který umožňuje objektů, který se má použít pro vlákno, proces i ohraničení sítě, čímž umožní nezávislost umístění.  
  
-   [Agregace](../atl/aggregation.md) , ve kterém můžete provádět jednoho objektu pomocí jiného.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM a knihovny ATL](../atl/introduction-to-com-and-atl.md)   
 [Component Object Model](/windows/desktop/com/the-component-object-model)

