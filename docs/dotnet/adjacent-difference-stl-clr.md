---
title: adjacent_difference (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::adjacent_difference
dev_langs: C++
helpviewer_keywords: adjacent_difference function
ms.assetid: 2b462e2e-b8f2-4b2e-9b87-5f688d8da9f4
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0be63f7032de5f6d3def4ba74f24a346785b7391
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="adjacentdifference-stlclr"></a>adjacent_difference (STL/CLR)
Vypočítá po sobě následující rozdíly mezi každým prvkem a jeho předchůdcem ve vstupním rozsahu a vydá výsledky do cílového rozsahu nebo vypočte výsledek zobecněné procedury, kde je operace rozdílu nahrazena jinou zadanou binární operací.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako číselné funkce standardní knihovny C++ `adjacent_difference`. Další informace najdete v tématu [adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo číselný >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [číselný (STL/CLR)](../dotnet/numeric-stl-clr.md)