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
ms.openlocfilehash: 6a2e685d33b108ce542fdc6e3e0565cc37299c1c
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508738"
---
# <a name="creating-an-sbr-file"></a>Vytvoření souboru .Sbr

> [!WARNING]
> Přestože BSCMAKE je stále instalace sady Visual Studio, se už používá integrovaným vývojovým prostředím. Od verze Visual Studio 2008 je automaticky uloženy informace o procházení a symbol v soubor SDF SQL serveru ve složce řešení.

Vstupní soubory pro nástroje BSCMAKE jsou soubory .sbr. Kompilátor vytvoří soubor .sbr pro každý soubor objekt (.obj) se zkompiluje. Při vytváření nebo aktualizaci informačního souboru procházení, všechny soubory .sbr pro váš projekt musí být k dispozici na disku.

Chcete-li vytvořit soubor .sbr všechny možné informace, zadejte [/FR](fr-fr-create-dot-sbr-file.md).

Chcete-li vytvořit soubor .sbr, které nebude obsahovat místní symboly, zadejte [/Fr](fr-fr-create-dot-sbr-file.md). Pokud soubory .sbr obsahovat místní symboly, můžete stále vynechat je ze souboru .bsc pomocí nástroje BSCMAKE společnosti [/El – možnost](bscmake-options.md)`.`

Můžete vytvořit soubor .sbr bez provádí se úplná kompilace. Například můžete zadat /Zs – možnost kompilátoru a proveďte kontrolu syntaxe při zadání /FR nebo /Fr. stále generování souboru .sbr

Proces sestavení může být efektivnější, pokud soubory .sbr jsou zkomprimována nejprve odebrat neodkazované definice. Kompilátor automaticky sbalí soubory .sbr.

## <a name="see-also"></a>Viz také:

[Sestavení souboru .Bsc](building-a-dot-bsc-file.md)
