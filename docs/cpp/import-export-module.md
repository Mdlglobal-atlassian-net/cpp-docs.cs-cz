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
description: Pomocí dovozních a vývozních prohlášení můžete přistupovat k typům a funkcím definovaným v zadaném modulu a publikovat je.
ms.openlocfilehash: a765e9a406660d3c945ef3d70754178b0648458c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374117"
---
# <a name="module-import-export"></a>modul, import, export

Deklarace **modulu**, **importu**a **exportu** jsou k dispozici v jazyce C++20 a vyžadují přepínač kompilátoru [/experimental:module](../build/reference/experimental-module.md) spolu s [parametrem /std:c++latest](../build/reference/std-specify-language-standard-version.md). Další informace naleznete [v tématu Přehled modulů v jazyce C++](modules-cpp.md).

## <a name="module"></a>module

Umístěte deklaraci **modulu** na začátek souboru implementace modulu, abyste určili, že obsah souboru patří do pojmenovaného modulu.

```cpp
module ModuleA;
```

## <a name="export"></a>export

Použijte **deklaraci exportního modulu** pro primární soubor rozhraní modulu, který musí mít příponu **.ixx**:

```cpp
export module ModuleA;
```

V souboru rozhraní použijte modifikátor **exportu** u názvů, které mají být součástí veřejného rozhraní:

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

int main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

Klíčové slovo **exportu** se nemusí zobrazit v souboru implementace modulu. Při **použití exportu** na název oboru názvů jsou exportovány všechny názvy v oboru názvů.

## <a name="import"></a>import

Pomocí **deklarace importu** zviditelněte názvy modulu v programu. Dovozní prohlášení musí být uvedeno za prohlášením modulu a po všech #include směrnic, ale před všemi prohlášeními v souboru.

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

**Import** i **modul** jsou považovány za klíčová slova pouze v případě, že se zobrazí na začátku logického řádku:

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

**Specifické pro Microsoft**

V jazyce Microsoft C++ **jsou import** tokenů a **modul** vždy identifikátory a nikdy klíčová slova, pokud jsou použity jako argumenty pro makro.

### <a name="example"></a>Příklad

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**Ukončit microsoft specifické**

## <a name="see-also"></a>Viz také

[Přehled modulů v C++](modules-cpp.md)
