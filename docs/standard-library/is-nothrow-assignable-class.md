---
title: "is_nothrow_assignable třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_nothrow_assignable
dev_langs: C++
helpviewer_keywords: is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe32798dc98335dbada12e1914a77e89f0d78a25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="isnothrowassignable-class"></a>is_nothrow_assignable – třída
Kontroluje, zda hodnota `From` typ lze přiřadit k `To` typu a přiřazení není znám výjimku.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class To, class From>  
struct is_nothrow_assignable;
```  
  
#### <a name="parameters"></a>Parametry  
 Chcete-li  
 Typ objektu, který obdrží přiřazení.  
  
 From  
 Typ objektu, který obsahuje hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Výraz `declval<To>() = declval<From>()` musí být ve správném formátu a musí být známo kompilátoru nechcete výjimku. Obě `From` a `To` musí být úplný typy `void`, nebo pole neznámé hranice.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



