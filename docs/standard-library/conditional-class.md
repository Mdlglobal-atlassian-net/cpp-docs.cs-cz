---
title: "Conditional – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::conditional
dev_langs:
- C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4c0c6deb6a7167852101efba30a978aee78f96f9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="conditional-class"></a>conditional – třída
Vybere jeden ze dvou typů v závislosti na zadané podmínce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <bool B, class T1, class T2>  
struct conditional;

template <bool _Test, class _T1, class _T2>  
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```  
  
#### <a name="parameters"></a>Parametry  
 `B`  
 Hodnota, která určuje vybraný typ.  
  
 `T1`  
 Výsledek typu, pokud B hodnotu true.  
  
 `T2`  
 Výsledek typu při B je false.  
  
## <a name="remarks"></a>Poznámky  
 Typedef člen šablony `conditional<B, T1, T2>::type` vyhodnotí jako `T1` při `B` vyhodnotí jako `true`a vyhodnocuje `T2` při `B` vyhodnocuje `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



