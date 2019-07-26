---
title: modul, import, export
ms.date: 07/15/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: Použijte příkaz Import pro přístup k typům a funkcím definovaným v zadaném modulu.
ms.openlocfilehash: fbb9c45ec816c859edb4df38ad67dc7778247e87
ms.sourcegitcommit: 7b039b5f32f6c59be6c6bb1cffafd69c3bfadd35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68537764"
---
# <a name="module-import-export"></a>modul, import, export

Klíčová slova **modul**, **Import**a **Export** jsou k dispozici v `/experimental:modules` c++ 20 a vyžadují přepínač kompilátoru společně `/std:c++latest`s. Další informace najdete v tématu [Přehled modulů v C++ ](modules-cpp.md).

## <a name="module"></a>module

Pomocí příkazu **Module** na začátku souboru implementace modulu určete, že obsah souboru patří do pojmenovaného modulu. 

```cpp
module ModuleA;
```

## <a name="export"></a>export

Použijte příkaz **exportovat modul** pro soubor primárního rozhraní modulu, který musí mít příponu **. IXX**:

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

Klíčové slovo **Export** se nemusí zobrazit v souboru implementace modulu. Při použití modifikátoru **exportu** pro název oboru názvů jsou exportovány všechny názvy v oboru názvů.

## <a name="import"></a>import

Pomocí příkazu **Import** můžete nastavit, aby se v programu zobrazovaly názvy modulů. Příkaz import musí být uveden za příkazem Module a za #include direktivami, ale před všemi deklaracemi v souboru.

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

## <a name="see-also"></a>Viz také
[Přehled modulů vC++](modules-cpp.md)
