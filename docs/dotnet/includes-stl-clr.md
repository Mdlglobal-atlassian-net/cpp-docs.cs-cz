---
title: zahrnuje (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::includes
dev_langs: C++
helpviewer_keywords: includes function [STL/CLR]
ms.assetid: 566307f4-92e0-4acc-ba49-caa48f3ec744
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 007eb0c908d37e3caa462dd51680d5062572b399
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="includes-stlclr"></a>includes (STL/CLR)
Ověřuje, zda jeden seřazený rozsah obsahuje všechny prvky obsažené ve druhém seřazeném rozsahu, kde kritérium pořadí nebo ekvivalence mezi prvky může být určeno binárním predikátem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt1, class _InIt2> inline  
    bool includes(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    bool includes(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `includes`. Další informace najdete v tématu [zahrnuje](../standard-library/algorithm-functions.md#includes).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)