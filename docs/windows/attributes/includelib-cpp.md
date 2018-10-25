---
title: includelib – (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.includelib
dev_langs:
- C++
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96d4ecff09cf00b5221fd0c9c80b4584b203a781
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059647"
---
# <a name="includelib-c"></a>includelib (C++)

Způsobí, že soubor IDL nebo .h mají být zahrnuty v souboru generovaného IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>Parametry

*name.IDL*<br/>
Název souboru, který chcete zahrnout jako součást souboru generovaného IDL.

## <a name="remarks"></a>Poznámky

**Includelib** C++ atribut vygeneruje soubor IDL nebo .h mají být zahrnuty v souboru IDL vygenerované po `importlib` příkazu.

## <a name="example"></a>Příklad

Následující kód můžete vidět v souboru s příponou .cpp:

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Kdekoli|
|**Opakovatelné**|Ano|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)