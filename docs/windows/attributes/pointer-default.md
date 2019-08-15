---
title: pointer_default (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: c70c372e5f1c3a9c2f620a1fa3505fb9d0436e79
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514267"
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

Ukázkové použití **pointer_default**najdete v příkladu pro vlastnost [DefaultValue](defaultvalue.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**interface**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)