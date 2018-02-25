---
title: "is_move_constructible třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15c1fb9b3b4e3dc27b887ac70005be55813399a7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ismoveconstructible-class"></a>is_move_constructible – třída
Ověřuje, zda má tento typ konstruktor move.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
struct is_move_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 T  
 Typ, který se má vyhodnotit  
  
## <a name="remarks"></a>Poznámky  
 Predikát typ, který se vyhodnotí na hodnotu true, pokud typ `T` lze sestavit pomocí operace přesunu. Tento predikát je ekvivalentní `is_constructible<T, T&&>`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



