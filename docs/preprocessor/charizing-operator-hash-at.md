---
title: "Charakterizace operátoru (#@) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#@'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6521322e7a71d8e76b657fb8580157c036e881b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="charizing-operator-"></a>Charakterizace operátoru (#@)
**Microsoft Specific**  
  
 Operátor zřetězení lze použít pouze s argumenty makra. Pokud  **#@**  předchází formální parametr v definici makra skutečné argument je uzavřena do jednoduchých uvozovek a považován za znakem, pokud není rozbalen makro. Příklad:  
  
```  
#define makechar(x)  #@x  
```  
  
 způsobí, že příkaz  
  
```  
a = makechar(b);  
```  
  
 je rozbalen na  
  
```  
a = 'b';  
```  
  
 Znak jednoduchých uvozovek nelze použít spolu s operátorem zřetězení.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Operátory preprocesoru](../preprocessor/preprocessor-operators.md)