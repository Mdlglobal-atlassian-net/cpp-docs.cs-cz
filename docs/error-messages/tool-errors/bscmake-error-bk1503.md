---
title: Chyba nástroje BSCMAKE BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: 2c8ca005922c3c94b557e2f1052e8811099d9948
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555788"
---
# <a name="bscmake-error-bk1503"></a>Chyba nástroje BSCMAKE BK1503

Nelze zapisovat do souboru 'filename' [: z důvodu]

BscMake – kombinuje soubory .sbr vygenerované při kompilaci do jedné databáze prohlížeče. Pokud výsledná databáze prohlížeče přesáhne 64 MB, nebo pokud vstup (.sbr) souborů překračuje 4092, tato chyba bude vygenerován.

Je-li tento problém je více než 4092 soubory .sbr, je třeba zmenšit počet vstupních souborů. Z Visual Studia to můžete udělat [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) celý projekt a potom znovu zkontroluje každý soubor po souboru.

Je-li tento problém souboru .BSC nástrojem, který je větší než 64MB, snížení počtu soubory .sbr jako vstup se zmenší velikost výsledného souboru .bsc. Kromě toho množství informací o procházení, může být snížena prostřednictvím /Em (vyloučit – makro rozšířit symboly), /El (vyloučit lokální proměnné) a /Es (soubory vyloučit).

## <a name="see-also"></a>Viz také

[BSCMAKEE – možnosti](../../build/reference/bscmake-options.md)