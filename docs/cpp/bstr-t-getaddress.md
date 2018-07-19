---
title: _bstr_t::GetAddress | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4895153abe248265e0aacfbe636b9a4bd46ed205
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941194"
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress
**Specifické pro Microsoft**  
  
 Uvolní všechny existující řetězce a vrátí adresu řetězce s nově přidělenou pamětí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na objekt `BSTR` obalený objektem `_bstr_t`.  
  
## <a name="remarks"></a>Poznámky  
 Funkce `GetAddress` ovlivňuje všechny objekty `_bstr_t` sdílející objekt `BSTR`. Více než jeden `_bstr_t` můžete sdílet `BSTR` prostřednictvím kopírovacího konstruktoru a a **operátoru =**.  
  
## <a name="example"></a>Příklad  
 Zobrazit [_bstr_t::Assign](../cpp/bstr-t-assign.md) příklad použití `GetAddress`.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [_bstr_t – třída](../cpp/bstr-t-class.md)