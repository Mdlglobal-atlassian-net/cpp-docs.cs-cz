---
title: "allocator_variable_size – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
dev_langs: C++
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 43825113ac1c067354dd95c675a54a7741806108
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="allocatorvariablesize-class"></a>allocator_variable_size – třída
Popisuje objekt, který spravuje přidělení úložiště a uvolnění objektů typu `Type` použití mezipaměti typu [cache_freelist –](../standard-library/cache-freelist-class.md) s délkou spravuje [max_variable_size](../standard-library/max-variable-size-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Type>  
class allocator_variable_size;
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Type`|Typ elementů přidělené pomocí přidělujícího modulu.|  
  
## <a name="remarks"></a>Poznámky  
 [Allocator_decl –](../standard-library/allocators-functions.md#allocator_decl) makro předá tuto třídu jako `name` parametr v následující příkaz:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
## <a name="see-also"></a>Viz také  
 [\<alokátorů >](../standard-library/allocators-header.md)



