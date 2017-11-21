---
title: "binary_search – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::binary_search
dev_langs: C++
helpviewer_keywords: binary_search function [STL/CLR]
ms.assetid: 520869cc-7cd3-4c81-b439-05f042474416
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e927620259befd53dacbd6b666414a43bd6feaf5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="binarysearch-stlclr"></a>binary_search (STL/CLR)
Ověřuje, zda v seřazeném rozsahu existuje prvek, který je roven zadané hodnotě nebo je jí ekvivalentní ve smyslu určeném binárním predikátem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt, class _Ty> inline  
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    bool binary_search(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `binary_search`. Další informace najdete v tématu [binary_search –](../standard-library/algorithm-functions.md#binary_search).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)