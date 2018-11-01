---
title: Chyba linkerů LNK1112
ms.date: 11/04/2016
f1_keywords:
- LNK1112
helpviewer_keywords:
- LNK1112
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
ms.openlocfilehash: bc01d56fb8144d23b91c82a7f791a70a5dadb7ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607087"
---
# <a name="linker-tools-error-lnk1112"></a>Chyba linkerů LNK1112

> Typ modulu počítače "*type1*"je v konfliktu s cílovým typem počítače"*type2*.

## <a name="remarks"></a>Poznámky

Soubory objektů zadán jako vstup byly zkompilovány pro typy jiné počítače.

Například, pokud se pokusíte připojit soubor objektu zkompilovaná **/CLR** a soubor objektu zkompilovaná **/CLR: pure** (typ CEE počítače), linker vygeneruje chybu LNK1112. **/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Podobně pokud vytvoříte jeden modul s x64 kompilátoru a jiný modul s x86 kompilátoru a pokuste se propojují, linker vytvoří LNK1112.

Důvodem této chyby je, pokud vyvíjíte aplikace 64-bit, ale nebyly nainstalovanou některou z kompilátorů Visual C++ 64-bit. V takovém případě 64-bit konfigurace nebudou k dispozici. Chcete tento problém vyřešit, spusťte instalační program pro Visual Studio a nainstalovat chybějící součásti C++.

K této chybě může dojít, pokud změníte **konfigurace aktivního řešení** v **nástroje Configuration Manager** a pokuste se sestavit projekt před odstraněním projektu zprostředkující soubory. Chcete-li tuto chybu vyřešit, vyberte **znovu sestavit řešení** z **sestavení** nabídky. Můžete také vybrat **Vyčistit řešení** z **sestavení** nabídky a pak vytvořte řešení.

## <a name="see-also"></a>Viz také:

- [Chyby a upozornění linkerů](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
