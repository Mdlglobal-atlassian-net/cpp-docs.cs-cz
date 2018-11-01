---
title: Závažná chyba nástroje ML A1017
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 22a16569364760d0cb1d01011405f7a11dd21cac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560820"
---
# <a name="ml-fatal-error-a1017"></a>Závažná chyba nástroje ML A1017

**Chybějící název zdrojového souboru**

ML nejde najít soubor sestavení nebo předání do propojovacího programu.

Tato chyba se vygeneruje, když poskytují ML možnosti příkazového řádku bez zadání názvu souboru k provedení akce. Chcete-li uspořádat soubory, které nemají příponu .asm, použijte **/Ta** možnost příkazového řádku.

Tato chyba může být také generován volání ML bez parametrů, pokud ML – proměnná prostředí obsahuje možnosti příkazového řádku.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>