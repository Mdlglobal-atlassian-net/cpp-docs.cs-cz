---
title: "is_constructible třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 88c35088d202f9247ed947ef2d722fe0cdaac984
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="isconstructible-class"></a>is_constructible – třída
Testuje, zda je zkonstruovatelný typu, pokud se používá zadané typy argumentů.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class... Args>  
struct is_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
 `Args`  
 Typy argumentů tak, aby odpovídaly v konstruktoru objektu `T`.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je zkonstruovatelný pomocí typy argumentů v `Args`, jinak má hodnotu false. Typ `T` je zkonstruovatelný Pokud za definicí proměnné `T t(std::declval<Args>()...);` je ve správném formátu. Obě `T` a všechny typy v `Args` musí být úplný typy `void`, nebo pole neznámé hranice.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



