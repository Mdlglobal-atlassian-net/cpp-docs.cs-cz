---
title: Tools.ini a příkaz NMAKE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84406886c9aa0c0053ed7c183912bf8a7f1f4771
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723577"
---
# <a name="toolsini-and-nmake"></a>Tools.ini a příkaz NMAKE

NMAKE přečte Tools.ini předtím, než se načte soubory pravidel, pokud se nepoužije/r. Hledá Tools.ini nejprve v aktuálním adresáři a potom do adresáře určené proměnnou prostředí INIT. V části Nastavení NMAKE v souboru inicializace začíná `[NMAKE]` a může obsahovat jakékoli informace o souboru pravidel. Zadejte komentář na samostatný řádek začínající znakem čísla (#).

## <a name="see-also"></a>Viz také

[Spuštění příkazu NMAKE](../build/running-nmake.md)