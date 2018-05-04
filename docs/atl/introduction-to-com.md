---
title: Úvod do modelu COM | Microsoft Docs
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
ms.openlocfilehash: 938d0c45cae5ec9a2988f77f539af1a3d5513b83
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="introduction-to-com"></a>Úvod do modelu COM
COM je základní "model objektu" na které ovládací prvky ActiveX a OLE jsou vytvořeny. Model COM umožňuje objekt vystavit jeho funkce pro ostatní součásti a hostování aplikací. Definuje, jak objekt zpřístupní samotné i jak tato ohrožení funguje napříč procesy a napříč sítí. COM také definuje objektu životního cyklu.  
  
 Základní do modelu COM jsou tyto koncepty:  
  
-   [Rozhraní](../atl/interfaces-atl.md) – mechanismus, pomocí kterého se objekt zpřístupňuje jeho funkci.  
  
-   [IUnknown](../atl/iunknown.md) – základní rozhraní, na kterém jsou všechny ostatní založena. Implementuje počítání odkazů a rozhraní dotazování mechanismy spuštěn prostřednictvím modelu COM.  
  
-   [Počítání odkazů](../atl/reference-counting.md) – techniku, pomocí kterého objektu (, výhradně, rozhraní) rozhodne nebo pokud se už nepoužívá a je proto volné k odebrání samotné.  
  
-   [QueryInterface –](../atl/queryinterface.md) – metoda použitá pro dotaz na objekt v příslušném rozhraní.  
  
-   [Zařazování](../atl/marshaling.md) – mechanismus, který povoluje objekty pro použití na celém přístup z více vláken, proces a síťovými hranicemi, aby vám umožnil nezávislost umístění.  
  
-   [Agregace](../atl/aggregation.md) , ve kterém můžete provádět jeden objekt pomocí jiné.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM a knihovny ATL](../atl/introduction-to-com-and-atl.md)   
 [Komponentový objektový Model](http://msdn.microsoft.com/library/windows/desktop/ms694363)

