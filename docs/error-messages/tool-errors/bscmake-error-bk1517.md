---
title: Chyba nástroje BSCMAKE BK1517 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1517
dev_langs:
- C++
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 941773fbcf65a3b1c1a6041a1e7a067cfc286823
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097052"
---
# <a name="bscmake-error-bk1517"></a>Chyba nástroje BSCMAKE BK1517

zdrojový soubor pro sbrfile zkompilovaná /Yc a /Yu

Soubor .sbr odkazuje sama na sebe. Po kompilaci s možností/Yc to bylo pravděpodobně rekompilovány/YU. Resetovat možnosti kompilátoru pro zdrojový soubor pro /Yc a pak vyberte **znovu sestavit** generovat nové soubory .sbr. Nezkompilujete zdrojového souboru s/Yu.