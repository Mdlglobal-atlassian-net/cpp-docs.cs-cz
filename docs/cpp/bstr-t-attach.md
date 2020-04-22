---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 718efb9e3dac0d776678fe9efd912a602e041659
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749698"
---
# <a name="_bstr_tattach"></a>_bstr_t::Attach

**Specifické pro Microsoft**

Propojuje obálku `_bstr_t` s `BSTR`.

## <a name="syntax"></a>Syntaxe

```cpp
void Attach(
   BSTR s
);
```

#### <a name="parameters"></a>Parametry

*S*<br/>
Proměnná `BSTR`, která má být přidružena nebo přiřazena k proměnné `_bstr_t`.

## <a name="remarks"></a>Poznámky

Pokud byla proměnná `_bstr_t` dříve připojena k jiné proměnné `BSTR`, vyčistí proměnná `_bstr_t` prostředky proměnné `BSTR`, pokud žádné jiné proměnné `_bstr_t` nepoužívají proměnnou `BSTR`.

## <a name="example"></a>Příklad

Viz [_bstr_t::Přiřazení](../cpp/bstr-t-assign.md) příkladu pomocí **připojit**.

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[_bstr_t – třída](../cpp/bstr-t-class.md)
