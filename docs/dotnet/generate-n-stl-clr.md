---
title: generate_n – (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::generate_n
dev_langs:
- C++
helpviewer_keywords:
- generate_n function [STL/CLR]
ms.assetid: 2f56e649-7a6f-4861-ae49-d0b25f5cd50c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e0072d3694c058d0951e55b09ee6a2a376cbe94a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110609"
---
# <a name="generaten-stlclr"></a>generate_n (STL/CLR)
Přiřadí hodnoty generované objektem funkce zadanému počtu prvků v rozsahu a vrátí pozici prvku za poslední přiřazenou hodnotou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _OutIt, class _Diff, class _Fn0> inline  
    void generate_n(_OutIt _Dest, _Diff _Count, _Fn0 _Func);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `generate_n`. Další informace najdete v tématu [generate_n –](../standard-library/algorithm-functions.md#generate_n).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)