---
title: partial_sum (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- cliext::partial_sum
dev_langs:
- C++
helpviewer_keywords:
- partial_sum function [STL/CLR]
ms.assetid: 845badae-8519-4ac8-9ea7-2b921bac7c51
caps.latest.revision: 4
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7200fbf4adb7866125cfd8956b7b35ad5d5a2657
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="partialsum-stlclr"></a>partial_sum (STL/CLR)
Vypočítá řadu součtů ve vstupní oblasti z první prvek prostřednictvím `i`element TD a ukládá výsledek každé součet v `i`element TD cílového rozsahu nebo vypočítá výsledek obecný postup kde operaci součet je nahrazena jinou zadaný binární operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako číselné funkce standardní knihovny C++ `partial_sum`. Další informace najdete v tématu [partial_sum](../standard-library/numeric-functions.md#partial_sum).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo číselný >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)