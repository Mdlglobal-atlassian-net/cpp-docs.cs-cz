---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 8601ebbea6a9ab837c07518b018e83e8c0df226d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385060"
---
# <a name="bstrtattach"></a>_bstr_t::Attach

**Microsoft Specific**

Odkazy `_bstr_t` obálky `BSTR`.

## <a name="syntax"></a>Syntaxe

```
void Attach(
   BSTR s
);
```

#### <a name="parameters"></a>Parametry

*s*<br/>
Proměnná `BSTR`, která má být přidružena nebo přiřazena k proměnné `_bstr_t`.

## <a name="remarks"></a>Poznámky

Pokud byla proměnná `_bstr_t` dříve připojena k jiné proměnné `BSTR`, vyčistí proměnná `_bstr_t` prostředky proměnné `BSTR`, pokud žádné jiné proměnné `_bstr_t` nepoužívají proměnnou `BSTR`.

## <a name="example"></a>Příklad

Zobrazit [_bstr_t::Assign](../cpp/bstr-t-assign.md) příklad použití **připojit**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_bstr_t – třída](../cpp/bstr-t-class.md)