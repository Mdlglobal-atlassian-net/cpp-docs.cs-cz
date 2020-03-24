---
title: INCLUDELIB – (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 4022a3f1f2d4ccaabe65c24065be8e1c846d604d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214839"
---
# <a name="includelib-c"></a>includelib (C++)

Způsobí, že soubor. idl nebo. h bude zahrnut do generovaného souboru IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>Parametry

*název. idl*<br/>
Název souboru. idl, který chcete zahrnout jako součást vygenerovaného souboru IDL.

## <a name="remarks"></a>Poznámky

Atribut **INCLUDELIB –** C++ způsobí, že soubor. idl nebo. h bude do generovaného souboru IDL zahrnut po příkazu `importlib`.

## <a name="example"></a>Příklad

Následující kód je zobrazen v souboru. cpp:

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Jakékoli|
|**REPEATABLE**|Ano|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)
