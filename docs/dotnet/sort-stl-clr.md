---
title: "řazení (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::sort
dev_langs: C++
helpviewer_keywords: sort function [STL/CLR]
ms.assetid: e30f3e97-60c4-4a8e-89f1-75ec056f587a
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eed713de1f73fcf96c7327f583079f24a2379b8d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="sort-stlclr"></a>sort (STL/CLR)
Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _RanIt> inline  
    void sort(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void sort(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `sort`. Další informace najdete v tématu [řazení](../mfc/reference/cmfclistctrl-class.md#sort).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)