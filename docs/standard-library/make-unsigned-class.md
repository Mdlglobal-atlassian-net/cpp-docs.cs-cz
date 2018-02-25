---
title: "make_unsigned – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::make_unsigned
dev_langs:
- C++
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3691e8840bf4d51f48359e7efbdd777bd18e01cb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="makeunsigned-class"></a>make_unsigned – třída
Zadejte díky nebo nejmenší nepodepsané zadejte větší než nebo roven hodnotě velikost na typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`T`|Typ, který chcete upravit.|  
  
## <a name="remarks"></a>Poznámky  
 Instance typu modifikátor obsahuje upravit – typ, který je `T` Pokud `is_unsigned<T>` platí. V opačném případě je nejmenší typ se znaménkem `ST` pro kterou `sizeof (T) <= sizeof (ST)`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



