---
title: 'Posunutí: diagnostika'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: a274b7c5f29b091b2bf29922abfa4d66d3447b47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344964"
---
# <a name="translation-diagnostics"></a>Posunutí: diagnostika

**2.1.1.3 ANSI** Způsob identifikace diagnostiky

Jazyk Microsoft C generuje chybové zprávy v následujícím tvaru:

> *filename* **(** *číslo řádku* **):** <em>number</em> *zpráva* *diagnostiky* **C**

kde *filename* je název zdrojového souboru, ve kterém došlo k chybě; *číslo řádku* je číslo řádku, ve kterém kompilátor zjistil chybu. *Diagnostika* je buď chyba, nebo upozornění. *číslo* je jedinečné číslo se čtyřmi číslicemi (před písmenem **C**, jak je uvedeno v syntaxi), které identifikuje chybu nebo varování; *zpráva* je vysvětlující zpráva.

## <a name="see-also"></a>Viz také

[Chování definované implementací](../c-language/implementation-defined-behavior.md)
