---
title: Upozornění kompilátoru (úroveň 1) C4251
ms.date: 04/21/2020
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 9f261d3deb7f1cac8cd5c60b920e0be49bc8b7a6
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032327"
---
# <a name="compiler-warning-level-1-c4251"></a>Upozornění kompilátoru (úroveň 1) C4251

> "*typ*" : třída "*type1*" musí mít rozhraní dll, které mají používat klienti třídy "*type2*"

## <a name="remarks"></a>Poznámky

Chcete-li minimalizovat možnost poškození dat při exportu třídy deklarované jako [__declspec(dllexport)](../../cpp/dllexport-dllimport.md), zajistěte, aby:

- Ke všem statickým datům se přistupuje prostřednictvím funkcí, které jsou exportovány z dll.

- Žádné vložené metody vaší třídy můžete upravit statická data.

- Žádné vložené metody vaší třídy používají funkce CRT nebo jiné funkce knihovny, které používají statická data. Další informace naleznete [v tématu Potenciální chyby předávání crt objekty přes hranice DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

- Žádné metody vaší třídy (ať už vložené nebo ne) můžete použít typy, kde instance v EXE a DLL mají statické datové rozdíly.

Můžete se vyhnout problémům při exportu třídy z DLL: Definujte třídu tak, aby měla virtuální funkce a funkce pro vytváření instancí a odstraňování objektů typu. Potom stačí volat virtuální funkce na typu.

C4251 lze ignorovat, pokud je vaše třída odvozena z typu ve standardní knihovně jazyka C++, kompilujete verzi ladění ( `_Container_base`**/MTd**) a kde se odkazuje na chybovou zprávu kompilátoru .

## <a name="example"></a>Příklad

Tento příklad exportuje `VecWrapper` specializovanou `std::vector`třídu odvozenou z .

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllexport) VecWrapper : vector<Node *> {};   // C4251
```
