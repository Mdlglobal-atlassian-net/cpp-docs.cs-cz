---
title: Tools.ini a příkaz NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
ms.openlocfilehash: c50fef5d2fd36b8fb9327cad25bc5b2ab4ba61e2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419880"
---
# <a name="toolsini-and-nmake"></a>Tools.ini a příkaz NMAKE

NMAKE přečte Tools.ini předtím, než se načte soubory pravidel, pokud se nepoužije/r. Hledá Tools.ini nejprve v aktuálním adresáři a potom do adresáře určené proměnnou prostředí INIT. V části Nastavení NMAKE v souboru inicializace začíná `[NMAKE]` a může obsahovat jakékoli informace o souboru pravidel. Zadejte komentář na samostatný řádek začínající znakem čísla (#).

## <a name="see-also"></a>Viz také:

[Spuštění příkazu NMAKE](../build/running-nmake.md)
