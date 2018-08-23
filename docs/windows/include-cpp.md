---
title: Zahrnout (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 8fe604074b843e7c0b76c2e671e0abd9e40770a7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598457"
---
# <a name="include-c"></a>include (C++)

Určuje jeden nebo více souborů záhlaví mají být zahrnuty v souboru generovaného IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[ include(
   header_file
) ];
```

### <a name="parameters"></a>Parametry

*HEADER_FILE*  
Název souboru, který chcete, aby zahrnuté v souboru generovaného IDL.

## <a name="remarks"></a>Poznámky

**Zahrnují** C++ atribut způsobí, že `#include` příkaz umístit pod `import "docobj.idl"` příkaz v souboru generovaného IDL.

**Zahrnují** C++ atribut má stejné funkce jako [zahrnují](http://msdn.microsoft.com/library/windows/desktop/aa367052) atribut MIDL.

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

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Samostatné atributy](../windows/stand-alone-attributes.md)  
[import](../windows/import.md)  
[importidl](../windows/importidl.md)  
[includelib –](../windows/includelib-cpp.md)  
[importlib](../windows/importlib.md)  