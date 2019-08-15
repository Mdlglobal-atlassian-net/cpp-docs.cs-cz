---
title: Import (C++ atribut com)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: f9ed80bdcc04302c0dee85935f377c8e3dbfd37f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514617"
---
# <a name="import"></a>import

Určuje jiný soubor. idl,. odl nebo hlavičkový soubor obsahující definice, na které chcete odkazovat z hlavního IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>Parametry

*idl_file*<br/>
Název souboru. idl, který chcete importovat do knihovny typů aktuálního projektu.

## <a name="remarks"></a>Poznámky

Atribut **Import** C++ způsobí, že je `import "docobj.idl"` příkaz umístěn pod příkazem v generovaném souboru IDL. `#import` Atribut **Import** má stejné funkce jako atribut [Import](/windows/win32/Midl/import) MIDL.

Atribut **Import** umístí zadaný soubor pouze do souboru. idl, který bude vytvořen vaším projektem; atribut **Import** neumožňuje volat konstrukce v zadaném souboru ze zdrojového kódu v projektu.  Chcete-li volat konstrukce v zadaném souboru ze zdrojového kódu v projektu, buď použijte [#import](../../preprocessor/hash-import-directive-cpp.md) a `embedded_idl` atribut nebo můžete zahrnout soubor. h pro *idl_file*, pokud existuje soubor. h.

## <a name="example"></a>Příklad

Následující kód:

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

Vytvoří následující kód v generovaném souboru IDL:

```
import "docobj.idl";
import "import.idl";

[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]
library MyLib {
   importlib("stdole2.tlb");
   importlib("olepro32.dll");
...
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
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)