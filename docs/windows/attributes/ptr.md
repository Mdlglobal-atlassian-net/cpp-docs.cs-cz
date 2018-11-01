---
title: PTR (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ptr
helpviewer_keywords:
- ptr attribute
ms.assetid: 95eaea57-a5be-45f6-a612-ba2c9bc4645a
ms.openlocfilehash: 7ed08403f32e5e4609266975c5c479a7b758fe89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506207"
---
# <a name="ptr"></a>ptr

Ukazatel se označí jako úplné ukazatel.

## <a name="syntax"></a>Syntaxe

```cpp
[ptr]
```

## <a name="remarks"></a>Poznámky

**Ptr** C++ atribut má stejné funkce jako [ptr](/windows/desktop/Midl/ptr) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [defaultvalue](defaultvalue.md) ukázkový používání **ptr**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Rozhraní parametrů, metody rozhraní **– typedef**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)