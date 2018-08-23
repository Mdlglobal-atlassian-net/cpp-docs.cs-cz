---
title: Importovat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 2ba62d3dfc1f71ab61b5041ebbd884be8b5e39f6
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592661"
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

*idl_file*  
Název souboru IDL, který chcete importovat do knihovny typů aktuálního projektu.

## <a name="remarks"></a>Poznámky

**Importovat** C++ atribut způsobí, že `#import` příkaz umístit pod `import "docobj.idl"` příkaz v souboru generovaného IDL. **Importovat** atribut má stejné funkce jako [importovat](http://msdn.microsoft.com/library/windows/desktop/aa367047) atribut MIDL.

**Importovat** atribut pouze umístí do souboru IDL, který se vygeneruje vaším projektem; zadaný soubor **importovat** atribut neumožňuje volání konstruktorů v zadaném souboru ze zdrojového kódu ve vašem projektu.  Pokud chcete volat konstrukce v zadaném souboru ze zdrojového kódu ve vašem projektu, buď použijte [#import](../preprocessor/hash-import-directive-cpp.md) a `embedded_idl` atribut nebo je můžete zahrnout soubor hlaviček pro *idl_file*, pokud existuje soubor hlaviček.

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

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Samostatné atributy](../windows/stand-alone-attributes.md)  
[importidl](../windows/importidl.md)  
[importlib](../windows/importlib.md)  
[Zahrnout](../windows/include-cpp.md)  
[includelib –](../windows/includelib-cpp.md)  