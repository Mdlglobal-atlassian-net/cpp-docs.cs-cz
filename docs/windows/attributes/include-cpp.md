---
title: include (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: 39f991bb036dce1c50a9d2ee800d3fec65af7c55
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166780"
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

Atribut **include** C++ způsobí, že je příkaz `#include` umístěn pod příkazem `import "docobj.idl"` v generovaném souboru IDL.

Atribut **include** C++ má stejné funkce jako atribut [include](/windows/win32/Midl/include) MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje příklad použití **include**. V tomto příkladu soubor include. h obsahuje pouze příkaz `#include`.

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

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)
