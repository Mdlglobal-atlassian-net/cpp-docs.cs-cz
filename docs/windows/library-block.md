---
title: library_block – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.library_block
dev_langs:
- C++
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33febb69db2a8f3bd67205de2e6e5cf019016471
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598490"
---
# <a name="libraryblock"></a>library_block

Umístí konstrukci uvnitř bloku knihovny IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[library_block]
```

## <a name="remarks"></a>Poznámky

Umístíte-li použít konstrukce uvnitř bloku knihovny, zajistíte tím, že budou předány do knihovny typů, bez ohledu na to, zda se na ni odkazuje. Ve výchozím nastavení, pouze vytvoří změnil [coclass](../windows/coclass.md), [dispinterface](../windows/dispinterface.md), a [možnost idl_module](../windows/idl-module.md) atributy jsou umístěny v bloku knihovny.

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
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](../windows/compiler-attributes.md)  
[Samostatné atributy](../windows/stand-alone-attributes.md)  