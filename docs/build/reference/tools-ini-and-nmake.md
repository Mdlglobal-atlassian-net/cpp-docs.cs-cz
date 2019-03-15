---
title: Tools.ini a příkaz NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
ms.openlocfilehash: 38eebb3aaf07438da85b0cfe6bd3f26fb5d6db29
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823092"
---
# <a name="toolsini-and-nmake"></a>Tools.ini a příkaz NMAKE

NMAKE přečte Tools.ini předtím, než se načte soubory pravidel, pokud se nepoužije/r. Hledá Tools.ini nejprve v aktuálním adresáři a potom do adresáře určené proměnnou prostředí INIT. V části Nastavení NMAKE v souboru inicializace začíná `[NMAKE]` a může obsahovat jakékoli informace o souboru pravidel. Zadejte komentář na samostatný řádek začínající znakem čísla (#).

## <a name="see-also"></a>Viz také:

[Spuštění příkazu NMAKE](running-nmake.md)
