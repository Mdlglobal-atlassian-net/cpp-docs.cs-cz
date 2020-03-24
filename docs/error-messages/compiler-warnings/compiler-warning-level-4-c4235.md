---
title: Upozornění kompilátoru (úroveň 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: df80bec2294929be463425d74d4bf00421b368e6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198429"
---
# <a name="compiler-warning-level-4-c4235"></a>Upozornění kompilátoru (úroveň 4) C4235

používá se nestandardní rozšíření: klíčové slovo klíčové slovo není v této architektuře podporované.

Kompilátor nepodporuje klíčové slovo, které jste použili.

Toto upozornění je automaticky povýšeno na chybu. Pokud chcete toto chování změnit, použijte [#pragma upozornění](../../preprocessor/warning.md). Pokud například chcete, aby se C4235 do upozornění úrovně 2, použijte následující řádek kódu.

```cpp
#pragma warning(2:4235)
```

v souboru zdrojového kódu.
