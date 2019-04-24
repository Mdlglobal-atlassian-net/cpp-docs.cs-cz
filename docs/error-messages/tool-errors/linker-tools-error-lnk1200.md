---
title: Chyba linkerů LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: c99b25a83836f1ee0bc6ba622e42ea382c377172
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213547"
---
# <a name="linker-tools-error-lnk1200"></a>Chyba linkerů LNK1200

Chyba při čtení databáze programu: filename.

Nelze načíst databázi programu (PDB).

Tuto chybu může způsobovat poškození souborů.

Pokud `filename` je do souboru PDB soubor objektu znovu zkompilujte soubor objektu pomocí [/zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Pokud `filename` je soubor PDB pro hlavního výstupního souboru a k této chybě došlo během přírůstkového propojení, odstraňte soubor PDB a znovu připojit.