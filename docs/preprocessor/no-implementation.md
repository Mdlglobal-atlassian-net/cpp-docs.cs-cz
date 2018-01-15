---
title: "no_implementation – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_implementation
dev_langs: C++
helpviewer_keywords: no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa0a8337de519b2b0d43e8d5035e3845e1aefbe4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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