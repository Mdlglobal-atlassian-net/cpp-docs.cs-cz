---
title: _bstr_t::copy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::copy
dev_langs:
- C++
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50f9a17c93849dec49c2c9a72825a5797d8c040c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068621"
---
# <a name="bstrtcopy"></a>_bstr_t::copy

**Specifické pro Microsoft**

Vytvoří kopii zapouzdřeného `BSTR`.

## <a name="syntax"></a>Syntaxe

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>Parametry

*fCopy*<br/>
Při hodnotě TRUE se **kopírování** vrátí kopii obsaženého objektu `BSTR`, jinak **kopírování** vrátí skutečný objekt BSTR.

## <a name="remarks"></a>Poznámky

Vrátí nově přidělenou kopii zapouzdřeného objektu `BSTR`.

## <a name="example"></a>Příklad

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_bstr_t – třída](../cpp/bstr-t-class.md)