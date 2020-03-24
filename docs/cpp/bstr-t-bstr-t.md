---
title: _bstr_t::_bstr_t
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::_bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
ms.openlocfilehash: 3384da733586c828496a8728a0f5855f92eeec35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190466"
---
# <a name="_bstr_t_bstr_t"></a>_bstr_t::_bstr_t

**Specifické pro společnost Microsoft**

Vytvoří objekt `_bstr_t`.

## <a name="syntax"></a>Syntaxe

```
_bstr_t( ) throw( );
_bstr_t(
   const _bstr_t& s1
) throw( );
_bstr_t(
   const char* s2
);
_bstr_t(
   const wchar_t* s3
);
_bstr_t(
   const _variant_t& var
);
_bstr_t(
   BSTR bstr,
   bool fCopy
);
```

#### <a name="parameters"></a>Parametry

*S1*<br/>
Objekt `_bstr_t`, který se má zkopírovat

*S2*<br/>
Vícebajtový řetězec.

*stavu*<br/>
Řetězec Unicode

*var*<br/>
Objekt [_variant_t](../cpp/variant-t-class.md) .

*BSTR*<br/>
Existující objekt `BSTR`.

*fCopy*<br/>
Je-li nastavena hodnota FALSE, je argument *BSTR* připojen k novému objektu bez vytvoření kopie voláním `SysAllocString`.

## <a name="remarks"></a>Poznámky

Následující tabulka popisuje konstruktory `_bstr_t`.

|Konstruktor|Popis|
|-----------------|-----------------|
|`_bstr_t( )`|Vytvoří výchozí objekt `_bstr_t`, který zapouzdřuje null objekt `BSTR`.|
|`_bstr_t( _bstr_t&`  `s1`  `)`|Vytvoří objekt `_bstr_t` jako kopii jiného objektu.<br /><br /> Jedná se o *neomezený* výtisk, který zvýší počet odkazů zapouzdřeného objektu `BSTR` místo vytvoření nového.|
|`_bstr_t( char*`  `s2`  `)`|Vytvoří objekt `_bstr_t` voláním `SysAllocString` k vytvoření nového objektu `BSTR` a jeho zapouzdřením.<br /><br /> Tento konstruktor nejdříve provede vícebajtový převod na kódování Unicode.|
|`_bstr_t( wchar_t*`  `s3`  `)`|Vytvoří objekt `_bstr_t` voláním `SysAllocString` k vytvoření nového objektu `BSTR` a jeho zapouzdřením.|
|`_bstr_t( _variant_t&`  `var`  `)`|Vytvoří objekt `_bstr_t` z objektu `_variant_t` tím, že nejprve načte objekt `BSTR` z zapouzdřeného objektu VARIANT.|
|`_bstr_t( BSTR``bstr` `, bool``fCopy``)`|Vytvoří objekt `_bstr_t` z existující `BSTR` (na rozdíl od `wchar_t*`ho řetězce). Pokud má *fCopy* hodnotu false, je zadaný `BSTR` připojen k novému objektu bez vytvoření nové kopie pomocí `SysAllocString`.<br /><br /> Tento konstruktor je používán funkcemi obálky v hlavičkách knihovny typů k zapouzdření a převzetí vlastnictví `BSTR`, který je vrácen metodou rozhraní.|

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_bstr_t – třída](../cpp/bstr-t-class.md)<br/>
[_variant_t – třída](../cpp/variant-t-class.md)
