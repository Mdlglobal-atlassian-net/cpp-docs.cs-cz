---
title: Zahrnout (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: 6fb385877285602c1eb6649d11e16558d7fb07ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544752"
---
# <a name="include-c"></a>include (C++)

Určuje jeden nebo více souborů záhlaví mají být zahrnuty v souboru generovaného IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>Parametry

*HEADER_FILE*<br/>
Název souboru, který chcete, aby zahrnuté v souboru generovaného IDL.

## <a name="remarks"></a>Poznámky

**Zahrnují** C++ atribut způsobí, že `#include` příkaz umístit pod `import "docobj.idl"` příkaz v souboru generovaného IDL.

**Zahrnují** C++ atribut má stejné funkce jako [zahrnují](/windows/desktop/Midl/include) atribut MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje příklad, jak používat **zahrnují**. V tomto příkladu include.h souboru obsahuje pouze `#include` příkazu.

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Kdekoli|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)