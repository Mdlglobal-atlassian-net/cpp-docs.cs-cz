---
title: "inner_product – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::inner_product
dev_langs: C++
helpviewer_keywords: inner_product function [STL/CLR]
ms.assetid: 97d7a507-7494-4216-aedf-0546ed0edb3f
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d10b4b3b62c135e110f63acb555691c256450491
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="innerproduct-stlclr"></a>inner_product (STL/CLR)
Vypočítá součet element-wise součin dvou rozsahy a přidává ji k zadaná počáteční hodnota nebo vypočítá výsledek obecný postup kde binárních operací sum a produktu jsou nahrazovány jiné zadaný binární operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt1, class _InIt2, class _Ty> inline  
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Ty _Val);  
template<class _InIt1, class _InIt2, class _Ty, class _Fn21,  
       class _Fn22> inline  
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Ty _Val, _Fn21 _Func1, _Fn22 _Func2);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako číselné funkce standardní knihovny C++ `inner_product`. Další informace najdete v tématu [inner_product –](../standard-library/numeric-functions.md#inner_product).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo číselný >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [číselný (STL/CLR)](../dotnet/numeric-stl-clr.md)