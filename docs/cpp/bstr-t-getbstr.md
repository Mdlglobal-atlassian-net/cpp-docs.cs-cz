---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: da438c65256d9a7e5bf5b02e108fee1385171d2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181210"
---
# <a name="_bstr_tgetbstr"></a>_bstr_t::GetBSTR

**Specifické pro společnost Microsoft**

Odkazuje na začátek `BSTR` zabalených `_bstr_t`.

## <a name="syntax"></a>Syntaxe

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>Návratová hodnota

Začátek `BSTR` zabalený `_bstr_t`.

## <a name="remarks"></a>Poznámky

**GetBSTR** má vliv na všechny `_bstr_t` objekty, které sdílejí `BSTR`. Více než jeden `_bstr_t` může sdílet `BSTR` prostřednictvím použití kopírovacího konstruktoru a **operátoru =** .

## <a name="example"></a>Příklad

Příklad použití **GetBSTR**naleznete v tématu [_Bstr_t:: Assign](../cpp/bstr-t-assign.md) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_bstr_t – třída](../cpp/bstr-t-class.md)
