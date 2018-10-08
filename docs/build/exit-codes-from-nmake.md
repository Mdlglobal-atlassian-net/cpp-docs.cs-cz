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
ms.openlocfilehash: 1c70c76292b62560b1d9895aca2851b4cf56802b
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861795"
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