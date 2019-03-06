---
title: Soubory .Ilk jako vstup linkeru
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 6c0eb5627d7dd1b414351dc65685c0c5071d249e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422504"
---
# <a name="ilk-files-as-linker-input"></a>Soubory .Ilk jako vstup linkeru

Při přírůstkové propojování, aktualizuje LINK soubor .ilk stav, který je vytvořen při prvním přírůstkové propojení. Tento soubor má stejný základní název jako soubor .exe nebo .dll a má .ilk rozšíření. Během následná přírůstková propojení aktualizuje LINK soubor .ilk. Pokud chybí soubor .ilk, odkaz provede úplné propojení. a vytvoří nový soubor .ilk. Pokud je soubor .ilk nepůjdou použít, provede odkaz nepřírůstková propojení. Podrobnosti o přírůstkové propojování, najdete v článku [přírůstkové propojení (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) možnost.

## <a name="see-also"></a>Viz také:

[Vstupní soubory LINK](../../build/reference/link-input-files.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
