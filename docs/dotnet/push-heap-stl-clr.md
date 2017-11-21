---
title: "push_heap – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::push_heap
dev_langs: C++
helpviewer_keywords: push_heap function [STL/CLR]
ms.assetid: 184fe1d9-5f75-4c11-adbb-84b6b5c8ecd3
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b04e0a52efd6f2a9923f9294efb3f4d48b29567a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="pushheap-stlclr"></a>push_heap (STL/CLR)
Přidá prvek, který je na konci rozsahu, do stávající haldy, která zahrnuje předchozí prvky daného rozsahu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _RanIt> inline  
    void push_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void push_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `push_heap`. Další informace najdete v tématu [push_heap –](../standard-library/algorithm-functions.md#push_heap).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)