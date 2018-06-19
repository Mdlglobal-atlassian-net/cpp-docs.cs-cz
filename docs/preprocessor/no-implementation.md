---
title: no_implementation – | Microsoft Docs
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
ms.openlocfilehash: bf756a411404d2ebb821d5b226818844acfca75b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849545"
---
# <a name="noimplementation"></a>no_implementation
**Konkrétní C++**  
  
 Potlačí generování .tli hlavičky, která obsahuje implementace členských funkcí obálku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
no_implementation  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud tento atribut je zadán, hlavičku .tlh s deklaracemi vystavit knihovny typů položek, vygeneruje se bez `#include` příkaz, který má zahrnout soubor hlaviček, .tli.  
  
 Tento atribut se používá ve spojení s [implementation_only –](../preprocessor/implementation-only.md).  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)