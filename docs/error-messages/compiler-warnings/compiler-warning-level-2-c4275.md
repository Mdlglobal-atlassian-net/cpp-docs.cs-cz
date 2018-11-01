---
title: Kompilátor upozornění (úroveň 2) C4275
ms.date: 11/04/2016
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: 985a622e2c89306c453ae6c860d21e6265d0fff1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594321"
---
# <a name="compiler-warning-level-2-c4275"></a>Kompilátor upozornění (úroveň 2) C4275

jiné – rozhraní DLL classkey 'identifier' používá jako základ pro rozhraní DLL classkey 'identifier'

Exportované třídy byla odvozena ze třídy, který nebyl exportován.

Aby se minimalizovala možnost poškození dat při exportu třída s atributem [__declspec(dllexport)](../../cpp/dllexport-dllimport.md), ujistěte se, že:

- Všechna statická data se přistupuje prostřednictvím funkce, které jsou exportovány z knihovny DLL.

- Žádné vložené metody třídy můžete upravit statická data.

- Žádné vložené metody třídy použijte funkce CRT nebo jiné funkce knihovny používají statická data.

- Žádné vložené třídy funkce pomocí funkce CRT nebo jiné funkce knihovny, kde, například k statická data.

- Žádné metody třídy (bez ohledu na to vkládání) můžete použít typy, kde instance v souboru EXE a DLL obsahuje rozdíly ve statická data.

Export tříd, které knihovny DLL, která definuje třídu s virtuálními funkcemi a funkce, které můžete volat k vytvoření instance definováním a odstranit objekty typu se můžete vyhnout.  Pak můžete pouze volání virtuálních funkcí na typu.

C4275 můžete ignorovat v jazyce Visual C++, pokud je odvozený od typu ve standardní knihovně C++ kompilaci ladění vydání (**/MTD**) a kde se chybová zpráva kompilátoru odkazuje na _Container_base.

```
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```