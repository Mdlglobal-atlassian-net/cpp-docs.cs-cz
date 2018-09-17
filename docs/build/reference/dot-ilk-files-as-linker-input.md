---
title: . Soubory ilk jako vstup Linkeru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3b8de3758daf59a543cdcc9f3b73e1d6c6f0ce8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720587"
---
# <a name="ilk-files-as-linker-input"></a>Soubory .Ilk jako vstup linkeru

Při přírůstkové propojování, aktualizuje LINK soubor .ilk stav, který je vytvořen při prvním přírůstkové propojení. Tento soubor má stejný základní název jako soubor .exe nebo .dll a má .ilk rozšíření. Během následná přírůstková propojení aktualizuje LINK soubor .ilk. Pokud chybí soubor .ilk, odkaz provede úplné propojení. a vytvoří nový soubor .ilk. Pokud je soubor .ilk nepůjdou použít, provede odkaz nepřírůstková propojení. Podrobnosti o přírůstkové propojování, najdete v článku [přírůstkové propojení (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) možnost.

## <a name="see-also"></a>Viz také

[Vstupní soubory LINK](../../build/reference/link-input-files.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)