---
title: "equal_range – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::equal_range
dev_langs: C++
helpviewer_keywords: equal_range function [STL/CLR]
ms.assetid: 1b2e76c3-6b52-486d-9785-2639b54277fd
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6b94388f233c8ffb6577d88e137245475c3656de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="equalrange-stlclr"></a>equal_range (STL/CLR)
Najde dvojici pozic v seřazeném rozsahu. První bude menší nebo rovna pozici zadaného prvku a druhá větší než pozice prvku, kde smysl ekvivalence nebo řazení použitý k určení pozic v sekvenci může být určen binárním predikátem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt, class _Ty> inline  
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `equal_range`. Další informace najdete v tématu [equal_range –](../standard-library/algorithm-functions.md#equal_range).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)