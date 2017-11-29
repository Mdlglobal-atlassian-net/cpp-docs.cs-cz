---
title: _SECURE_SCL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _SECURE_SCL
dev_langs: C++
helpviewer_keywords: _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d06ea79b3dd5ca960ba57d0d27416acffe51c632
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="securescl"></a>_SECURE_SCL
  
Nahrazeno [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), definuje tato makro zda [zaškrtnutí iterátory](../standard-library/checked-iterators.md) jsou povoleny. Ve výchozím nastavení jsou checked – iterátory povoleno v sestavení pro ladění a v sestavení prodejní zakázáno.  
  
> [!IMPORTANT]
> Přímé použití `_SECURE_SCL` makro je zastaralý. Místo toho použijte `_ITERATOR_DEBUG_LEVEL` řídit nastavení zaškrtnuté iterator. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).  
  
## <a name="remarks"></a>Poznámky  
  
Po checked – iterátory povoleno, unsafe iterator použití způsobí, že chyba za běhu a program bude ukončen. Chcete-li povolit checked – iterátory, nastavte `_ITERATOR_DEBUG_LEVEL` 1 nebo 2. Jde o ekvivalent `_SECURE_SCL` nastavení 1 nebo povoleno:  
  
```  
#define _ITERATOR_DEBUG_LEVEL 1  
```  
  
Chcete-li zakázat checked – iterátory, nastavte `_ITERATOR_DEBUG_LEVEL` na hodnotu 0. Jde o ekvivalent `_SECURE_SCL` nastavení 0 nebo vypne:  
  
```  
#define _ITERATOR_DEBUG_LEVEL 0  
```  
  
Informace o tom, jak zakázat upozornění o checked – iterátory najdete v tématu [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).  
  
## <a name="see-also"></a>Viz také  
[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)   
[Checked – iterátory](../standard-library/checked-iterators.md)   
[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)   
[Bezpečné knihovny: Standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)
