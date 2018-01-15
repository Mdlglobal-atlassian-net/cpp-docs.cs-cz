---
title: "is_trivially_constructible třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_trivially_constructible
dev_langs: C++
helpviewer_keywords: is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0a01ee89c1bb07ab0ca3c9c54161b7d9a3097be3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible – třída
Ověřuje, zda typ je trivially zkonstruovatelný, pokud se používá zadané typy argumentů.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class... Args>  
struct is_trivially_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
 `Args`  
 Typy argumentů tak, aby odpovídaly v konstruktoru objektu `T`.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je trivially zkonstruovatelný pomocí typy argumentů v `Args`, jinak má hodnotu false. Typ `T` je trivially zkonstruovatelný Pokud za definicí proměnné `T t(std::declval<Args>()...);` má správný tvar a je zřejmé, že volání žádné netriviální operací. Obě `T` a všechny typy v `Args` musí být úplný typy `void`, nebo pole neznámé hranice.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



