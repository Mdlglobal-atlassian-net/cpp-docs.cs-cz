---
title: Entry (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 9bdfc64506f26ee4e9876920821883a0fa12bc7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167092"
---
# <a name="entry"></a>entry

Určuje exportovanou funkci nebo konstantu v modulu určením vstupního bodu v knihovně DLL.

## <a name="syntax"></a>Syntaxe

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>Parametry

*id*<br/>
ID vstupního bodu

## <a name="remarks"></a>Poznámky

Atribut **entry** C++ má stejné funkce jako atribut [entry](/windows/win32/Midl/entry) MIDL.

## <a name="example"></a>Příklad

Příklad použití **položky**naleznete v příkladu pro [idl_module](idl-module.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|atribut `idl_module`|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)
