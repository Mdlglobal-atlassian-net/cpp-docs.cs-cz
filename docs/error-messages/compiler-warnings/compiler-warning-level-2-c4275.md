---
title: Kompilátor upozornění (úroveň 2) C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: 6e0e80d465d77bd4fe99fbcaa98e289b8a4c8b63
ms.sourcegitcommit: 966e4466f10c93fc12faf33d28e03b39489423fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987024"
---
# <a name="compiler-warning-level-2-c4275"></a>Kompilátor upozornění (úroveň 2) C4275

> jiné – třídu DLL-interface*třída_1*'použít jako základ pro knihovnu DLL-interface class'*třída_2*.

Exportované třídy byla odvozena ze třídy, který nebyl exportován.

Aby se minimalizovala možnost poškození dat při exportu třída s atributem [__declspec(dllexport)](../../cpp/dllexport-dllimport.md), ujistěte se, že:

- Všechna statická data se přistupuje prostřednictvím funkce, které jsou exportovány z knihovny DLL.

- Žádné vložené metody třídy můžete upravit statická data.

- Žádné vložené metody třídy pomocí funkce CRT nebo jiné funkce knihovny, které používají statická data.

- Platí pro vložené třídy použijte funkce CRT nebo jiné funkce knihovny, odkud statická data.

- Žádné metody třídy (bez ohledu na to vkládání) můžete použít typy, kde instance v souboru EXE a DLL obsahuje rozdíly ve statická data.

Export tříd, které knihovny DLL, která definuje třídu s virtuálními funkcemi a funkce, které můžete volat k vytvoření instance definováním a odstranit objekty typu se můžete vyhnout.  Pak můžete pouze volání virtuálních funkcí na typu.

C4275 můžete ignorovat v jazyce Visual C++, pokud je odvozený od typu ve standardní knihovně C++ kompilaci ladění vydání (**/MTD**) a kde se chybová zpráva kompilátoru odkazuje na `_Container_base`.

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```