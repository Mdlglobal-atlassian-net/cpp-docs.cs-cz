---
title: "Úvod do modelu COM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs: C++
helpviewer_keywords: COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 236222296b270fe52f43f42a823e3f6f790d08ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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

