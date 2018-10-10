---
title: Upozornění (úroveň 1) C4251 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4251
dev_langs:
- C++
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d964c375adf80caef3bb5a6eb06c67ef8e3e7200
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890046"
---
# <a name="compiler-warning-level-1-c4251"></a>Kompilátor upozornění (úroveň 1) C4251

'identifier': Třída 'type' musí mít rozhraní dll klienty třídy 'type2'

Aby se minimalizovala možnost poškození dat při exportu třída s atributem [__declspec(dllexport)](../../cpp/dllexport-dllimport.md), ujistěte se, že:

- Všechna statická data je přístup prostřednictvím funkce, které jsou exportovány z knihovny DLL.

- Žádné vložené metody třídy můžete upravit statická data.

- Žádné vložené metody třídy použijte funkce CRT nebo jiné funkce knihovny statických dat (viz [potenciální chyby předávání CRT objekty přes hranice knihovny DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) Další informace).

- Žádné metody třídy (bez ohledu na to vkládání) můžete použít typy, kde instance v souboru EXE a DLL obsahuje rozdíly ve statická data.

Export tříd, které knihovny DLL, která definuje třídu s virtuálními funkcemi a funkce, které můžete volat k vytvoření instance definováním a odstranit objekty typu se můžete vyhnout.  Pak můžete pouze volání virtuálních funkcí na typu.

C4251 můžete ignorovat, pokud je odvozený od typu ve standardní knihovně C++ kompilaci ladění vydání (**/MTD**) a kde se chybová zpráva kompilátoru odkazuje na _Container_base.

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```