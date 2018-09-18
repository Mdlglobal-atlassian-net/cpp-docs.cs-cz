---
title: Upozornění Linkerů LNK4227 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4227
dev_langs:
- C++
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28bcf242e48046278030ec4259b7ae3edd1c4a61
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088862"
---
# <a name="linker-tools-warning-lnk4227"></a>Upozornění linkerů LNK4227

> upozornění operace metadat (*HRESULT*): *warning_message*

Linker byly zjištěny při slučování metadat rozdíly:

- Jeden nebo víc odkazovaných sestavení se sestavením jsou sestaveny.

- Jeden nebo více soubory zdrojového kódu v kompilaci.

Například může být způsobeno LNK4227 Pokud máte dvě globální funkce se stejným názvem, ale informace o parametrech, které jsou deklarovány jinak (to znamená, že deklarace nejsou konzistentní vzhledem k aplikacím ve všech souborech určených ke kompilaci). Použijte ildasm.exe/text/metadata *object_file* každého souboru .obj, pokud chcete zobrazit, jak se liší typy.

LNK4227 slouží také k hlášení problémů, které pocházejí z jiného nástroje. Vyhledejte upozornění pro další informace.

Problémy metadat musí být nastaven na vyřešení upozornění.

## <a name="example"></a>Příklad

LNK4227 se vygeneruje, když odkazované sestavení byla podepsána jiným způsobem než sestavení, která na něj odkazuje.

Následující ukázka generuje LNK4227:

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

a pak,

```cpp
// LNK4227b.cpp
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe
using namespace System::Reflection;
using namespace System::Runtime::CompilerServices;

[assembly:AssemblyDelaySignAttribute(true)];
// Try the following line instead
// [assembly:AssemblyDelaySignAttribute(false)];

ref class MyClass
{
};
```

## <a name="example"></a>Příklad

Při předávání čísla verze v nesprávném formátu pro atributy sestavení, můžou být taky vygenerovaná LNK4227.  "*" Je specifické pro zápis `AssemblyVersionAttribute`.  Pokud chcete vyřešit toto upozornění, použijte pouze čísla v atributech verze jiné než `AssemblyVersionAttribute`.

Následující ukázka generuje LNK4227:

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```