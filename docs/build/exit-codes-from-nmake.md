---
title: Kódy ukončení příkazu NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
ms.openlocfilehash: 08aceadf107112b446844b09fad24a11fbe7a731
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499590"
---
# <a name="exit-codes-from-nmake"></a>Kódy ukončení příkazu NMAKE

NMAKE vrátí následující kódy ukončení:

|Kód|Význam|
|----------|-------------|
|0|Žádná chybová zpráva (pravděpodobně upozornění)|
|1|Neúplné sestavení (vydané, pouze pokud je použit /K)|
|2|Chyba programu, pravděpodobně kvůli jednomu z následujících akcí:|
||-Chyba syntaxe v souboru pravidel|
||– Chyba nebo ukončovací kód z příkazu|
||-Přerušení uživatelem.|
|4|Systémová chyba – nedostatek paměti|
|255|Cíl není aktuální (vydané, pouze pokud je použit /Q)|

## <a name="see-also"></a>Viz také

[Spuštění příkazu NMAKE](../build/running-nmake.md)