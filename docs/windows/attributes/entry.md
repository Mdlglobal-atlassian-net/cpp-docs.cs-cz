---
title: Položka (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 703a55ee7c56b64a5b168016770508508bab09e0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346132"
---
# <a name="entry"></a>entry

Určuje exportované funkce nebo konstanta v modulu určením vstupní bod v knihovně DLL.

## <a name="syntax"></a>Syntaxe

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>Parametry

*id*<br/>
ID vstupní bod.

## <a name="remarks"></a>Poznámky

**Položka** C++ atribut má stejné funkce jako [položka](/windows/desktop/Midl/entry) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [možnost idl_module](idl-module.md) pro příklad použití **položka**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|`idl_module` Atribut|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)