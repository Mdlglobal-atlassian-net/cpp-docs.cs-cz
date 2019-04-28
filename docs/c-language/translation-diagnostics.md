---
title: 'Překlad: Diagnostika'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: a274b7c5f29b091b2bf29922abfa4d66d3447b47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344964"
---
# <a name="translation-diagnostics"></a>Překlad: Diagnostika

**ANSI 2.1.1.3** jak identifikovat diagnostiky

Jazyk Microsoft C generuje chybové zprávy v následujícím tvaru:

> *Název souboru* **(** *číslo řádku* **):** *diagnostických* **C**  <em>číslo</em> *zprávy*

kde *filename* je název zdrojového souboru, ve kterém došlo k chybě; *číslo řádku* je číslo řádku, ve kterém kompilátor zjistil chybu. *diagnostických* je "Chyba" nebo "upozornění"; *číslo* je jedinečné čtyřmístné číslo (předcházet párový příkaz **C**, jak je uvedeno v syntaxi) identifikující chybu nebo upozornění; *zpráva* vysvětlující zpráva.

## <a name="see-also"></a>Viz také:

[Chování definované implementací](../c-language/implementation-defined-behavior.md)
