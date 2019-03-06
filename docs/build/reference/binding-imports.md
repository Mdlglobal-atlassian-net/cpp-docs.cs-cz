---
title: Import vazeb
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
ms.openlocfilehash: 90af3af7e71928b18c77c0d21ff6a30c4561e251
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415237"
---
# <a name="binding-imports"></a>Import vazeb

Výchozí chování linkeru je vytvoření tabulky s možností vazby importních adres pro knihovny DLL načtené se zpožděním. Pokud je vázán knihovnu DLL, pomocná funkce se pokusí použít vázané informace namísto volání metody **GetProcAddress** ve všech odkazovaných importy. Pokud časové razítko nebo upřednostňovanou adresu neodpovídají těm načtené knihovny DLL, bude předpokládat pomocnou funkci tabulky vázané importních adres je zastaralá a bude pokračovat, protože pokud neexistuje.

Pokud chcete nikdy svázat importy knihovny DLL s odloženým načtením, určení [/delay](../../build/reference/delay-delay-load-import-settings.md): nobind příkazového řádku linkeru zabráníte tabulky vázané importních adres generované a využívání místa v souboru bitové kopie.

## <a name="see-also"></a>Viz také:

[Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)
