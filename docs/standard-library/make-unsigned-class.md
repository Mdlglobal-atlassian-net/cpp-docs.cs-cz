---
title: "make_unsigned – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::make_unsigned
dev_langs: C++
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea6150163c63378ed131db3c97e879b89aba9556
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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



