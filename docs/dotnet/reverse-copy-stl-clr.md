---
title: "reverse_copy – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::reverse_copy
dev_langs: C++
helpviewer_keywords: reverse_copy function [STL/CLR]
ms.assetid: 694e577a-0fa8-44f7-adde-6dd9f45adefd
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 69dbf8a9ff6c240d02e5f38ed4ed4d5f6bfcf072
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="reversecopy-stlclr"></a>reverse_copy (STL/CLR)
Obrátí pořadí prvků v rámci zdrojový rozsah při kopírování do cílové oblasti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _BidIt, class _OutIt> inline  
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `reverse_copy`. Další informace najdete v tématu [reverse_copy –](../standard-library/algorithm-functions.md#reverse_copy).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)