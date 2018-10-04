---
title: importidl – (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importidl
dev_langs:
- C++
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d1c022a48ef5510f67355af3af1ff0a0e98ad4c4
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789363"
---
# <a name="importidl"></a>importidl

Vloží zadaný souboru do generovaného souboru.

## <a name="syntax"></a>Syntaxe

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>Parametry

*idl_file*<br/>
Určuje název souboru, který chcete sloučit s souboru IDL se vygeneruje pro vaši aplikaci.

## <a name="remarks"></a>Poznámky

**Importidl –** C++ atribut umístí části mimo blok knihovny (v *idl_file*) do generovaného souboru váš program a v části library (v *idl_file*) do knihovny část váš program vygeneruje soubor IDL.

Můžete chtít použít **importidl –**, například, pokud chcete použít soubor .idl. ruční pevně zakódované souborem generované IDL.

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
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

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[Zahrnout](include-cpp.md)<br/>
[includelib –](includelib-cpp.md)  