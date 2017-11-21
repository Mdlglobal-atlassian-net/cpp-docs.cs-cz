---
title: Generovat (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::generate
dev_langs: C++
helpviewer_keywords: generate function [STL/CLR]
ms.assetid: 970f209f-31db-47c4-a0bb-4c3e579adb52
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2a2941894e6aa63708f9878abbf33f1335f812ef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="generate-stlclr"></a>generate (STL/CLR)
Přiřadí hodnoty generované objektem funkce každému prvku v rozsahu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt, class _Fn0> inline  
    void generate(_FwdIt _First, _FwdIt _Last, _Fn0 _Func);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `generate`. Další informace najdete v tématu [generovat](../standard-library/algorithm-functions.md#generate).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)