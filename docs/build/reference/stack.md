---
title: -STACK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /stack
dev_langs:
- C++
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8deb3e3bedcb773aa01ae5f1c3ff66ce9d509f2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716657"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Poznámky

Tato možnost nastaví velikost zásobníku v bajtech a přebírá argumenty v zápisu jazyka C nebo decimal. Možnost/Stack se vztahuje pouze na spustitelný soubor.

*Rezervovat* argument určuje celkové přidělení zásobníku ve virtuální paměti. Editbin – zaokrouhlí nahoru zadanou hodnotu do nejbližší 4 bajty.

Volitelný `commit` argument podléhá interpretaci operačního systému. V systému Windows NT, Windows 95 a Windows 98 `commit` určuje množství fyzické paměti do okamžiku přidělit. Potvrzená virtuální paměť rezervuje místo ve stránkovacím souboru. Vyšší `commit` hodnotu šetří čas, kdy aplikace potřebuje více místa v zásobníku, ale zvyšuje požadavky na paměť a případně čas spuštění.

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](../../build/reference/editbin-options.md)