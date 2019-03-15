---
title: Soubory .Ilk jako vstup linkeru
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 252c1cd6e17346954fce7ebf16134246da76ba57
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808466"
---
# <a name="ilk-files-as-linker-input"></a>Soubory .Ilk jako vstup linkeru

Při přírůstkové propojování, aktualizuje LINK soubor .ilk stav, který je vytvořen při prvním přírůstkové propojení. Tento soubor má stejný základní název jako soubor .exe nebo .dll a má .ilk rozšíření. Během následná přírůstková propojení aktualizuje LINK soubor .ilk. Pokud chybí soubor .ilk, odkaz provede úplné propojení. a vytvoří nový soubor .ilk. Pokud je soubor .ilk nepůjdou použít, provede odkaz nepřírůstková propojení. Podrobnosti o přírůstkové propojování, najdete v článku [přírůstkové propojení (/ INCREMENTAL)](incremental-link-incrementally.md) možnost.

## <a name="see-also"></a>Viz také:

[Vstupní soubory LINK](link-input-files.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
