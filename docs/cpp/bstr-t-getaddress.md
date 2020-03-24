---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: ca78bd1b607ba4a86bbc824887a7ec767cd5476e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181249"
---
# <a name="_bstr_tgetaddress"></a>_bstr_t::GetAddress

**Specifické pro společnost Microsoft**

Uvolní všechny existující řetězce a vrátí adresu řetězce s nově přidělenou pamětí.

## <a name="syntax"></a>Syntaxe

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `BSTR` obalený objektem `_bstr_t`.

## <a name="remarks"></a>Poznámky

**GetAddress** má vliv na všechny `_bstr_t` objekty, které sdílejí `BSTR`. Více než jeden `_bstr_t` může sdílet `BSTR` prostřednictvím použití kopírovacího konstruktoru a **operátoru =** .

## <a name="example"></a>Příklad

Viz [_bstr_t:: Assign](../cpp/bstr-t-assign.md) pro příklad pomocí **GetAddress**.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_bstr_t – třída](../cpp/bstr-t-class.md)
