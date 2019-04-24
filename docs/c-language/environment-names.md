---
title: Názvy prostředí
ms.date: 11/04/2016
ms.assetid: 9af409a5-e724-465a-9a21-88d3586c2e92
ms.openlocfilehash: 43e1254b4c1ee61a92fbb6499d9396e8b15a3047
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234124"
---
# <a name="environment-names"></a>Názvy prostředí

**ANSI 4.10.4.4** sada názvů prostředí a metoda pro změnu seznamu prostředí používané funkcí [getenv](../c-runtime-library/reference/getenv-wgetenv.md) – funkce

Sada názvů prostředí je neomezená.

Chcete-li změnit proměnné prostředí z programu v jazyce C, zavolejte [_putenv](../c-runtime-library/reference/putenv-wputenv.md) funkce. Chcete-li změnit proměnné prostředí z příkazového řádku v systému Windows, použijte příkaz SET (například SET LIB = D:\LIBS).

Proměnné prostředí nastavené v programu jazyka C existují pouze tak dlouho, dokud je spuštěna jejich kopie příkazového prostředí operačního systému (CMD.EXE nebo COMMAND.COM). Například řádek

```
system( SET LIB = D:\LIBS );
```

spustí kopii příkazového prostředí (CMD.EXE), nastaví proměnnou prostředí LIB, vrátí se do programu jazyka C a ukončí sekundární kopii programu CMD.EXE. Ukončení této kopie programu CMD.EXE odebere dočasnou proměnnou prostředí LIB.

Podobně změny provedené pomocí funkce `_putenv` trvají pouze do ukončení programu.

## <a name="see-also"></a>Viz také:

[Funkce knihovny](../c-language/library-functions.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)
