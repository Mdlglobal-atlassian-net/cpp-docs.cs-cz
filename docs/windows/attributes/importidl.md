---
title: importidl (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 6e41a98bef079c92b6df6e7eff203301aa9ceae4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166819"
---
# <a name="importidl"></a>importidl

Vloží zadaný soubor. idl do vygenerovaného souboru IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>Parametry

*idl_file*<br/>
Určuje název souboru. idl, který chcete sloučit se souborem. idl, který bude vygenerován pro vaši aplikaci.

## <a name="remarks"></a>Poznámky

Atribut **importidl** C++ umístí oddíl mimo blok knihovny (v *idl_file*) do generovaného souboru. idl vašeho programu a oddílu knihovny (v idl_file) do části Library (v *idl_file*) generovaného souboru. idl vašeho programu.

Můžete chtít použít **importidl**, například pokud chcete použít ručně kódovaný soubor IDL s vygenerovaným souborem. idl.

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
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
[Samostatné atributy](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
