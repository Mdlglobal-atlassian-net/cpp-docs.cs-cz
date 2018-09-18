---
title: Chyba sestavení projektu PRJ0006 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0006
dev_langs:
- C++
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 264b2f90a2d778b1545117ce5c3b1272626ebad6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073249"
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