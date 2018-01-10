---
title: "Charakterizace operátoru (#@) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#@'
dev_langs: C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 933e97732462b61919d9e5a1e73f2a72d26ea01b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="charizing-operator-"></a>Charakterizace operátoru (#@)
**Konkrétní Microsoft**  
  
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