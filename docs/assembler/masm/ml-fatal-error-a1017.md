---
title: Závažná chyba nástroje ML A1017
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 6fb0835cca135fc994866dc2453734d7b3012a64
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856823"
---
# <a name="ml-fatal-error-a1017"></a>Závažná chyba nástroje ML A1017

**Chybí název zdrojového souboru.**

ML nemůže najít soubor, který se má sestavit nebo předat linkeru.

Tato chyba se generuje, když zadáte možnosti příkazového řádku ML bez zadání názvu souboru, na který se má jednat. Chcete-li sestavit soubory, které nemají příponu. ASM, použijte možnost příkazového řádku **/ta** .

Tato chyba se dá vygenerovat taky vyvoláním ML bez parametrů, pokud proměnná prostředí ML obsahuje možnosti příkazového řádku.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>