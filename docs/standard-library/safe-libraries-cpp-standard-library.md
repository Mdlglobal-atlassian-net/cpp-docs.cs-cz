---
title: "Bezpečné knihovny: Standardní knihovna C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _SCL_SECURE_NO_DEPRECATE
dev_langs: C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b8cc4b94534845901a900a8c0ecff1d89c6bb600
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="safe-libraries-c-standard-library"></a>Bezpečné knihovny: standardní knihovna C++
Do knihovny, které se dodávají spolu s Visual C++, včetně standardní knihovny C++, aby byly bezpečnější jste provedli několik vylepšení.  
  
 Několika metod ve standardní knihovně C++ byly identifikovány jako potenciálně nebezpečného protože může vést k přetečení vyrovnávací paměti nebo jiných vadou kódu. Použití těchto metod se nedoporučuje a byly vytvořeny nové, bezpečnější metody je Pokud chcete nahradit. Tyto nové metody všechny končit `_s`.  
  
 Chcete-li iterátory a algoritmy také byly provedeny několik vylepšení. Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md), [podpora ladění iterátorů](../standard-library/debug-iterator-support.md) a [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).  
  
## <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí standardní knihovna C++ metody, které mohou být nebezpečné, jakož i ekvivalenty bezpečnější:  
  
|Potenciálně nebezpečného – metoda|Bezpečnější ekvivalent|  
|-------------------------------|----------------------|  
|[kopírování](../standard-library/basic-string-class.md#copy)|[basic_string::_Copy_s](../standard-library/basic-string-class.md#copy_s)|  
|[kopírování](../standard-library/char-traits-struct.md#copy)|[char_traits::_Copy_s](../standard-library/char-traits-struct.md#copy_s)|  
  
 Pokud volání jedné z výše uvedených potenciálně nebezpečného metod, nebo pokud používáte iterátory nesprávně, vygeneruje kompilátor [upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Informace o tom, jak zakázat tato upozornění najdete v tématu [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)  
  
 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)  
  
 [Checked – iterátory](../standard-library/checked-iterators.md)  
  
 [Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehled knihovny C++ Standard](../standard-library/cpp-standard-library-overview.md)

