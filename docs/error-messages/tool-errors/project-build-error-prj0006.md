---
title: Chyba sestavení projektu PRJ0006
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: 816355276a203adba1401841ce02eb94a18085b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192780"
---
# <a name="project-build-error-prj0006"></a>Chyba sestavení projektu PRJ0006

Nepodařilo se otevřít dočasný soubor ' file '. Ujistěte se, že soubor existuje a že adresář není chráněn proti zápisu.

Vizuál C++ nemůže během procesu sestavování vytvořit dočasný soubor. Možné důvody zahrnují:

- Není k dispozici dočasný adresář.

- Dočasný adresář jen pro čtení.

- Nedostatek místa na disku.

- Složka $ (IntDir) je buď jen pro čtení, nebo obsahuje dočasné soubory, které jsou jen pro čtení.

K této chybě dojde také po chybě projektu PRJ0007: nelze vytvořit výstupní adresář ' Directory '. Error projektu PRJ0007 znamená, že se nepovedlo vytvořit adresář $ (IntDir), což způsobí, že vytváření dočasně souborů selže taky.

Dočasné soubory se vytvoří pokaždé, když zadáte:

- Soubor odpovědí.

- Vlastní krok sestavení.

- Událost sestavení.
