---
title: Count (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::count
dev_langs:
- C++
helpviewer_keywords:
- count function [STL/CLR]
ms.assetid: 6d10abb4-3c48-469c-804c-281015b12865
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ce8169f5a9fa5ac7f483921bc6c261ffbc4e8842
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="count-stlclr"></a>count (STL/CLR)
Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané hodnotě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt, class _Ty> inline  
    typename iterator_traits<_InIt>::difference_type  
        count(_InIt _First, _InIt _Last, const _Ty% _Val);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `count`. Další informace najdete v tématu [počet](../standard-library/algorithm-functions.md#count).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)