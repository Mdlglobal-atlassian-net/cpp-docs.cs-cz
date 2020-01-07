---
title: modul, import, export
ms.date: 12/12/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: Deklarace import a export použijte pro přístup k a k publikování typů a funkcí definovaných v zadaném modulu.
ms.openlocfilehash: ae28bce8e06840cafa5c92521f6e9a62aa5bfde6
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301454"
---
# <a name="module-import-export"></a>modul, import, export

Deklarace **modulu**, **importu**a **exportu** jsou k dispozici v c++ 20 a vyžadují přepínač kompilátoru [/Experimental: Module](../build/reference/experimental-module.md) společně s [/std: C + + nejnovější](../build/reference/std-specify-language-standard-version.md). Další informace najdete v tématu [Přehled modulů v C++ ](modules-cpp.md).

## <a name="module"></a>module

Umístěte deklaraci **modulu** na začátek souboru implementace modulu, abyste určili, že obsah souboru patří do pojmenovaného modulu.

```cpp
module ModuleA;
```

## <a name="export"></a>export

Použijte deklaraci **modulu exportu** pro soubor primárního rozhraní modulu, který musí mít příponu **. IXX**:

```cpp
export module ModuleA;
```

V souboru rozhraní použijte modifikátor **exportu** u názvů, které jsou určeny jako součást veřejného rozhraní:

```cpp
// ModuleA.ixx

export module ModuleA;

namespace Bar
{
   export int f();
   export double d();
   double internal_f(); // not exported
}
```

Neexportované názvy nejsou viditelné pro kód, který importuje modul:

```cpp
//MyProgram.cpp

import module ModuleA;

void main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

Klíčové slovo **Export** se nemusí zobrazit v souboru implementace modulu. Pokud je pro název oboru názvů použit **Export** , jsou exportovány všechny názvy v oboru názvů.

## <a name="import"></a>import

Pomocí deklarace **importu** můžete v programu zviditelnit názvy modulů. Deklarace importu se musí vyskytovat po deklaraci modulu a za direktivami #include, ale před všemi deklaracemi v souboru.

```cpp
module ModuleA;

#include "custom-lib.h"
import std.core;
import std.regex;
import ModuleB;

// begin declarations here:
template <class T>
class Baz
{...};
```

## <a name="remarks"></a>Poznámky

**Import** i **modul** se považují za klíčová slova pouze v případě, že se zobrazují na začátku logického řádku:

```cpp

// OK:
module ;
module module-name
import :
import <
import "
import module-name
export module ;
export module module-name
export import :
export import <
export import "
export import module-name

// Error:
int i; module ;
```

**Specifické pro společnost Microsoft**

V Microsoftu C++jsou tokeny **importu** a **modul** vždycky identifikátory a klíčová slova nikdy, když se používají jako argumenty pro makro.

### <a name="example"></a>Příklad

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Přehled modulů vC++](modules-cpp.md)
