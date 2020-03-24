---
title: Upozornění kompilátoru (úroveň 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: c27f16f7d2933ca1860b304afa6e04f96f0687f0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173904"
---
# <a name="compiler-warning-level-4-c4234"></a>Upozornění kompilátoru (úroveň 4) C4234

používá se nestandardní rozšíření: klíčové slovo klíčové slovo rezervované pro budoucí použití

Kompilátor ještě neimplementuje klíčové slovo, které jste použili.

Toto upozornění je automaticky povýšeno na chybu. Pokud chcete toto chování změnit, použijte [#pragma upozornění](../../preprocessor/warning.md). Pokud například chcete, aby se C4234 problém s upozorněním na úrovni 4,

```cpp
#pragma warning(2:4234)
```

v souboru zdrojového kódu.
