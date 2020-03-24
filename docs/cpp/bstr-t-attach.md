---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 3b52661097ca1feab4c8045be240e4138a0c0f21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190623"
---
# <a name="_bstr_tattach"></a>_bstr_t::Attach

**Specifické pro společnost Microsoft**

Propojí `_bstr_t` obálku s `BSTR`.

## <a name="syntax"></a>Syntaxe

```
void Attach(
   BSTR s
);
```

#### <a name="parameters"></a>Parametry

*pracují*<br/>
Proměnná `BSTR`, která má být přidružena nebo přiřazena k proměnné `_bstr_t`.

## <a name="remarks"></a>Poznámky

Pokud byla proměnná `_bstr_t` dříve připojena k jiné proměnné `BSTR`, vyčistí proměnná `_bstr_t` prostředky proměnné `BSTR`, pokud žádné jiné proměnné `_bstr_t` nepoužívají proměnnou `BSTR`.

## <a name="example"></a>Příklad

Příklad použití **připojení**naleznete v tématu [_Bstr_t:: Assign](../cpp/bstr-t-assign.md) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_bstr_t – třída](../cpp/bstr-t-class.md)
