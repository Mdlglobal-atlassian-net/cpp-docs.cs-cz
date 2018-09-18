---
title: Upozornění (úroveň 1) C4819 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4819
dev_langs:
- C++
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac468bc605c261b66f47fdf40efd1a01a5383d58
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074276"
---
# <a name="compiler-warning-level-1-c4819"></a>Kompilátor upozornění (úroveň 1) C4819

Tento soubor obsahuje znak, který nemůže být reprezentovaný v aktuální znakové stránce (číslo). Uložte soubor ve formátu Unicode, aby se zabránilo ztrátě dat.

C4819 vyvolá při kompilaci zdrojového souboru ANSI v systému, znakovou stránku, která nemůže představovat všechny znaky v souboru.

Chcete-li vyřešit C4819, uložte soubor ve formátu Unicode. V sadě Visual Studio, zvolte **souboru**, **pokročilé nastavení uložení**. V **pokročilé nastavení uložení** dialogové okno Vyberte kódování, které mohou představovat všechny znaky v souboru, například UTF-8 – a klikněte na tlačítko **OK**.