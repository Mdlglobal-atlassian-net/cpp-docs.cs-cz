---
title: retval (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: 5aded4588614eb4171e31a588f125ea8aa8de7ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166338"
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

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[Atributy metody](method-attributes.md)
