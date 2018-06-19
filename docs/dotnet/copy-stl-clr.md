---
title: kopírování (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::copy
dev_langs:
- C++
helpviewer_keywords:
- copy function [STL/CLR]
ms.assetid: f6738535-fde6-446e-a797-bf2b457c2bff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6946868f80a3a655acf32eba80e2fc6f95c0cd71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105709"
---
# <a name="copy-stlclr"></a>copy (STL/CLR)
Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dopředu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se chová stejně jako funkce standardní knihovny C++ `copy`. Další informace najdete v tématu [kopie](http://msdn.microsoft.com/Library/f1fec7da-e01b-40f1-b5bd-6b81e304cae1).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)