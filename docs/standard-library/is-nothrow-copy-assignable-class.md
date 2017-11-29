---
title: "is_nothrow_copy_assignable – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_nothrow_copy_assignable
dev_langs: C++
helpviewer_keywords: is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 798bd496504dafe2f4d9ac2510fef37b5bce0b91
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable – třída
Ověřuje, zda má typ operátor přiřazení kopie, který se označuje kompilátoru nechcete výjimku.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>
struct is_nothrow_copy_assignable;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance typu predikátu platí pro kde typ `T` kde `is_nothrow_assignable<T&, const T&>` obsahuje hodnotu true; jinak má hodnotu false.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)   
 [is_nothrow_assignable – třída](../standard-library/is-nothrow-assignable-class.md)   




