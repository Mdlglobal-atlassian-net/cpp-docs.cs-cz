---
title: "stdext – Namespace | Microsoft Docs"
ms.custom: 
ms.date: 09/06/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- stdext
dev_langs:
- C++
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 265a10e71064f2bf3a318a272b751009b1b193be
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="stdext-namespace"></a>stdext – obor názvů

Členové [ \<hash_map >](../standard-library/hash-map.md) a [ \<hash_set >](../standard-library/hash-set.md) soubory hlaviček aktuálně nejsou součástí standardu ISO C++. Proto tyto typy a členy byly přesunuté z `std` oboru názvů do oboru názvů `stdext`, zůstat shoduje s C++ standard.

Při kompilaci s [/Ze](../build/reference/za-ze-disable-language-extensions.md), což je výchozí, kompilátor upozorní na použití `std` pro členy \<hash_map > a \<hash_set > soubory hlaviček. Chcete-li zakázat upozornění, použijte [upozornění](../preprocessor/warning.md) – Direktiva pragma.

Tak, aby měl kompilátoru chybovou zprávu pro použití `std` pro členy \<hash_map > a \<hash_set > hlavičkové soubory s **/Ze**, přidejte následující direktivu před `#include` soubory hlaviček všechny standardní knihovna C++.

```cpp  
#define _DEFINE_DEPRECATED_HASH_CLASSES 0  
```  

Při kompilaci s **/Za**, kompilátor, vygeneruje se chyba.  

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)

