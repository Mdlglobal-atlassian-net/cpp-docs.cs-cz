---
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 5b7f499dd84a67020232aab84966647378daadad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181067"
---
# <a name="_bstr_toperator-"></a>_bstr_t::operator =

**Specifické pro společnost Microsoft**

Přiřadí novou hodnotu existujícímu objektu `_bstr_t`.

## <a name="syntax"></a>Syntaxe

```
_bstr_t& operator=(const _bstr_t& s1) throw ( );
_bstr_t& operator=(const char* s2);
_bstr_t& operator=(const wchar_t* s3);
_bstr_t& operator=(const _variant_t& var);
```

#### <a name="parameters"></a>Parametry

*S1*<br/>
Objekt `_bstr_t`, který se má přiřadit existujícímu objektu `_bstr_t`.

*S2*<br/>
Vícebajtový řetězec, který má být přiřazen existujícímu objektu `_bstr_t`.

*stavu*<br/>
Řetězec v kódování Unicode, který má být přiřazen existujícímu objektu `_bstr_t`.

*var*<br/>
Objekt `_variant_t`, který se má přiřadit existujícímu objektu `_bstr_t`.

**Specifické pro konec Microsoftu**

## <a name="example"></a>Příklad

Příklad použití **operátoru =** získáte v tématu [_Bstr_t:: Assign](../cpp/bstr-t-assign.md) .

## <a name="see-also"></a>Viz také

[_bstr_t – třída](../cpp/bstr-t-class.md)
