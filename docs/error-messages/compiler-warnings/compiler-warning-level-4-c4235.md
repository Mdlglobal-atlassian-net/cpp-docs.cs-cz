---
title: Upozornění (úroveň 4) C4235 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4235
dev_langs:
- C++
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9e709017e51101efe53a8697bb145014f200871
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031818"
---
# <a name="compiler-warning-level-4-c4235"></a>Kompilátor upozornění (úroveň 4) C4235

používá se nestandardní rozšíření: klíčové slovo '– klíčové slovo' není na této architektuře podporováno

Kompilátor nepodporuje klíčové slovo, které jste použili.

Toto upozornění je automaticky povýšen na chybu. Pokud chcete toto chování upravit, použijte [varování #pragma](../../preprocessor/warning.md). Například chcete-li C4235 do upozornění úrovně 2, použijte následující řádek kódu

```
#pragma warning(2:4235)
```

v souboru zdrojového kódu.