---
title: importlib (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importlib
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
ms.openlocfilehash: 29c7df8fbedbd107a9bb0b05466addc4672fc555
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041442"
---
# <a name="importlib"></a>importlib

Díky typy, které již byly zkompilovány do jiné knihovny typů k dispozici pro vytváření knihovny typů.

## <a name="syntax"></a>Syntaxe

```cpp
[ importlib("tlb_file") ];
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
|**Neplatné atributy**|Žádný|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)