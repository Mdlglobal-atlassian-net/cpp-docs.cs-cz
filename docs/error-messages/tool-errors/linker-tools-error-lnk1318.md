---
title: Chyba LNK1318 Linkerů | Microsoft Docs
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1318
dev_langs:
- C++
helpviewer_keywords:
- LNK1318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 364c819c6ec2bf6e1195011eced6e6ad1699877b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570901"
---
# <a name="linker-tools-error-lnk1318"></a>LNK1318 chyby nástroje linkeru

> Neočekávaná chyba PDB; *způsobit* '*podrobnosti*.

Linkeru došlo k neočekávané chybě při otevírání, čtení nebo zápisu do souboru PDB.

Tato chybová zpráva se vytvářejí neobvyklé problémů v soubory PDB. *Způsobit* a *podrobnosti* reprezentaci informace k dispozici linkeru, když došlo k selhání. Toto nemusí být velmi užitečná, jako běžné chyby při práci s soubory PDB mít samostatné, informativnější chybové zprávy.

Vzhledem k tomu, že zdroj chyba neobvyklé, je pouze obecné Rady k dispozici pro řešení tohoto problému:

- Provést čisté operaci v sestavení adresářů a potom proveďte úplné sestavení vašeho řešení.

- Restartování počítače, nebo zkontrolujte mspdbsrv.exe stray nebo "zamrzlých" procesů a ukončení nich v Správce úloh.

- Vypněte antivirové kontroly v adresáře projektu.

- Použití [/Zf](../../build/reference/zf.md) – možnost kompilátoru při použití [/MP](../../build/reference/mp-build-with-multiple-processes.md) pomocí nástroje MSBuild nebo jiné paralelní proces sestavení.

- Zkuste sestavení pomocí 64bitovou hostovanou sadu nástrojů.

- Serializuje propojení zmírnit problémy paralelní odkaz v případě potřeby. K této chybě může dojít, pokud se spustí jednou instancí odkaz mspdbsrv.exe a je vypnutý předtím, než se provádí jiná instance odkaz jeho použití. Nevýhodou tato oprava je, že vaše sestavení projektu, může trvat výrazně delší dobu.