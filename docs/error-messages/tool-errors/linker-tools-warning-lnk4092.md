---
title: Upozornění Linkerů LNK4092 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4092
dev_langs:
- C++
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9b47b347e11e640425bc7840a0f78a33e9e3b7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113419"
---
# <a name="linker-tools-warning-lnk4092"></a>Upozornění linkerů LNK4092

sdílený oddíl s možností zápisu "části" obsahuje přemístění; bitové kopie se možná správně nespustí

Linker vydá toto varování, kdykoli budete chtít sdílený oddíl vás potenciálně závažný problém.

Jedním ze způsobů sdílení dat mezi více procesů je označte části jako "sdílené". Označení oddílu jako sdílené však může způsobit problémy. Například máte knihovnu DLL, která obsahuje deklarace, jako jsou to sdílené datové části:

```
int var = 1;
int *pvar = &var;
```

Linker nemůže vyřešit `pvar` vzhledem k tomu, že jeho hodnota závisí na kde načtení knihovny DLL v paměti, takže uloží záznam přemístění v knihovně DLL. Při načtení knihovny DLL do paměti, adresu `var` lze vyřešit a `pvar` přiřazené. Pokud jiný proces stejnou knihovnu DLL načte, ale nelze načíst ve stejnou adresu, přemístění adresy `var` bude aktualizován pro proces druhé a první proces adresního prostoru bude odkazovat na nesprávnou adresu.