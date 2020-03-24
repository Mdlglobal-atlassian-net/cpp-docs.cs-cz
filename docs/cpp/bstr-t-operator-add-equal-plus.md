---
title: _bstr_t::operator +=, +
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
ms.openlocfilehash: b9eddca85d66f4978e1b33299ca655cd880cf45e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181145"
---
# <a name="_bstr_toperator--"></a>_bstr_t::operator +=, +

**Specifické pro společnost Microsoft**

Připojí znaky na konec objektu `_bstr_t` nebo zřetězí dva řetězce.

## <a name="syntax"></a>Syntaxe

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a>Parametry

*S1*<br/>
Objekt `_bstr_t`.

*S2*<br/>
Vícebajtový řetězec.

*stavu*<br/>
Řetězec Unicode.

## <a name="remarks"></a>Poznámky

Tyto operátory provádějí zřetězení řetězců:

- **operator + = (**  *S1*  **)** – operátor Připojí znaky v zapouzdřených `BSTR` *S1* na konec zapouzdřené `BSTR`tohoto objektu.

- **operator + (**  *S1*  **)** – operátor Vrátí novou `_bstr_t` vytvořenou zřetězením `BSTR` tohoto objektu s vlastností *S1*.

- **operator + (**  *S2*  **&#124;**  *S1*  **)** Vrátí novou `_bstr_t` vytvořenou zřetězením vícebajtového řetězce *S2*, převedeného do kódování Unicode s `BSTR` zapouzdřenou v *S1*.

- **operator + (**  *S3* **,**  *S1*  **)** Vrátí nový `_bstr_t`, který se vytvoří tak, že zřetězí řetězec *S3* ve formátu Unicode s `BSTR` zapouzdřeným ve *S1*.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_bstr_t – třída](../cpp/bstr-t-class.md)
