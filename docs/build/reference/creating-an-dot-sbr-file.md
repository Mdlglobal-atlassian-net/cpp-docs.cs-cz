---
title: Vytváření. Soubor SBR | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac872dd13458c3fe15971f30a72b06e5510c5bd0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723681"
---
# <a name="creating-an-sbr-file"></a>Vytvoření souboru .Sbr

Vstupní soubory pro nástroje BSCMAKE jsou soubory .sbr. Kompilátor vytvoří soubor .sbr pro každý soubor objekt (.obj) se zkompiluje. Při vytváření nebo aktualizaci informačního souboru procházení, všechny soubory .sbr pro váš projekt musí být k dispozici na disku.

Chcete-li vytvořit soubor .sbr všechny možné informace, zadejte [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).

Chcete-li vytvořit soubor .sbr, které nebude obsahovat místní symboly, zadejte [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md). Pokud soubory .sbr obsahovat místní symboly, můžete stále vynechat je ze souboru .bsc pomocí nástroje BSCMAKE společnosti [/El – možnost](../../build/reference/bscmake-options.md)`.`

Můžete vytvořit soubor .sbr bez provádí se úplná kompilace. Například můžete zadat /Zs – možnost kompilátoru a proveďte kontrolu syntaxe při zadání /FR nebo /Fr. stále generování souboru .sbr

Proces sestavení může být efektivnější, pokud soubory .sbr jsou zkomprimována nejprve odebrat neodkazované definice. Kompilátor automaticky sbalí soubory .sbr.

## <a name="see-also"></a>Viz také

[Sestavení souboru .Bsc](../../build/reference/building-a-dot-bsc-file.md)