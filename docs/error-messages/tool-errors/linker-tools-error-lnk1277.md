---
title: Chyba linkerů LNK1277
ms.date: 11/04/2016
f1_keywords:
- LNK1277
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
ms.openlocfilehash: 7c00fb32e4b36eff119195efbb34d536d80df6a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183654"
---
# <a name="linker-tools-error-lnk1277"></a>Chyba linkerů LNK1277

v souboru PGD nebyl nalezen záznam objektu.

Při použití [/LTCG: PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md)se cesta jednoho ze vstupních souborů. lib, def nebo. obj liší od cesty, na které byly nalezeny během/LTCG: PGINSTRUMENT. To může být vysvětleno změnou v proměnné prostředí LIB po/LTCG: PGINSTRUMENT. Úplná cesta ke vstupním souborům je uložena v souboru. pgd.

/LTCG: PGOPTIMIZE vyžaduje, aby byly vstupy stejné jako fáze/LTCG: PGINSTRUMENT.

Chcete-li vyřešit toto upozornění, proveďte jednu z následujících akcí:

- Spusťte/LTCG: PGINSTRUMENT, znovu proveďte všechny testovací běhy a spusťte/LTCG: PGOPTIMIZE.

- Změňte proměnnou prostředí LIB na to, co bylo v době, kdy jste spustili/LTCG: PGINSTRUMENT.

Nedoporučujeme vám pracovat s LINKERŮ LNK1277 pomocí/LTCG: PGUPDATE.
