---
title: Chyba linkerů LNK1211
ms.date: 12/05/2017
f1_keywords:
- LNK1211
helpviewer_keywords:
- LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
ms.openlocfilehash: 7c918cacb87460c2aad30285b750d9b170425534
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242666"
---
# <a name="linker-tools-error-lnk1211"></a>Chyba linkerů LNK1211

> Předkompilované informace o typu nebyl nalezen. "*filename*" není propojený nebo přepsaný

*Filename* soubor objektu zkompilován s použitím [/Yc](../../build/reference/yc-create-precompiled-header-file.md), nebyl zadaný v příkazu propojení nebo byl přepsán.

Pokud vytváříte knihovnu ladění, která používá předkompilovaných hlaviček, a pokud zadáte **/Yc** a [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), Visual C++ generuje soubor předkompilovaný objekt, který obsahuje informace o ladění. K této chybě dojde, jenom když uložíte soubor předkompilované objektů v knihovně, použití knihovny k sestavení spustitelnou bitovou kopii a objektových souborů, které jsou odkazovány neobsahují tranzitivní odkazy na některé z funkcí, které definuje soubor předkompilované objektu.

Chcete-li této situaci dvěma způsoby:

- Zadejte [/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) – možnost kompilátoru můžete přidat informace o ladění z předkompilované hlavičky do každého objektu modulu. Tato metoda je méně vhodné, protože obecně vytváří velkého objektu moduly, které může prodloužit dobu požadovanou pro propojení aplikace.

- Zadejte [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) a předejte mu název libovolný řetězec, když vytvoříte soubor předkompilované hlavičky, která neobsahuje žádné definice funkce. To instruuje kompilátor vytvoření symbolu v souboru předkompilovaný objekt a vygenerovat odkaz na tento symbol v každém objektu souboru, který používá soubor předkompilované hlavičky, který je spojen se souborem předkompilované objektu.

Pokud kompilujete modul s **/Yc** a **/Yl**, kompilátor vytvoří symbol podobný `__@@_PchSym_@00@...@symbol_name`, kde se třemi tečkami (...) představuje řetězce znaků vygenerovaný kompilátorem a uloží jej do objekt module. Zdrojový soubor, který kompilovat s této předkompilované hlavičky odkazuje na zadaný symbol, což způsobí, že linkeru, aby zahrnul modul objektu a jeho ladicí informace z knihovny.
