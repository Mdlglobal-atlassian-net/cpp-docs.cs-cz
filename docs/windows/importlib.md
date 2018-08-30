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
ms.openlocfilehash: a790887f54e01cea835c6110e3d81e1c2d3afeaa
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206698"
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

*tlb_file*  
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

[Atributy kompilátoru](../windows/compiler-attributes.md)  
[Samostatné atributy](../windows/stand-alone-attributes.md)  
[import](../windows/import.md)  
[importidl](../windows/importidl.md)  
[Zahrnout](../windows/include-cpp.md)  
[includelib –](../windows/includelib-cpp.md)