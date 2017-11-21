---
title: next_permutation (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::next_permutation
dev_langs: C++
helpviewer_keywords: next_permutation function [STL/CLR]
ms.assetid: e36e821f-4b8d-461b-8074-69cd0175ccec
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 073aef1aa8e18ecbefe0c0816785c4f67af84244
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nextpermutation-stlclr"></a>next_permutation (STL/CLR)
Znovu uspořádá prvky v rozsahu tak, aby původní pořadí bylo nahrazeno lexikograficky následující větší permutací, pokud existuje, kde význam následujícího může být určen binárním predikátem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _BidIt> inline  
    bool next_permutation(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `next_permutation`. Další informace najdete v tématu [next_permutation](../standard-library/algorithm-functions.md#next_permutation).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)