---
title: _bstr_t::GetAddress | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c1b2b348277f7d33a32c8d0e6ad1fc80d51ec68d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress
**Konkrétní Microsoft**  
  
 Uvolní všechny existující řetězce a vrátí adresu řetězce s nově přidělenou pamětí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na objekt `BSTR` obalený objektem `_bstr_t`.  
  
## <a name="remarks"></a>Poznámky  
 Funkce `GetAddress` ovlivňuje všechny objekty `_bstr_t` sdílející objekt `BSTR`. Objekt `_bstr_t` může být sdílen více než jedním objektem `BSTR` prostřednictvím kopírovacího konstruktoru a operátoru `operator=` and.  
  
## <a name="example"></a>Příklad  
 V tématu [_bstr_t::Assign](../cpp/bstr-t-assign.md) příklad použití `GetAddress`.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_bstr_t – třída](../cpp/bstr-t-class.md)