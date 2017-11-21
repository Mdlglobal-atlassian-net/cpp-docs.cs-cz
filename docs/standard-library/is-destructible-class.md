---
title: "is_destructible třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_destructible
dev_langs: C++
helpviewer_keywords: is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1b673ae9c46479723684a22205853229f913573d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="isdestructible-class"></a>is_destructible – třída
Ověřuje, zda je typ zničitelné.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
struct is_destructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `T` zničitelné typu, jinak má hodnotu false. Zničitelné typy jsou odkazové typy, kde je pro nějaký typ objektu typy a typy `U` rovna `remove_all_extents_t<T>` unevaluated operand `std::declval<U&>.~U()` je ve správném formátu. Jiné typy, včetně neúplné typy `void`a funkce typy, nejsou zničitelné typy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)



