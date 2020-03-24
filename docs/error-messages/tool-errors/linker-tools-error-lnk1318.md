---
title: Chyba linkerů LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: a61c11a9cbb25fea6fddc0bf1c5c4c2a7af1cf4f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183576"
---
# <a name="linker-tools-error-lnk1318"></a>Chyba linkerů LNK1318

> Neočekávaná chyba PDB; *Příčina* *Podrobnosti*

V linkeru došlo k neočekávané chybě při otevírání, čtení nebo zápisu do souboru PDB.

Tato chybová zpráva se vytvoří pro Neběžné problémy v souborech PDB. *Příčina* a *Podrobnosti* reprezentují informace, které jsou k dispozici linkeru v okamžiku, kdy došlo k chybě. To nemusí být velmi užitečné, protože běžné chyby při práci se soubory PDB mají samostatné, více informativní chybové zprávy.

Vzhledem k tomu, že zdroj chyby je neobvyklý, je pro vyřešení tohoto problému k dispozici pouze obecná Rada:

- Proveďte čistou operaci v adresářích sestavení a pak proveďte úplné sestavení vašeho řešení.

- Restartujte počítač, nebo se podívejte na osamocené nebo nereagující procesy Mspdbsrv. exe a ukončete je v TaskManager.

- Vypněte kontroly antivirové ochrany v adresářích projektu.

- Použijte možnost kompilátoru [/ZF](../../build/reference/zf.md) , pokud používáte [/MP](../../build/reference/mp-build-with-multiple-processes.md) s nástrojem MSBuild nebo jiným paralelním procesem sestavení.

- Zkuste sestavovat pomocí sady nástrojů hostovaného pro 64.

- V případě potřeby můžete vyserializovat propojení a zmírnit problémy s paralelním propojením. Tato chyba může být způsobena tím, že Mspdbsrv. exe je spuštěn jednou instancí propojení a je vypnut před tím, než ji bude provedeno pomocí jiné instance propojení. Nevýhodou k této opravě je, že sestavení projektu může trvat mnohem déle.
