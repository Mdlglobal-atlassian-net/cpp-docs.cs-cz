---
title: "hash – struktura (standardní knihovna C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- thread/std::hash
dev_langs:
- C++
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d14ee7900fe3c83097e0241859d9b569562736fb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="hash-structure-c-standard-library"></a>hash – struktura (standardní knihovna C++)
Definuje členské funkce, která vrátí hodnotu, která je jednoznačně dáno `Val`. Definuje – členská funkce [hash](../standard-library/hash-class.md) funkce, který je vhodný pro mapování hodnoty typu `thread::id` k distribučnímu index hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <>  
struct hash<thread::id> :   
    public unary_function<thread::id, size_t>  
{  
    size_t operator()(thread::id Val) const;

 
};  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<vlákno >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<vlákno >](../standard-library/thread.md)   
 [unary_function – struktura](../standard-library/unary-function-struct.md)
