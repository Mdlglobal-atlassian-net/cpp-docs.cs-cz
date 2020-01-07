---
title: Závažná chyba nástroje ML A1017
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 523fed26afae5a88c5f154283487d3453a2e48c7
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318056"
---
# <a name="ml-fatal-error-a1017"></a>Závažná chyba nástroje ML A1017

**Chybí název zdrojového souboru.**

ML nemůže najít soubor, který se má sestavit nebo předat linkeru.

Tato chyba se generuje, když zadáte možnosti příkazového řádku ML bez zadání názvu souboru, na který se má jednat. Chcete-li sestavit soubory, které nemají příponu. ASM, použijte možnost příkazového řádku **/ta** .

Tato chyba se dá vygenerovat taky vyvoláním ML bez parametrů, pokud proměnná prostředí ML obsahuje možnosti příkazového řádku.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](ml-error-messages.md)
