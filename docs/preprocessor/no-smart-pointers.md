---
title: no_smart_pointers – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_search_pointers
dev_langs:
- C++
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 345da5de492c33107effffb9c97b2fe60906e899
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466195"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**Specifické pro C++**  
  
Potlačí vytváření inteligentních ukazatelů pro všechna rozhraní v knihovně typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
no_smart_pointers  
```  
  
## <a name="remarks"></a>Poznámky  
 
Ve výchozím nastavení při použití `#import`, získat deklarace inteligentního ukazatele pro všechna rozhraní v knihovně typů. Tyto inteligentní ukazatele jsou typu [třída _com_ptr_t](../cpp/com-ptr-t-class.md).  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)