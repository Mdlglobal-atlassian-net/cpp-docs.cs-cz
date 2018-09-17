---
title: Nastavení možností Linkeru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- files [C++], LINK
- input files [C++], linker
- linker [C++], ways to set options
- linker [C++], switches
- input files [C++]
- object/library modules
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2fd99732c7f79b3c61ff5b31516b98a478ed4a8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713073"
---
# <a name="setting-linker-options"></a>Nastavení možností linkeru

Možnosti linkeru můžete nastavit uvnitř nebo mimo vývojové prostředí. Téma pro jednotlivé možnosti linkeru popisuje, jak lze nastavit ve vývojovém prostředí. Zobrazit [možnosti Linkeru](../../build/reference/linker-options.md) úplný seznam.

Při spuštění odkaz mimo vývojové prostředí můžete určit vstup jednu nebo více způsoby:

- Na [příkazového řádku](../../build/reference/linker-command-line-syntax.md)

- Pomocí [soubory příkazů](../../build/reference/link-command-files.md)

- V [proměnné prostředí](../../build/reference/link-environment-variables.md)

ODKAZ první procesy možnosti zadané v proměnné prostředí LINK, za nímž následuje možnosti v pořadí, v jakém jsou uvedeny v příkazovém řádku a v souborech příkazů. Pokud možnost se opakuje různé argumenty, posledním blokem zpracovat přednost.

Možnosti platí pro celé sestavení; bez možností je použít na konkrétní vstupní soubory.

## <a name="see-also"></a>Viz také

[Referenční zdroje k sestavení programu v jazyce C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)