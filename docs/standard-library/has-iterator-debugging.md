---
title: _HAS_ITERATOR_DEBUGGING | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _HAS_ITERATOR_DEBUGGING
dev_langs: C++
helpviewer_keywords: _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 77690e373363aebec8876bc20fe88e3f09f8d79b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING  
  
Nahrazeno [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), tento makro definuje, zda je povoleno iterator ladění funkce v sestavení ladicí verze. Ve výchozím nastavení ladění iterátorů povoleno v sestavení pro ladění a zakázáno v prodejní sestavení. Další informace najdete v tématu [podpora ladění iterátorů](../standard-library/debug-iterator-support.md).  
  
> [!IMPORTANT]
> Přímé použití `_HAS_ITERATOR_DEBUGGING` makro je zastaralý. Místo toho použijte `_ITERATOR_DEBUG_LEVEL` k řízení iterator nastavení ladění. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).  
  
## <a name="remarks"></a>Poznámky  
Chcete-li povolit iterator ladění v sestavení pro ladění, nastavte `_ITERATOR_DEBUG_LEVEL` 2. Jde o ekvivalent `_HAS_ITERATOR_DEBUGGING` nastavení 1 nebo povoleno:  
  
```  
#define _ITERATOR_DEBUG_LEVEL 2  
```  
  
`_ITERATOR_DEBUG_LEVEL`Nelze nastavit na hodnotu 2 (a `_HAS_ITERATOR_DEBUGGING` nelze nastavit na hodnotu 1) v prodejní sestavení.  
  
Chcete-li zakázat ladění iterátory v sestavení pro ladění, nastavte `_ITERATOR_DEBUG_LEVEL` na 0 nebo 1. Jde o ekvivalent `_HAS_ITERATOR_DEBUGGING` nastavení 0 nebo vypne:  
  
```  
#define _ITERATOR_DEBUG_LEVEL 0  
```  
  
## <a name="see-also"></a>Viz také  
 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)   
 [Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)   
 [Checked – iterátory](../standard-library/checked-iterators.md)   
 [Bezpečné knihovny: Standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)

