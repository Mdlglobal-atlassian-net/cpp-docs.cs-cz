---
title: "is_nothrow_constructible třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_nothrow_constructible
dev_langs: C++
helpviewer_keywords: is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d38a8b426aff513165bd29c234d842d6a611653e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible – třída
Ověřuje, zda je zkonstruovatelný typu a není znám výjimku, pokud se používá zadané typy argumentů.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class... Args>  
struct is_nothrow_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
 `Args`  
 Typy argumentů tak, aby odpovídaly v konstruktoru objektu `T`.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je zkonstruovatelný pomocí typy argumentů v `Args`a konstruktoru není znám kompilátorem throw; jinak má hodnotu false. Typ `T` je zkonstruovatelný Pokud za definicí proměnné `T t(std::declval<Args>()...);` je ve správném formátu. Obě `T` a všechny typy v `Args` musí být úplný typy `void`, nebo pole neznámé hranice.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)


