---
title: _bstr_t::GetBSTR | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetBSTR
dev_langs:
- C++
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8863f3a6c37693ec28f931c2af4cb0d299788daa
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402660"
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR
**Specifické pro Microsoft**  
  
 Odkazuje na začátku `BSTR` uzavřenou `_bstr_t`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BSTR& GetBSTR( );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Na začátek `BSTR` uzavřenou `_bstr_t`.  
  
## <a name="remarks"></a>Poznámky  
 **Getbstr –** ovlivní všechny `_bstr_t` objekty tuto sdílenou složku `BSTR`. Více než jeden `_bstr_t` můžete sdílet `BSTR` prostřednictvím kopírovacího konstruktoru a a **operátoru =**.  
  
## <a name="example"></a>Příklad  
 Zobrazit [_bstr_t::Assign](../cpp/bstr-t-assign.md) příklad použití **getbstr –**.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_bstr_t – třída](../cpp/bstr-t-class.md)