---
title: "jedinečné (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::unique
dev_langs: C++
helpviewer_keywords: unique function [STL/CLR]
ms.assetid: 833cc314-b452-4659-bbb4-575c2bb63855
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6336a5579be9172caf6addd89e8b3b1b022151db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="unique-stlclr"></a>unique (STL/CLR)
Odstraní duplicitní prvky, které v zadaném rozsahu sousedí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt> inline  
    _FwdIt unique(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt unique(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `unique`. Další informace najdete v tématu [jedinečný](../standard-library/algorithm-functions.md#unique).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)