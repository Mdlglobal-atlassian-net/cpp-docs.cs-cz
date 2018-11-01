---
title: Soubory .Ilk jako vstup linkeru
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 012ca9aaa50ac2f8bb9d95ef77df5bb7127c5b79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595972"
---
# <a name="ilk-files-as-linker-input"></a>Soubory .Ilk jako vstup linkeru

Při přírůstkové propojování, aktualizuje LINK soubor .ilk stav, který je vytvořen při prvním přírůstkové propojení. Tento soubor má stejný základní název jako soubor .exe nebo .dll a má .ilk rozšíření. Během následná přírůstková propojení aktualizuje LINK soubor .ilk. Pokud chybí soubor .ilk, odkaz provede úplné propojení. a vytvoří nový soubor .ilk. Pokud je soubor .ilk nepůjdou použít, provede odkaz nepřírůstková propojení. Podrobnosti o přírůstkové propojování, najdete v článku [přírůstkové propojení (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) možnost.

## <a name="see-also"></a>Viz také

[Vstupní soubory LINK](../../build/reference/link-input-files.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)