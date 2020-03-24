---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 1fe8cfb5b644b3c7c34cf3325a91ebdf23a04946
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190323"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Specifické pro společnost Microsoft**

Vytvoří kopii zapouzdřeného `BSTR`.

## <a name="syntax"></a>Syntaxe

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>Parametry

*fCopy*<br/>
Je-li nastavena hodnota TRUE, funkce **copy** vrátí kopii obsažené `BSTR`, jinak **Kopírovat** vrátí skutečný objekt BSTR.

## <a name="remarks"></a>Poznámky

Vrátí nově přidělenou kopii zapouzdřeného objektu `BSTR`.

## <a name="example"></a>Příklad

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_bstr_t – třída](../cpp/bstr-t-class.md)
