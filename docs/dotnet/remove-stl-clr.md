---
title: odebrat (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- cliext::remove
dev_langs:
- C++
helpviewer_keywords:
- remove function [STL/CLR]
ms.assetid: 85a11883-3e25-49aa-b4a0-b2cffd6dc110
caps.latest.revision: 4
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c866d920451cd9ae21d161630520813b699a3eff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="remove-stlclr"></a>remove (STL/CLR)
Odstraní zadanou hodnotu z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _FwdIt, class _Ty> inline  
    _FwdIt remove(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `remove`. Další informace najdete v tématu [odebrat](http://msdn.microsoft.com/Library/77e2585c-441e-448d-bd1d-c893d1356ed8).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)