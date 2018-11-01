---
title: 'Posunutí: diagnostika'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: 4863b97dc1db7ff295b5f786ca97da2551d0fa62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664994"
---
# <a name="translation-diagnostics"></a>Posunutí: diagnostika

**ANSI 2.1.1.3** jak identifikovat diagnostiky

Jazyk Microsoft C generuje chybové zprávy v následujícím tvaru:

> *Název souboru* **(** *číslo řádku* **):** *diagnostických* **C**  <em>číslo</em> *zprávy*

kde *filename* je název zdrojového souboru, ve kterém došlo k chybě; *číslo řádku* je číslo řádku, ve kterém kompilátor zjistil chybu. *diagnostických* je "Chyba" nebo "upozornění"; *číslo* je jedinečné čtyřmístné číslo (předcházet párový příkaz **C**, jak je uvedeno v syntaxi) identifikující chybu nebo upozornění; *zpráva* vysvětlující zpráva.

## <a name="see-also"></a>Viz také

[Chování definované implementací](../c-language/implementation-defined-behavior.md)