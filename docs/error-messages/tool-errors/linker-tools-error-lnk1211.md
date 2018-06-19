---
title: Chyba linkerů Lnk1211 | Microsoft Docs
ms.date: 12/05/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1211
dev_langs:
- C++
helpviewer_keywords:
- LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57948556ae7b94b9a1788b7cb4453646b5b504f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300381"
---
# <a name="linker-tools-error-lnk1211"></a>Chyba linkerů LNK1211

> informace o předkompilovaných typu nebyl nalezen. '*filename*' není propojená nebo přepsání

*Filename* souboru objektu, kompilovat s použitím [/Yc](../../build/reference/yc-create-precompiled-header-file.md), nebyl specifikován v příkazu odkaz nebo byl přepsán.

Pokud vytváříte ladicí knihovny, který používá předkompilovaných hlaviček, a pokud zadáte **/Yc** a [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), Visual C++ vygeneruje soubor předkompilovaných objekt, který obsahuje informace o ladění. Této chybě dojde, pouze když ukládáte soubor předkompilovaných objektu v knihovně, použijte k tvorbě spustitelné bitové kopie knihovny, a soubory objektů, které jsou odkazované neobsahují přenositelné odkazy na některé funkce, které definuje soubor předkompilovaných objektu.

Chcete-li vyřešit tuto situaci dvěma způsoby:

- Zadejte [/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) – možnost kompilátoru přidat informace o ladění z předkompilované hlavičky pro každý modul objektu. Tato metoda je méně vhodné, protože obecně vytváří velkého objektu moduly, které může prodloužit doba nutná k propojení aplikace.

- Zadejte [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) a předat název libovolný řetězec, když vytvoříte předkompilovaný hlavičkový soubor, který neobsahuje žádné definice funkcí. To bude směrovat kompilátoru pro vytvoření symbolu v souboru předkompilovaných objektu a pro vydávání odkaz na tento symbol do každého souboru objektu, který použít předkompilovaný hlavičkový soubor, který je přidružený soubor předkompilovaných objektu.

Když zkompilujete modul s **/Yc** a **/Yl**, kompilátor vytvoří symbol podobná `__@@_PchSym_@00@...@symbol_name`, kde se třemi tečkami (...) představuje řetězec znaků generované kompilátorem a uloží jej do modul objektu. Zdrojový soubor, který kompilujete s Tento předkompilovaných hlaviček odkazuje zadaný symbol, což způsobí, že linkeru zahrnuje modul objektu a jeho ladicí informace z knihovny.
