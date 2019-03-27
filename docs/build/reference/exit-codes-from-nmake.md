---
title: Kódy ukončení příkazu NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
ms.openlocfilehash: 25ea4060e7b7a968b6a9da78f344e645c5d43a44
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822994"
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

## <a name="see-also"></a>Viz také:

[Spuštění příkazu NMAKE](running-nmake.md)