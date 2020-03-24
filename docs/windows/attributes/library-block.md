---
title: library_block (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.library_block
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
ms.openlocfilehash: 405cc1cd5af7dcd689e833764f3da2fdc6d5f703
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214770"
---
# <a name="library_block"></a>library_block

Umístí konstrukce do bloku knihovny IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[library_block]
```

## <a name="remarks"></a>Poznámky

Když umístíte konstrukci do bloku knihovny, zajistíte, že bude předána do knihovny typů bez ohledu na to, zda je odkazováno. Ve výchozím nastavení jsou v bloku knihovny umístěny pouze konstrukce, které jsou upraveny atributy [Coclass](coclass.md), [IDispatch](dispinterface.md)a [idl_module](idl-module.md) .

## <a name="example"></a>Příklad

V následujícím kódu je vlastní rozhraní umístěno uvnitř bloku knihovny.

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

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Jakékoli|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)
