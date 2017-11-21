---
title: "remove_if – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::remove_if
dev_langs: C++
helpviewer_keywords: remove_if function [STL/CLR]
ms.assetid: de501d3f-965b-4a99-b833-f6fa303fbcdc
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a89698c11800f3943beb2ee47d01cc5506a538e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="removeif-stlclr"></a>remove_if (STL/CLR)
Odstraní prvky, které splňují predikát, z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt, class _Pr> inline  
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `remove_if`. Další informace najdete v tématu [remove_if –](../standard-library/algorithm-functions.md#remove_if).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)