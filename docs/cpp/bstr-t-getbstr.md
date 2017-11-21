---
title: _bstr_t::GetBSTR | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t::GetBSTR
dev_langs: C++
helpviewer_keywords: GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7b8a66c9bf40ccb1467b0679f567a79bfd065315
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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