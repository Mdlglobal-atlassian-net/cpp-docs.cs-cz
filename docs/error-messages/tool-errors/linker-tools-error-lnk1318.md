---
title: LNK1318 chyba nástrojů linkeru
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: 8ed6489a27d4c0e117f7f18281ff188f40936e0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648731"
---
# <a name="linker-tools-error-lnk1318"></a>LNK1318 chyba nástrojů linkeru

> Neočekávaná chyba souboru .pdb; *způsobit* "*podrobnosti*.

Linker došlo k neočekávané chybě při otevírání, čtení nebo zápis do souboru PDB.

Pro běžné problémy v souborech PDB je vytvořen tato chybová zpráva. *Způsobit* a *podrobnosti* představují k dispozici informace o linkeru, kdy došlo k chybě. To nemusí být velmi užitečné, jako běžných chyb při práci se soubory PDB mít samostatné, další chybové zprávy.

Vzhledem k tomu, že zdroj chyby neobvyklé, je dostupná jenom obecné Rady k řešení tohoto problému:

- Operace vyčištění v adresáře sestavení a poté proveďte úplné sestavení vašeho řešení.

- Restartování počítače, nebo zkontrolujte mspdbsrv.exe zapomenutý nebo ukončování "zamrzlých" procesů a ukončit v úloh.

- Vypněte antivirové kontroly v adresářích projektu.

- Použití [/Zf](../../build/reference/zf.md) – možnost kompilátoru při použití [/MP](../../build/reference/mp-build-with-multiple-processes.md) s MSBuild nebo jiné paralelní procesu sestavení.

- Vyzkoušejte vytváření s použitím 64bitovou hostovanou sadu nástrojů.

- Serializace za účelem zmírnění problémů paralelní odkaz v případě potřeby propojení. Tato chyba může nastat, pokud mspdbsrv.exe spustí jednu instanci propojení a je vypnutý předtím, než jiná instance propojení se provádí jeho použití. Nevýhodou této opravy je, že vaše sestavení projektu může trvat výrazně déle.