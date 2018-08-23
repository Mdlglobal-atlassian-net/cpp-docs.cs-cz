---
title: no_implementation – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_implementation
dev_langs:
- C++
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbf715e2cbd19d139904438e722e4d0b72e29f29
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465940"
---
# <a name="noimplementation"></a>no_implementation
**Specifické pro C++**  
  
Potlačí generování tli hlavičky, která obsahuje implementace členské funkce obálky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
no_implementation  
```  
  
## <a name="remarks"></a>Poznámky  
 
Pokud tento atribut je zadán, hlavičku .tlh s deklaracemi vystavit knihovny typů položek, vygeneruje se bez `#include` příkazu zahrnout hlavičku souboru tli.  
  
Tento atribut se používá ve spojení s [implementation_only –](../preprocessor/implementation-only.md).  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)