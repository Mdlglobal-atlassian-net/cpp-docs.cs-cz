---
title: "decay – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::decay
dev_langs:
- C++
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d43ee8ff7971af3026066b3483de4808ec2dc114
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="decay-class"></a>decay – třída
Vytvoří typ jako předaná hodnota. Díky bez – odkaz na typ, není const, stálé nebo je ukazatel typu z funkce nebo typ pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>
struct decay;

template <class T>  
using decay_t = typename decay<T>::type;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, který chcete upravit.  
  
## <a name="remarks"></a>Poznámky  
 Šablona decay slouží k vytvoření výsledný typ, jako kdyby byl předán typ podle hodnoty jako argument. Typedef člena třídy šablony `type` obsahuje upravené typ, který je definován v těchto fází:  
  
-   Typ `U` je definován jako `remove_reference<T>::type`.  
  
-   Pokud `is_array<U>::value` má hodnotu true, typ upravené `type` je `remove_extent<U>::type *`.  
  
-   Jinak Pokud `is_function<U>::value` má hodnotu true, typ upravené `type` je `add_pointer<U>::type`.  
  
-   Jinak upravené typ `type` je `remove_cv<U>::type`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



