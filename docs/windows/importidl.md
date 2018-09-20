---
title: importidl – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 9406cc95804e4eb9fd76f53201118f13f0e422a4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410504"
---
# <a name="importidl"></a>importidl

Vloží zadaný souboru do generovaného souboru.

## <a name="syntax"></a>Syntaxe

```cpp
[ importidl(
   idl_file
) ];
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

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](../windows/compiler-attributes.md)<br/>
[Samostatné atributy](../windows/stand-alone-attributes.md)<br/>
[import](../windows/import.md)<br/>
[importlib](../windows/importlib.md)<br/>
[Zahrnout](../windows/include-cpp.md)<br/>
[includelib –](../windows/includelib-cpp.md)  