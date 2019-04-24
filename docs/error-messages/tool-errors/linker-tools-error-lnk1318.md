---
title: Chyba linkerů LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: 8ed6489a27d4c0e117f7f18281ff188f40936e0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160988"
---
# <a name="linker-tools-error-lnk1318"></a>Chyba linkerů LNK1318

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