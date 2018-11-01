---
title: Import vazeb
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
ms.openlocfilehash: 6ee9d9cc180e77d817b7b52baa1a6eb5209a8365
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486343"
---
# <a name="binding-imports"></a>Import vazeb

Výchozí chování linkeru je vytvoření tabulky s možností vazby importních adres pro knihovny DLL načtené se zpožděním. Pokud je vázán knihovnu DLL, pomocná funkce se pokusí použít vázané informace namísto volání metody **GetProcAddress** ve všech odkazovaných importy. Pokud časové razítko nebo upřednostňovanou adresu neodpovídají těm načtené knihovny DLL, bude předpokládat pomocnou funkci tabulky vázané importních adres je zastaralá a bude pokračovat, protože pokud neexistuje.

Pokud chcete nikdy svázat importy knihovny DLL s odloženým načtením, určení [/delay](../../build/reference/delay-delay-load-import-settings.md): nobind příkazového řádku linkeru zabráníte tabulky vázané importních adres generované a využívání místa v souboru bitové kopie.

## <a name="see-also"></a>Viz také

[Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)