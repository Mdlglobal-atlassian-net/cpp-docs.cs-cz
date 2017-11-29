---
title: "result_of – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
dev_langs: C++
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3d48ed78b221217fd132592521481922c15c949d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="resultof-class"></a>result_of – třída
Určuje návratový typ s typ, který má zadané typy argumentů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class>  
struct result_of; // Causes a static assert  
  
template <class Fn, class... ArgTypes>  
struct result_of<Fn(ArgTypes...)>;

// Helper type  
template<class T>
   using result_of_t = typename result_of<T>::type;
```  
  
#### <a name="parameters"></a>Parametry  
 `Fn`  
 S typ dotazu.  
  
 `ArgTypes`  
 Typy seznam argumentů s typ dotazu.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí této šablony můžete určit výsledný typ při kompilaci `Fn`(`ArgTypes`), kde `Fn` je možné volat typu, odkaz na funkci nebo odkaz na s typu, vyvolá pomocí seznam argumentů typů v `ArgTypes`. `type` Názvů výsledný typ členů třídy šablony `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` Pokud unevaluated výraz `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` je ve správném formátu. Jinak hodnota šablony třída nemá žádné člen `type`. Typ `Fn` a všechny typy v parametru pack `ArgTypes` musí být úplný typy `void`, nebo pole neznámé hranice.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)


