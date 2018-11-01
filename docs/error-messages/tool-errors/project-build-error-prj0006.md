---
title: Chyba sestavení projektu PRJ0006
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: d62c774411fda80a3e94044b3272567177328ff5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451556"
---
# <a name="project-build-error-prj0006"></a>Chyba sestavení projektu PRJ0006

Nepovedlo se otevřít dočasný soubor 'file'. Ujistěte se, že soubor existuje a že adresář není chráněn proti zápisu.

Visual C++ nelze vytvořit dočasný soubor během procesu sestavení. Možné důvody zahrnují:

- Žádný adresář temp.

- Jen pro čtení dočasného adresáře.

- Nedostatek místa na disku.

- Složka $(IntDir) je buď jen pro čtení nebo obsahuje dočasné soubory, které jsou jen pro čtení.

Tato chyba se vrátí taky následující chybu PRJ0007: Nelze vytvořit výstupní adresář 'directory'. Chyba PRJ0007 znamená, že nelze vytvořit adresář $(IntDir) zdání vytvoření dočasné soubory se také nezdaří.

Dočasné soubory jsou vytvořeny vždy, když zadáte:

- Soubor odpovědí.

- Vlastní krok sestavení.

- Události sestavení.