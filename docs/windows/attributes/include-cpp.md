---
title: include (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: ece88ebd7b5d9d81beb871427b58a72b2cf02022
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514551"
---
# <a name="include-c"></a>include (C++)

Určuje jeden nebo více hlavičkových souborů, které mají být zahrnuty do vygenerovaného souboru IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>Parametry

*header_file*<br/>
Název souboru, který chcete zahrnout do vygenerovaného souboru IDL.

## <a name="remarks"></a>Poznámky

Atribut **include** C++ způsobí, že je `import "docobj.idl"` příkaz umístěn pod příkazem v generovaném souboru IDL. `#include`

Atribut **include** C++ má stejné funkce jako atribut [include](/windows/win32/Midl/include) MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje příklad použití **include**. V tomto příkladu soubor include. h obsahuje pouze `#include` příkaz.

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
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

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)