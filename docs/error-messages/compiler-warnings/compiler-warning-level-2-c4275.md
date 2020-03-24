---
title: Upozornění kompilátoru (úroveň 2) C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: ad12c1c27006a57c8339e9dad82e4d8e1a239a6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161994"
---
# <a name="compiler-warning-level-2-c4275"></a>Upozornění kompilátoru (úroveň 2) C4275

> Třída rozhraní*class_1*, která není typu DLL, se používá jako základ pro třídu rozhraní dll*class_2*.

Exportovaná třída byla odvozena z třídy, která nebyla exportována.

Chcete-li minimalizovat možnost poškození dat při exportu třídy s [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), ujistěte se, že:

- Všechna vaše statická data jsou k dispozici prostřednictvím funkcí, které jsou exportovány z knihovny DLL.

- Žádné vložené metody třídy nemůžou upravovat statická data.

- Žádné vložené metody vaší třídy nepoužívají funkce CRT nebo jiné funkce knihovny, které používají statická data.

- Žádné vložené funkce třídy nepoužívají funkce CRT nebo jiné funkce knihovny, kde přistupujete ke statickým datům.

- Žádné metody vaší třídy (bez ohledu na vkládání) mohou používat typy, kde instance v souboru EXE a DLL mají rozdíly v statických datech.

Exportování tříd se můžete vyhnout definováním knihovny DLL, která definuje třídu s virtuálními funkcemi, a funkcemi, které lze volat pro vytvoření instance a odstranění objektů typu.  Pak můžete volat pouze virtuální funkce typu.

C4275 lze v vizuálu C++ ignorovat, pokud se odvozují z typu ve C++ standardní knihovně, kompilování ladicí verze ( **/MTD**) a kde chybová zpráva kompilátoru odkazuje na `_Container_base`.

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```
