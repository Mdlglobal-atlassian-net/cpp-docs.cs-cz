---
title: Zahrnout (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.include
dev_langs:
- C++
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97c7ca1f808beb7e0658338dac77819455f9ed84
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789380"
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
[includelib –](includelib-cpp.md)<br/>
[importlib](importlib.md)  