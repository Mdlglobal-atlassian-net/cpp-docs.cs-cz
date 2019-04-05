---
title: pointer_default – (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: 37bd2b16fb7a7c1c186f59897898e08cc73fffae
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022663"
---
# <a name="pointerdefault"></a>pointer_default

Určuje výchozí atribut ukazatele pro všechny odkazy, s výjimkou ukazatelů nejvyšší úrovně, které se zobrazí v seznamech parametrů.

## <a name="syntax"></a>Syntaxe

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Parametry

*value*<br/>
Hodnota, která popisuje typ ukazatele: **ptr**, **ref**, nebo **jedinečný**.

## <a name="remarks"></a>Poznámky

**Pointer_default –** C++ atribut má stejné funkce jako [pointer_default –](/windows/desktop/Midl/pointer-default) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [defaultvalue](defaultvalue.md) ukázkový používání **pointer_default –**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**rozhraní**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)