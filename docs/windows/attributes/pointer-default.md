---
title: pointer_default (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: d0c5832623c1e418f4c6e8bdb606d1d363503483
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166533"
---
# <a name="pointer_default"></a>pointer_default

Určuje výchozí atribut ukazatele pro všechny ukazatele s výjimkou ukazatelů nejvyšší úrovně, které se zobrazují v seznamech parametrů.

## <a name="syntax"></a>Syntaxe

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Parametry

*value*<br/>
Hodnota, která popisuje typ ukazatele: **PTR**, **ref**nebo **Unique**.

## <a name="remarks"></a>Poznámky

Atribut **pointer_default** C++ má stejné funkce jako atribut [pointer_default](/windows/win32/Midl/pointer-default) MIDL.

## <a name="example"></a>Příklad

Ukázkové použití **pointer_default**naleznete v příkladu pro vlastnost [DefaultValue](defaultvalue.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**interface**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)
