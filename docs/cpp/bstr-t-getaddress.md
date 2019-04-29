---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: 4d51539d2afbb2fbcc860b6c4d821df119aca418
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393893"
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress

**Microsoft Specific**

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