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
ms.openlocfilehash: 0a2c374fc160a0575e0a17cc85ab51c65fa9392a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390826"
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=, +

**Microsoft Specific**

Připojí znaky na konec objektu `_bstr_t` objektu nebo spojuje dva řetězce.

## <a name="syntax"></a>Syntaxe

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a>Parametry

*s1*<br/>
A `_bstr_t` objektu.

*s2*<br/>
Vícebajtový řetězec.

*s3*<br/>
Řetězec znaků Unicode.

## <a name="remarks"></a>Poznámky

Tyto operátory provádějí zřetězení řetězců:

- **+= – operátor (**  *s1*  **)** připojí znaky v zapouzdřeného `BSTR` z *s1* na konec tohoto objektu zapouzdřený `BSTR`.

- **Operator + (**   *s1*  **)** vrátí nový `_bstr_t` zřetězením tento objekt, který je vytvořen `BSTR` se specifikací *s1*.

- **Operator + (**  *s2*  **&#124;**  *s1*  **)** vrátí nový `_bstr_t` , který je vytvořený zřetězením vícebajtový řetězec *s2*, převedeno na kódování Unicode, se `BSTR` zapouzdřena v *s1*.

- **Operator + (**  *s3* **,**  *s1*  **)** vrátí nový `_bstr_t` , který je vytvořen pomocí zřetězení řetězců kódování Unicode *s3* s `BSTR` zapouzdřena v *s1*.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_bstr_t – třída](../cpp/bstr-t-class.md)