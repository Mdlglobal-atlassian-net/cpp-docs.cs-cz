---
title: set_difference – (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set_difference
dev_langs:
- C++
helpviewer_keywords:
- set_difference function [STL/CLR]
ms.assetid: 47a34d92-53d7-4065-9302-9e2e70e46c4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 057b56c44df50fdd3c59a689650262e5e952f359
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="setdifference-stlclr"></a>set_difference (STL/CLR)
Sjednotí všechny prvky, které patří do jednoho seřazeného zdrojového rozsahu, ale nikoli do druhého seřazeného zdrojového rozsahu, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2,_OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `set_difference`. Další informace najdete v tématu [set_difference –](../standard-library/algorithm-functions.md#set_difference).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)