---
title: Charakterizace operátoru (#@) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9e0c0d140d937b7359ff3abf9c0eae145a89210
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912729"
---
# <a name="charizing-operator-"></a>Charakterizace operátoru (#@)
**Konkrétní Microsoft**  
  
 Operátor zřetězení lze použít pouze s argumenty makra. Pokud **#@** předchází formální parametr v definici makra skutečné argument je uzavřena do jednoduchých uvozovek a považován za znakem, pokud není rozbalen makro. Příklad:  
  
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