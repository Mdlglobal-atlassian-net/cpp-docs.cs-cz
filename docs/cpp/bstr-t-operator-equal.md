---
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 97f0100d8a34253f3a1375d34b887d3d31a77f43
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432575"
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =

**Specifické pro Microsoft**

Přiřadí novou hodnotu do existujícího `_bstr_t` objektu.

## <a name="syntax"></a>Syntaxe

```
_bstr_t& operator=(const _bstr_t& s1) throw ( );
_bstr_t& operator=(const char* s2);
_bstr_t& operator=(const wchar_t* s3);
_bstr_t& operator=(const _variant_t& var);
```

#### <a name="parameters"></a>Parametry

*S1*<br/>
A `_bstr_t` objektu má být přiřazena k existujícímu `_bstr_t` objektu.

*S2*<br/>
Vícebajtový řetězec má být přiřazena k existujícímu `_bstr_t` objektu.

*S3*<br/>
Řetězec znaků Unicode má být přiřazena k existujícímu `_bstr_t` objektu.

*var*<br/>
A `_variant_t` objektu má být přiřazena k existujícímu `_bstr_t` objektu.

**Specifické pro END Microsoft**

## <a name="example"></a>Příklad

Zobrazit [_bstr_t::Assign](../cpp/bstr-t-assign.md) pro příklad použití **operátoru =**.

## <a name="see-also"></a>Viz také:

[_bstr_t – třída](../cpp/bstr-t-class.md)