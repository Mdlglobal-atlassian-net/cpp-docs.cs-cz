---
title: library_block – (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.library_block
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
ms.openlocfilehash: 219f6a89dd7f80246e0337c2ef3bcad43540b165
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033206"
---
# <a name="libraryblock"></a>library_block

Umístí konstrukci uvnitř bloku knihovny IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[library_block]
```

## <a name="remarks"></a>Poznámky

Umístíte-li použít konstrukce uvnitř bloku knihovny, zajistíte tím, že budou předány do knihovny typů, bez ohledu na to, zda se na ni odkazuje. Ve výchozím nastavení, pouze vytvoří změnil [coclass](coclass.md), [dispinterface](dispinterface.md), a [možnost idl_module](idl-module.md) atributy jsou umístěny v bloku knihovny.

## <a name="example"></a>Příklad

V následujícím kódu, vlastní rozhraní nachází uvnitř bloku knihovny.

```cpp
// cpp_attr_ref_library_block.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib")];
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface IMyInterface {
   HRESULT f1();
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Kdekoli|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)