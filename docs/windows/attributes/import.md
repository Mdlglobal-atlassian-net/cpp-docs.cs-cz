---
title: Import (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.import
dev_langs:
- C++
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a0509f6c1292ee7bb2e1ba97d1f75c626f3b0761
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789498"
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
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[Zahrnout](include-cpp.md)<br/>
[includelib –](includelib-cpp.md)  