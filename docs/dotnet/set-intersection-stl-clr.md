---
title: "set_intersection – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::set_intersection
dev_langs: C++
helpviewer_keywords: set_intersection function [STL/CLR]
ms.assetid: 8a799b20-55a5-4fba-a9c1-a48597cbdae6
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1102aac340973e57c560953d61ebd8050a8bcd14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="setintersection-stlclr"></a>set_intersection (STL/CLR)
Sjednotí všechny prvky, které náleží do obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `set_intersection`. Další informace najdete v tématu [set_intersection –](../standard-library/algorithm-functions.md#set_intersection).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)