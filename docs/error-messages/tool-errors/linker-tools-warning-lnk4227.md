---
title: Upozornění linkerů LNK4227
ms.date: 11/04/2016
f1_keywords:
- LNK4227
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
ms.openlocfilehash: 7b75cff4f03370951245bde1b485d538ffdb4007
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182939"
---
# <a name="linker-tools-warning-lnk4227"></a>Upozornění linkerů LNK4227

> Upozornění operace metadat (*HRESULT*): *warning_message*

Linker zjistil rozdíly v metadatech při sloučení:

- Jedno nebo více odkazovaných sestavení se sestavou sestavení, které je právě sestaveno.

- Jeden nebo více souborů zdrojového kódu v kompilaci.

Například LINKERŮ LNK4227 může být způsobeno tím, že máte dvě globální funkce se stejným názvem, ale informace o parametrech jsou deklarovány jinak (tj. deklarace nejsou konzistentní ve všech compilands). Použijte Ildasm. exe/TEXT/METADATA *object_file* v každém souboru. obj, abyste viděli, jak se typy liší.

LINKERŮ LNK4227 se také používá k nahlášení problémů, které pocházejí z jiného nástroje. Vyhledejte zprávu s upozorněním, kde najdete další informace.

Aby bylo možné vyřešit upozornění, je nutné opravit problémy s metadaty.

## <a name="example"></a>Příklad

LINKERŮ LNK4227 se generuje, když se odkazované sestavení přihlásilo jinak než na sestavení, které na něj odkazuje.

Následující ukázka generuje LINKERŮ LNK4227:

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

a potom

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

LINKERŮ LNK4227 lze také vygenerovat, pokud jsou čísla verzí v nesprávném formátu předávána atributům sestavení.  Notace * je specifická pro `AssemblyVersionAttribute`.  Chcete-li toto upozornění vyřešit, použijte pouze čísla z atributů verze kromě `AssemblyVersionAttribute`.

Následující ukázka generuje LINKERŮ LNK4227:

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```
