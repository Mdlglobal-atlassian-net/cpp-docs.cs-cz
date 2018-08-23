---
title: Charakterizace operátoru (#@) | Dokumentace Microsoftu
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
ms.openlocfilehash: c6aa18936497f0415da331697aceb26f26345500
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464699"
---
# <a name="charizing-operator-"></a>Charakterizace operátoru (#@)
**Specifické pro Microsoft**  
  
Operátor zřetězení lze použít pouze s argumenty makra. Pokud `#@` předchází formální parametr v definici makra, je skutečný argument uzavřen do jednoduchých uvozovek a při rozbalení makra je považován za znak. Příklad:  
  
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
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 
[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)