---
title: _bstr_t::Operator += + | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
dev_langs:
- C++
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a440e8b8d078c7849de2a0b29f1d50b140d70070
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044766"
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=, +

**Specifické pro Microsoft**

Připojí znaky na konec objektu `_bstr_t` objektu nebo spojuje dva řetězce.

## <a name="syntax"></a>Syntaxe

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a>Parametry

*S1*<br/>
A `_bstr_t` objektu.

*S2*<br/>
Vícebajtový řetězec.

*S3*<br/>
Řetězec znaků Unicode.

## <a name="remarks"></a>Poznámky

Tyto operátory provádějí zřetězení řetězců:

- **+= – operátor (***s1***)** připojí znaky v zapouzdřeného `BSTR` z *s1* na konec tohoto objektu zapouzdřený `BSTR`.

- **Operator + (***s1***)** vrátí nový `_bstr_t` zřetězením tento objekt, který je vytvořen `BSTR` se specifikací *s1*.

- **Operator + (***s2***&#124;***s1***)** vrátí nový `_bstr_t` , který je vytvořený zřetězením vícebajtový řetězec *s2*, převedeno na kódování Unicode, se `BSTR` zapouzdřena v *s1*.

- **Operator + (***s3* **,***s1***)** vrátí nový `_bstr_t` , který je vytvořen pomocí zřetězení řetězců kódování Unicode *s3* s `BSTR` zapouzdřena v *s1*.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_bstr_t – třída](../cpp/bstr-t-class.md)