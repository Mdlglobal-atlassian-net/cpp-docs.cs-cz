---
title: Chyba linkerů LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: 9dcc37bd74a25e29726529346b1578bb8b18ac3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195133"
---
# <a name="linker-tools-error-lnk1200"></a>Chyba linkerů LNK1200

Chyba při čtení databáze programu filename

Nebylo možné přečíst programovou databázi (PDB).

Tato chyba může být způsobena poškozením souboru.

Pokud je `filename` PDB pro soubor objektu, překompilujte soubor objektu pomocí [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Pokud je `filename` PDB pro hlavní výstupní soubor a k této chybě došlo během přírůstkového propojení, odstraňte soubor PDB a znovu propojte.
