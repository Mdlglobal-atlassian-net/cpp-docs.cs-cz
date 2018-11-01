---
title: Vytvoření souboru .Sbr
ms.date: 11/04/2016
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
ms.openlocfilehash: 63f007e567f3c1db556ba6a7f0c1a354c449f31b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501003"
---
# <a name="creating-an-sbr-file"></a>Vytvoření souboru .Sbr

Vstupní soubory pro nástroje BSCMAKE jsou soubory .sbr. Kompilátor vytvoří soubor .sbr pro každý soubor objekt (.obj) se zkompiluje. Při vytváření nebo aktualizaci informačního souboru procházení, všechny soubory .sbr pro váš projekt musí být k dispozici na disku.

Chcete-li vytvořit soubor .sbr všechny možné informace, zadejte [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).

Chcete-li vytvořit soubor .sbr, které nebude obsahovat místní symboly, zadejte [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md). Pokud soubory .sbr obsahovat místní symboly, můžete stále vynechat je ze souboru .bsc pomocí nástroje BSCMAKE společnosti [/El – možnost](../../build/reference/bscmake-options.md)`.`

Můžete vytvořit soubor .sbr bez provádí se úplná kompilace. Například můžete zadat /Zs – možnost kompilátoru a proveďte kontrolu syntaxe při zadání /FR nebo /Fr. stále generování souboru .sbr

Proces sestavení může být efektivnější, pokud soubory .sbr jsou zkomprimována nejprve odebrat neodkazované definice. Kompilátor automaticky sbalí soubory .sbr.

## <a name="see-also"></a>Viz také

[Sestavení souboru .Bsc](../../build/reference/building-a-dot-bsc-file.md)