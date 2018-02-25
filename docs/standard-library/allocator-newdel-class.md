---
title: "allocator_newdel – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::allocators::allocator_newdel
- allocators/stdext::allocator_newdel
- stdext::allocators::allocator_newdel
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocators [C++], allocator_newdel
- stdext::allocator_newdel
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dab9a7b0d6cf424dcc361b8cc28cab0bdb7992ef
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="allocatornewdel-class"></a>allocator_newdel – třída
Implementuje přidělení, který používá `operator delete` se zrušit přidělení paměti bloku a `operator new` přidělit blok paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Type>  
class allocator_newdel;
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Type`|Typ elementů přidělené pomocí přidělujícího modulu.|  
  
## <a name="remarks"></a>Poznámky  
 [Allocator_decl –](../standard-library/allocators-functions.md#allocator_decl) makro předá tuto třídu jako `name` parametr v následující příkaz: `ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
## <a name="see-also"></a>Viz také  
 [\<allocators>](../standard-library/allocators-header.md)



