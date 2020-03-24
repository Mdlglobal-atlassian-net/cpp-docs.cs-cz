---
title: Upozornění linkerů LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: 391a477625b51fd37eacc5d455801ce90d2abbc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194002"
---
# <a name="linker-tools-warning-lnk4070"></a>Upozornění linkerů LNK4070

/OUT: filename – direktiva v. EXP se liší od výstupního názvu souboru filename; ignoruje se direktiva.

`filename` zadaná v příkazu [název](../../build/reference/name-c-cpp.md) nebo [Knihovna](../../build/reference/library.md) , když se vytvoří soubor. exp, se liší od výstupního `filename`, který byl buď ve výchozím nastavení předpokládaný, nebo zadaný pomocí možnosti [/out](../../build/reference/out-output-file-name.md) .

Toto upozornění se zobrazí, pokud změníte název výstupního souboru ve vývojovém prostředí a tam, kde se soubor. def projektu neaktualizoval. Chcete-li vyřešit toto upozornění, ručně aktualizujte soubor. def.

Může dojít k potížím v klientském programu, který používá výslednou knihovnu DLL.
