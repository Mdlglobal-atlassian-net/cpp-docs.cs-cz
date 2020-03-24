---
title: Chyba nástroje BSCMAKE BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: e0f05b3979024cb053394c51fa9337197b5de7bf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197857"
---
# <a name="bscmake-error-bk1503"></a>Chyba nástroje BSCMAKE BK1503

do souboru filename [: důvod] nejde zapisovat.

BSCMAKE kombinuje soubory. sbr generované během kompilace do jedné databáze prohlížeče. Pokud výsledná databáze prohlížeče překračuje 64 MB nebo pokud počet vstupních (. SBR) souborů překročí 4092, bude tato chyba vyvolána.

Pokud problém způsobuje více než 4092 souborů. SBR, musíte snížit počet vstupních souborů. V rámci sady Visual Studio můžete to provést [/fr](../../build/reference/fr-fr-create-dot-sbr-file.md) celým projektem a pak znovu kontrolovat soubor podle souborů.

Pokud je problém způsobený souborem. BSC větším než 64 MB, zmenšuje se počet souborů. sbr jako vstup, čímž se zmenší velikost výsledného souboru. BSC. Kromě toho může být množství informací o procházení zmenšeno pomocí/em (vyloučit rozšířené symboly makra),/El (vyloučení místních proměnných) a/ES (vyloučit systémové soubory).

## <a name="see-also"></a>Viz také

[BSCMAKEE – možnosti](../../build/reference/bscmake-options.md)
