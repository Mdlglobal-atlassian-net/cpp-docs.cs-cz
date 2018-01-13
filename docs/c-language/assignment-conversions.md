---
title: "Převody přiřazení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94087d5e07765b1052404a4c3e51f37db2a31e3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="assignment-conversions"></a>Převody přiřazení
V operacích přiřazení je typ přiřazené hodnoty převeden na typ proměnné, která obdrží přiřazení. Jazyk C umožňuje převod mezi celočíselnými typy a typy s plovoucí desetinnou čárkou i v případě, že je informace při převodu ztracena. Převod metodu použitou závisí na typech zahrnutých v přiřazení, jak je popsáno v [obvyklé aritmetické převody](../c-language/usual-arithmetic-conversions.md) a v následujících částech:  
  
-   [Převody z integrálních typů se znaménkem](../c-language/conversions-from-signed-integral-types.md)  
  
-   [Převody z integrálních typů bez znaménka](../c-language/conversions-from-unsigned-integral-types.md)  
  
-   [Převody z typů s plovoucí desetinnou čárkou](../c-language/conversions-from-floating-point-types.md)  
  
-   [Převod na a z typů ukazatele](../c-language/conversions-to-and-from-pointer-types.md)  
  
-   [Převody z ostatních typů](../c-language/conversions-from-other-types.md)  
  
 Kvalifikátory typu neovlivní allowability převodu, i když **const** l-value nelze použít na levé straně přiřazení.  
  
## <a name="see-also"></a>Viz také  
 [Převody typu](../c-language/type-conversions-c.md)