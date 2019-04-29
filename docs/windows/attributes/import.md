---
title: Import (atribut C++ COM)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: d458ce9d938da5f3650eb2478385165de6a140ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409370"
---
# <a name="import"></a>import

Určuje jiný soubor .idl, .odl nebo záhlaví obsahující definice, kterou chcete odkazovat z hlavní IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>Parametry

*idl_file*<br/>
Název souboru IDL, který chcete importovat do knihovny typů aktuálního projektu.

## <a name="remarks"></a>Poznámky

**Importovat** C++ atribut způsobí, že `#import` příkaz umístit pod `import "docobj.idl"` příkaz v souboru generovaného IDL. **Importovat** atribut má stejné funkce jako [importovat](/windows/desktop/Midl/import) atribut MIDL.

**Importovat** atribut pouze umístí do souboru IDL, který se vygeneruje vaším projektem; zadaný soubor **importovat** atribut neumožňuje volání konstruktorů v zadaném souboru ze zdrojového kódu ve vašem projektu.  Pokud chcete volat konstrukce v zadaném souboru ze zdrojového kódu ve vašem projektu, buď použijte [#import](../../preprocessor/hash-import-directive-cpp.md) a `embedded_idl` atribut nebo je můžete zahrnout soubor hlaviček pro *idl_file*, pokud existuje soubor hlaviček.

## <a name="example"></a>Příklad

Následující kód:

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

vytvoří následující kód v souboru generovaného IDL:

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Kdekoli|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)