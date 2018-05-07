---
title: Události (Linux C++) sestavení vzdálené | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 38c036bf747115823b853d0d66077f4402a7f7ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="build-event-properties-linux-c"></a>Vytvoření vlastnosti události (Linux C++) 

## <a name="pre-build-event"></a>Události před sestavením

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje události před sestavením.
Popis | Určuje popis události před sestavením nástroj k zobrazení.
Použití v sestavení | Určuje, zda je tato událost sestavení vyloučen ze sestavení pro aktuální konfiguraci.
Další soubory pro kopírování | Určuje další soubory zkopírovat do vzdáleného systému. Volitelně lze zadat seznam jako místní k párům vzdálené mapování pomocí syntaxe takto: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kam lze zkopírovat do místního souboru do zadaného umístění vzdáleného do vzdáleného systému.

## <a name="pre-link-event"></a>Událost před propojením

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro nástroj událost před propojením ke spuštění.
Popis | Určuje popis nástroj událost před propojením k zobrazení.
Použití v sestavení | Určuje, zda je tato událost sestavení vyloučen ze sestavení pro aktuální konfiguraci.
Další soubory pro kopírování | Určuje další soubory zkopírovat do vzdáleného systému. Volitelně lze zadat seznam jako místní k párům vzdálené mapování pomocí syntaxe takto: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kam lze zkopírovat do místního souboru do zadaného umístění vzdáleného do vzdáleného systému.

## <a name="post-build-event"></a>Události po sestavení

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje události po sestavení.
Popis | Určuje popis události po sestavení nástroj pro zobrazení.
Použití v sestavení | Určuje, zda je tato událost sestavení vyloučen ze sestavení pro aktuální konfiguraci.
Další soubory pro kopírování | Určuje další soubory zkopírovat do vzdáleného systému. Volitelně lze zadat seznam jako místní k párům vzdálené mapování pomocí syntaxe takto: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kam lze zkopírovat do místního souboru do zadaného umístění vzdáleného do vzdáleného systému.

## <a name="remote-pre-build-event"></a>Vzdálené události před sestavením

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek události před sestavením nástroje ke spuštění ve vzdáleném systému.
Popis | Určuje popis události před sestavením nástroj k zobrazení.
Použití v sestavení | Určuje, zda je tato událost sestavení vyloučen ze sestavení pro aktuální konfiguraci.
Další soubory pro kopírování | Určuje další soubory pro kopírování ze vzdáleného systému. Volitelně lze zadat seznam jako vzdálené k párům místních mapovacích pomocí syntaxe takto: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kam lze zkopírovat ke vzdálenému souboru do zadaného umístění v místním počítači.

## <a name="remote-pre-link-event"></a>Vzdálené událost před propojením

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro nástroj událost před propojením ke spuštění ve vzdáleném systému.
Popis | Určuje popis nástroj událost před propojením k zobrazení.
Použití v sestavení | Určuje, zda je tato událost sestavení vyloučen ze sestavení pro aktuální konfiguraci.
Další soubory pro kopírování | Určuje další soubory pro kopírování ze vzdáleného systému. Volitelně lze zadat seznam jako vzdálené k párům místních mapovacích pomocí syntaxe takto: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kam lze zkopírovat ke vzdálenému souboru do zadaného umístění v místním počítači.

## <a name="remote-post-build-event"></a>Vzdálené události po sestavení

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro nástroj události po sestavení ke spuštění ve vzdáleném systému.
Popis | Určuje popis události po sestavení nástroj pro zobrazení.
Použití v sestavení | Určuje, zda je tato událost sestavení vyloučen ze sestavení pro aktuální konfiguraci.
Další soubory pro kopírování | Určuje další soubory pro kopírování ze vzdáleného systému. Volitelně lze zadat seznam jako vzdálené k párům místních mapovacích pomocí syntaxe takto: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kam lze zkopírovat ke vzdálenému souboru do zadaného umístění v místním počítači.
