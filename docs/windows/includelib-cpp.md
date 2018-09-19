---
title: includelib – (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 5f15fcefe1a18156e4cbe8180138d7b6c1d944e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398583"
---
# <a name="includelib-c"></a>includelib (C++)

Způsobí, že soubor IDL nebo .h mají být zahrnuty v souboru generovaného IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[ includelib(
   name.idl
) ];
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

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)<br/>
[Samostatné atributy](../windows/stand-alone-attributes.md)<br/>
[import](../windows/import.md)<br/>
[importidl](../windows/importidl.md)<br/>
[Zahrnout](../windows/include-cpp.md)<br/>
[importlib](../windows/importlib.md)  