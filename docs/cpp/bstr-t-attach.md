---
title: _bstr_t::Attach | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1eddbc7a01be66430759bb84c3ce6d840f37d098
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111209"
---
# <a name="bstrtattach"></a>_bstr_t::Attach

**Specifické pro Microsoft**

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