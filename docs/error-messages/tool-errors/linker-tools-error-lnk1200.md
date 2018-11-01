---
title: Chyba linkerů LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: c99b25a83836f1ee0bc6ba622e42ea382c377172
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466830"
---
# <a name="linker-tools-error-lnk1200"></a>Chyba linkerů LNK1200

Chyba při čtení databáze programu: filename.

Nelze načíst databázi programu (PDB).

Tuto chybu může způsobovat poškození souborů.

Pokud `filename` je do souboru PDB soubor objektu znovu zkompilujte soubor objektu pomocí [/zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Pokud `filename` je soubor PDB pro hlavního výstupního souboru a k této chybě došlo během přírůstkového propojení, odstraňte soubor PDB a znovu připojit.