---
title: pop_heap – (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::pop_heap
dev_langs:
- C++
helpviewer_keywords:
- pop_heap function [STL/CLR]
ms.assetid: d9bde0ed-2122-4d83-b4b3-f47f6fb3729a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f33f2ff272cac40162777c457fc60e50adda87e5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33159285"
---
# <a name="popheap-stlclr"></a>pop_heap (STL/CLR)
Odstraní největší prvek z přední části haldy až do předposlední pozice v rozsahu a ze zbývajících prvků vytvoří novou haldu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _RanIt> inline  
    void pop_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void pop_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `pop_heap`. Další informace najdete v tématu [pop_heap –](../standard-library/algorithm-functions.md#pop_heap).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)