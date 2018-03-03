---
title: _bstr_t::GetBSTR | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetBSTR
dev_langs:
- C++
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00b2f7f487673c67aa7b681499462ea05a471b48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR
**Konkrétní Microsoft**  
  
 Odkazuje na začátku `BSTR` zabalený pomocí `_bstr_t`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BSTR& GetBSTR( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Na začátek `BSTR` zabalený pomocí `_bstr_t`.  
  
## <a name="remarks"></a>Poznámky  
 Funkce `GetBSTR` ovlivňuje všechny objekty `_bstr_t` sdílející objekt `BSTR`. Objekt `_bstr_t` může být sdílen více než jedním objektem `BSTR` prostřednictvím kopírovacího konstruktoru a operátoru `operator=` and.  
  
## <a name="example"></a>Příklad  
 V tématu [_bstr_t::Assign](../cpp/bstr-t-assign.md) pro příklad použití `GetBSTR`.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_bstr_t – třída](../cpp/bstr-t-class.md)