---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: cea3404e0732cb0e16b3fa9199ce95e3dfcc23f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618046"
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

**Getbstr –** ovlivní všechny `_bstr_t` objekty tuto sdílenou složku `BSTR`. Více než jeden `_bstr_t` můžete sdílet `BSTR` prostřednictvím kopírovacího konstruktoru a **operátoru =**.

## <a name="example"></a>Příklad

Zobrazit [_bstr_t::Assign](../cpp/bstr-t-assign.md) příklad použití **getbstr –**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_bstr_t – třída](../cpp/bstr-t-class.md)