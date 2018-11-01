---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: 4d51539d2afbb2fbcc860b6c4d821df119aca418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601458"
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

**GetAddress** ovlivní všechny `_bstr_t` objekty tuto sdílenou složku `BSTR`. Více než jeden `_bstr_t` můžete sdílet `BSTR` prostřednictvím kopírovacího konstruktoru a **operátoru =**.

## <a name="example"></a>Příklad

Zobrazit [_bstr_t::Assign](../cpp/bstr-t-assign.md) příklad použití **GetAddress**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_bstr_t – třída](../cpp/bstr-t-class.md)