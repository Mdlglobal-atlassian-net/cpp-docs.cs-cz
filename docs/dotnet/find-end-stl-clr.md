---
title: "find_end – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::find_end
dev_langs: C++
helpviewer_keywords: find_end function [STL/CLR]
ms.assetid: a2008414-163a-4da2-9ac6-4e3c85a02d38
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b7a758c690d1ddb2cda6d6265b6a65c80bd46322
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="findend-stlclr"></a>find_end (STL/CLR)
Vyhledá v rozsahu poslední dílčí sekvenci, která je shodná se zadanou sekvencí nebo která je ekvivalentní ve smyslu určeném binárním predikátem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `find_end`. Další informace najdete v tématu [find_end –](../standard-library/algorithm-functions.md#find_end).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)