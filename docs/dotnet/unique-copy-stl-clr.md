---
title: "unique_copy – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::unique_copy
dev_langs: C++
helpviewer_keywords: unique_copy function [STL/CLR]
ms.assetid: 37aa5b06-42c5-420d-94c5-00f00ad26471
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 521e45ab81e9d164e38c1ae9af8b7d0cf1048b4a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="uniquecopy-stlclr"></a>unique_copy (STL/CLR)
Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu s výjimkou sousedících duplicitních prvků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Pr> inline  
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `unique_copy`. Další informace najdete v tématu [unique_copy –](../standard-library/algorithm-functions.md#unique_copy).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)