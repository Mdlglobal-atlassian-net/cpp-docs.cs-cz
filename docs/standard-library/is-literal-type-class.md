---
title: "is_literal_type třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_literal_type
dev_langs: C++
helpviewer_keywords: is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aabb7d1c6e0c194f5d031e62d84753dfc0ded3d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="isliteraltype-class"></a>is_literal_type – třída
Kontroluje, zda typ lze použít jako `constexpr` proměnné nebo sestavený, používá nebo vrácená z `constexpr` funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
struct is_literal_type;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je *typu literálu*, jinak má hodnotu false. Typ literálu je buď `void`, skalárního typu, typu odkazu, pole literálu typu nebo typu literálu třídy. Typ literálu třídy je typu třídy, který má trivial – destruktor, je typ agregace nebo má alespoň jeden jiný přesunutí, bez kopírování `constexpr` konstruktor a všechny jeho základní třídy a nestatické datových členů jsou typy literálu stálé. Typ literál je vždy typu literálu, koncept typu literálu obsahuje všechno, co kompilátor můžete vyhodnotit jako `constexpr` v době kompilace.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



