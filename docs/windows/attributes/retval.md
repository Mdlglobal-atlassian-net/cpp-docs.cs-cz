---
title: retval (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: 2a2865c1eda229f1a2fcd457c22119b2908c1caa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514044"
---
# <a name="retval"></a>retval

Určuje parametr, který přijímá vrácenou hodnotu člena.

## <a name="syntax"></a>Syntaxe

```cpp
[retval]
```

## <a name="remarks"></a>Poznámky

Atribut **retval** C++ má stejné funkce jako atribut [retval](/windows/win32/Midl/retval) MIDL.

parametr **retval** musí být uveden v posledním argumentu v deklaraci funkce.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [vázání](bindable.md) pro použití vzorku **retval**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Parametr rozhraní, metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|**out**|
|**Neplatné atributy**|**in**|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[Atributy metody](method-attributes.md)