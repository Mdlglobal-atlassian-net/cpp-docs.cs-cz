---
title: "find_first_of – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::find_first_of
dev_langs: C++
helpviewer_keywords: find_first_of function [STL/CLR]
ms.assetid: d559bad4-fc12-4201-af49-db0e7eec48e8
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 473c2c5314cb8508fbcbff125e58956b0fb29630
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="findfirstof-stlclr"></a>find_first_of (STL/CLR)
Vyhledá první výskyt jedné z několika hodnot v cílovém rozsahu nebo první výskyt jednoho z několika prvků, které jsou ekvivalentní ve smyslu určeném binárním predikátem zadané sadě prvků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `find_first_of`. Další informace najdete v tématu [find_first_of –](../standard-library/algorithm-functions.md#find_first_of).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)