---
title: "oddíl (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::partition
dev_langs: C++
helpviewer_keywords: partition function [STL/CLR]
ms.assetid: 3f551eb3-31ec-4b1d-b585-07718d6a1bd7
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2e03ef816e0334717724b04f95b0838068c077d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="partition-stlclr"></a>partition (STL/CLR)
Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _BidIt, class _Pr> inline  
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `partition`. Další informace najdete v tématu [oddílu](../standard-library/algorithm-functions.md#partition).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)