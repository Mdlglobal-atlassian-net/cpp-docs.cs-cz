---
title: Upozornění kompilátoru (úroveň 1) C4251
ms.date: 11/04/2016
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 8a723b7ce7fc79fb6be9c9dd2b500631098622b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163216"
---
# <a name="compiler-warning-level-1-c4251"></a>Upozornění kompilátoru (úroveň 1) C4251

' identifier ': Třída ' type ' vyžaduje, aby klienti třídy ' typ2 ' používali rozhraní dll.

Chcete-li minimalizovat možnost poškození dat při exportu třídy s [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), zajistěte, aby:

- Všechna vaše statická data jsou přístupná prostřednictvím funkcí, které jsou exportovány z knihovny DLL.

- Žádné vložené metody třídy nemůžou upravovat statická data.

- Žádné vložené metody vaší třídy nepoužívají funkce CRT nebo jiné funkce knihovny používají statická data (viz [možné chyby při předávání objektů CRT napříč hranicemi knihoven DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) pro další informace).

- Žádné metody vaší třídy (bez ohledu na vkládání) mohou používat typy, kde instance v souboru EXE a DLL mají rozdíly v statických datech.

Exportování tříd se můžete vyhnout definováním knihovny DLL, která definuje třídu s virtuálními funkcemi, a funkcemi, které lze volat pro vytvoření instance a odstranění objektů typu.  Pak můžete volat pouze virtuální funkce typu.

C4251 lze ignorovat, pokud je odvozeno od typu ve C++ standardní knihovně, kompilování ladicí verze ( **/MTD**) a kde chybová zpráva kompilátoru odkazuje na _Container_base.

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```
