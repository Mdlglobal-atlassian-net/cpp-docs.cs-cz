---
title: Kompilátor upozornění (úroveň 1) C4819
ms.date: 11/04/2016
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: c0ca29a304fbd05cb0c6b7d1b06414304c70fb2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596609"
---
# <a name="compiler-warning-level-1-c4819"></a>Kompilátor upozornění (úroveň 1) C4819

Tento soubor obsahuje znak, který nemůže být reprezentovaný v aktuální znakové stránce (číslo). Uložte soubor ve formátu Unicode, aby se zabránilo ztrátě dat.

C4819 vyvolá při kompilaci zdrojového souboru ANSI v systému, znakovou stránku, která nemůže představovat všechny znaky v souboru.

Chcete-li vyřešit C4819, uložte soubor ve formátu Unicode. V sadě Visual Studio, zvolte **souboru**, **pokročilé nastavení uložení**. V **pokročilé nastavení uložení** dialogové okno Vyberte kódování, které mohou představovat všechny znaky v souboru, například UTF-8 – a klikněte na tlačítko **OK**.