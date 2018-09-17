---
title: Kódy ukončení příkazu NMake | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b5a593e38efb5230630ed01e65f4bfb1f2ba92a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722615"
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