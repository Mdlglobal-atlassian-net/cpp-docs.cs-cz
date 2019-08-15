---
title: Entry (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 71abf4f183255fa137b43ac9cabd88d15c3fc85d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490892"
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
|**Platí pro**|`idl_module`přidělen|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)