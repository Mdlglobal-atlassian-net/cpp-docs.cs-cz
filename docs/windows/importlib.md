---
title: importlib | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importlib
dev_langs:
- C++
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3df5a1893567b54337a5c3807fcace6a02154670
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416003"
---
# <a name="importlib"></a>importlib

Díky typy, které již byly zkompilovány do jiné knihovny typů k dispozici pro vytváření knihovny typů.

## <a name="syntax"></a>Syntaxe

```cpp
[ importlib(
   "tlb_file"
) ];
```

### <a name="parameters"></a>Parametry

*tlb_file*<br/>
Název souboru .tlb v uvozovkách, které chcete importovat do knihovny typů aktuálního projektu.

## <a name="remarks"></a>Poznámky

**Importlib** C++ atribut způsobí, že `importlib` příkaz umístit do bloku knihovny ze souboru generovaného IDL. **Importlib** atribut má stejné funkce jako [importlib](/windows/desktop/Midl/importlib) atribut MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje příklad, jak používat **importlib**:

```cpp
// cpp_attr_ref_importlib.cpp
// compile with: /LD
[module(name="MyLib")];
[importlib("importlib.tlb")];
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
[importidl](../windows/importidl.md)<br/>
[Zahrnout](../windows/include-cpp.md)<br/>
[includelib –](../windows/includelib-cpp.md)