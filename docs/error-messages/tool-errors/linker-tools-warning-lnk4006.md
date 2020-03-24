---
title: Upozornění linkerů LNK4006
ms.date: 11/04/2016
f1_keywords:
- LNK4006
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
ms.openlocfilehash: d949ba259de8e131f6191e757119b4c42effc3d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194314"
---
# <a name="linker-tools-warning-lnk4006"></a>Upozornění linkerů LNK4006

symbol už je definovaný v objektu. Druhá definice se ignoruje.

Zadaný `symbol`, zobrazený v jeho upraveném formuláři, byl definován pro násobení. Když se objeví toto upozornění, `symbol` se přidá dvakrát, ale použije se jenom první formulář.

Toto upozornění můžete zobrazit, pokud se pokusíte sloučit dva knihovny importu do jednoho.

Při opětovném sestavování knihovny run-time jazyka C můžete tuto zprávu ignorovat.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Oprava pomocí následujících možných řešení

1. Daný `symbol` může být zabalená funkce vytvořená kompilací s [/Gy](../../build/reference/gy-enable-function-level-linking.md). Tento symbol byl zahrnut ve více než jednom souboru, ale byl změněn mezi kompilacemi. Překompilujte všechny soubory, které obsahují `symbol`.

1. Daná `symbol` mohla být definována jinak ve dvou členských objektech v různých knihovnách.

1. Absolutní hodnota mohla být definována dvakrát s jinou hodnotou v každé definici.

1. Pokud je chybová zpráva přijata při kombinování knihoven, `symbol` již v knihovně, do které se přidávají, existuje.
