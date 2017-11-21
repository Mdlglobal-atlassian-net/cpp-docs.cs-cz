---
title: "vyhledávání (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::search
dev_langs: C++
helpviewer_keywords: search function [STL/CLR]
ms.assetid: 3317c7f4-9f47-44b8-a7c7-73948a2f83e1
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1b7228bc8c44c9cb6996a65aa4c558d8e4f99e32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="search-stlclr"></a>search (STL/CLR)
Vyhledá první výskyt sekvence v cílovém rozsahu, jejíž prvky jsou rovné prvkům v dané sekvenci prvků nebo jejíž prvky jsou ekvivalentní ve smyslu určeném binárním predikátem prvkům v dané sekvenci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `search`. Další informace najdete v tématu [vyhledávání](../standard-library/algorithm-functions.md#search).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)