---
title: Chyba nástroje BSCMAKE BK1503 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1503
dev_langs:
- C++
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16bf228804cb24f4fe7a2428dc581116d4cec91d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064660"
---
# <a name="bscmake-error-bk1503"></a>Chyba nástroje BSCMAKE BK1503

Nelze zapisovat do souboru 'filename' [: z důvodu]

BscMake – kombinuje soubory .sbr vygenerované při kompilaci do jedné databáze prohlížeče. Pokud výsledná databáze prohlížeče přesáhne 64 MB, nebo pokud vstup (.sbr) souborů překračuje 4092, tato chyba bude vygenerován.

Je-li tento problém je více než 4092 soubory .sbr, je třeba zmenšit počet vstupních souborů. Z Visual Studia to můžete udělat [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) celý projekt a potom znovu zkontroluje každý soubor po souboru.

Je-li tento problém souboru .BSC nástrojem, který je větší než 64MB, snížení počtu soubory .sbr jako vstup se zmenší velikost výsledného souboru .bsc. Kromě toho množství informací o procházení, může být snížena prostřednictvím /Em (vyloučit – makro rozšířit symboly), /El (vyloučit lokální proměnné) a /Es (soubory vyloučit).

## <a name="see-also"></a>Viz také

[BSCMAKEE – možnosti](../../build/reference/bscmake-options.md)