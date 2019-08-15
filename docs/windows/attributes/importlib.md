---
title: importlib (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importlib
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
ms.openlocfilehash: 92cf335e5c4754595f2c7af2e1aef30d309d2f5f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514608"
---
# <a name="importlib"></a>importlib

Vytvoří typy, které již byly zkompilovány do jiné knihovny typů, které jsou k dispozici pro vytvoření knihovny typů.

## <a name="syntax"></a>Syntaxe

```cpp
[ importlib("tlb_file") ];
```

### <a name="parameters"></a>Parametry

*tlb_file*<br/>
Název souboru. tlb (v uvozovkách), který chcete importovat do knihovny typů aktuálního projektu.

## <a name="remarks"></a>Poznámky

Atribut **importlib** C++ způsobí, že se příkazumístídoblokuknihovnyvygenerovanéhosouboru.idl.`importlib` Atribut **importlib** má stejné funkce jako atribut [importlib](/windows/win32/Midl/importlib) MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje příklad použití **importlib**:

```cpp
// cpp_attr_ref_importlib.cpp
// compile with: /LD
[module(name="MyLib")];
[importlib("importlib.tlb")];
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

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)