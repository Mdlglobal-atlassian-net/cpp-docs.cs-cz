---
title: '&lt;ostream –&gt; – definice TypeDef | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 3f5511cfbf73ddf74fa12954e1a108d8accf875e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream –&gt; – definice TypeDef

|||
|-|-|
|[ostream –](#ostream)|[wostream –](#wostream)|

## <a name="ostream"></a>  ostream –

Umožňuje vytvořit typ ze basic_ostream, který se specializuje na `char` a `char_traits` specializované na `char`.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ostream](../standard-library/basic-ostream-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.

## <a name="wostream"></a>  wostream –

Umožňuje vytvořit typ ze basic_ostream, který se specializuje na `wchar_t` a `char_traits` specializované na `wchar_t`.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ostream](../standard-library/basic-ostream-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.

## <a name="see-also"></a>Viz také

[\<ostream – >](../standard-library/ostream.md)<br/>
