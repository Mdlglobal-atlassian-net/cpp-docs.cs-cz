---
title: "once_flag – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- mutex/std::once_flag
dev_langs:
- C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 482ef221338651ef3e6f6ec272c1a48984d40912
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="onceflag-structure"></a>once_flag – struktura
Představuje `struct` používané funkce šablony [call_once –](../standard-library/mutex-functions.md#call_once) zajistit, že inicializace kód je volat pouze jednou, ani za přítomnosti více vláken provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
once_flag – struktura {constexpr once_flag() noexcept; once_flag(const once_flag&); once_flag – & operátor =(const once_flag&);};  
  
## <a name="remarks"></a>Poznámky  
 `once_flag` `struct` Má výchozí konstruktor.  
  
 Objekty typu `once_flag` mohou být vytvořeny, ale nelze kopírovat.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<mutex >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)



