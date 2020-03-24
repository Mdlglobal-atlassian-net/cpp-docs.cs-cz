---
title: Upozornění příkazového řádku D9026
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 59dfcdc97fb9caf60a018cb20583ee6fca3dcb27
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196700"
---
# <a name="command-line-warning-d9026"></a>Upozornění příkazového řádku D9026

možnosti se vztahují na celý příkazový řádek.

Po zadání názvu souboru se v příkazu zadala možnost. Možnost byla použita na soubor, který mu předchází.

Například v příkazu

```
CL verdi.c /G5 puccini.c
```

soubor VERDI. c se zkompiluje pomocí možnosti/G5, nikoli výchozí/G4.

Toto chování se liší od předchozích verzí, které používaly pouze možnosti určené před názvem souboru, výsledkem je VERDI. c kompilovány pomocí/G4 a PUCCINI. c kompilovány pomocí/G5.
