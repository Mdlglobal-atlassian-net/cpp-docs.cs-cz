---
title: "treat_as_floating_point – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: chrono/std::chrono::treat_as_floating_point
dev_langs: C++
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8bfdda5bab6db19a1cf6d123f141f87249b62478
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point – struktura
Určuje, zda `Rep` lze zacházet jako s plovoucí desetinnou čárkou typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Rep>  
struct treat_as_floating_point : is_floating_point<Rep>;  
```  
  
## <a name="remarks"></a>Poznámky  
 `Rep`lze zacházet jako s plovoucí desetinnou čárkou typ pouze tehdy, když specializace `treat_as_floating_point<Rep>` je odvozený od [true_type –](../standard-library/type-traits-typedefs.md#true_type). Šablony třídy můžete specializované pro uživatelem definovaný typ.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<typu chrono >  
  
 **Namespace:** std::chrono  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<typu chrono >](../standard-library/chrono.md)
