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
ms.openlocfilehash: 1920d8183607140ebe38aaf56a447bc9cd3010f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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