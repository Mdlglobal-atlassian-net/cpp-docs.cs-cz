---
title: Závažná chyba nástroje ML A1017 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb98eab68da417526a75beaa57870ce906c85a8d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688556"
---
# <a name="ml-fatal-error-a1017"></a>Závažná chyba nástroje ML A1017

**Chybějící název zdrojového souboru**

ML nejde najít soubor sestavení nebo předání do propojovacího programu.

Tato chyba se vygeneruje, když poskytují ML možnosti příkazového řádku bez zadání názvu souboru k provedení akce. Chcete-li uspořádat soubory, které nemají příponu .asm, použijte **/Ta** možnost příkazového řádku.

Tato chyba může být také generován volání ML bez parametrů, pokud ML – proměnná prostředí obsahuje možnosti příkazového řádku.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>