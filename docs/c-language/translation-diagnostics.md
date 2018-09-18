---
title: 'Posunutí: Diagnostika | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d297cfd4f4dee49d3344ae2f159f85682f05ea2f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017583"
---
# <a name="translation-diagnostics"></a>Posunutí: diagnostika

**ANSI 2.1.1.3** jak identifikovat diagnostiky

Jazyk Microsoft C generuje chybové zprávy v následujícím tvaru:

> *Název souboru* **(** *číslo řádku* **):** *diagnostických* **C**  <em>číslo</em> *zprávy*

kde *filename* je název zdrojového souboru, ve kterém došlo k chybě; *číslo řádku* je číslo řádku, ve kterém kompilátor zjistil chybu. *diagnostických* je "Chyba" nebo "upozornění"; *číslo* je jedinečné čtyřmístné číslo (předcházet párový příkaz **C**, jak je uvedeno v syntaxi) identifikující chybu nebo upozornění; *zpráva* vysvětlující zpráva.

## <a name="see-also"></a>Viz také

[Chování definované implementací](../c-language/implementation-defined-behavior.md)