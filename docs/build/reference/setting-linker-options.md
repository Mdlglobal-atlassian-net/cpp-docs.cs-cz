---
title: Nastavení možností linkeru
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], LINK
- input files [C++], linker
- linker [C++], ways to set options
- linker [C++], switches
- input files [C++]
- object/library modules
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
ms.openlocfilehash: 61f4ee8d02cda5b2cd270d7ef789bf58060e7fdf
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423167"
---
# <a name="setting-linker-options"></a>Nastavení možností linkeru

Možnosti linkeru můžete nastavit uvnitř nebo mimo vývojové prostředí. Téma pro jednotlivé možnosti linkeru popisuje, jak lze nastavit ve vývojovém prostředí. Zobrazit [možnosti Linkeru](../../build/reference/linker-options.md) úplný seznam.

Při spuštění odkaz mimo vývojové prostředí můžete určit vstup jednu nebo více způsoby:

- Na [příkazového řádku](../../build/reference/linker-command-line-syntax.md)

- Pomocí [soubory příkazů](../../build/reference/link-command-files.md)

- V [proměnné prostředí](../../build/reference/link-environment-variables.md)

ODKAZ první procesy možnosti zadané v proměnné prostředí LINK, za nímž následuje možnosti v pořadí, v jakém jsou uvedeny v příkazovém řádku a v souborech příkazů. Pokud možnost se opakuje různé argumenty, posledním blokem zpracovat přednost.

Možnosti platí pro celé sestavení; bez možností je použít na konkrétní vstupní soubory.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
