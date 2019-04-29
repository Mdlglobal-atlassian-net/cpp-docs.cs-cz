---
title: Vzdálený Buildovací události (Linux C++)
ms.date: 9/26/2017
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 87647948b641fff7370003a59775a5680c176fb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393087"
---
# <a name="build-event-properties-linux-c"></a>Vytvořit událost vlastnosti (Linux C++)

## <a name="pre-build-event"></a>Událost před sestavením

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události před sestavením.
Popis | Určuje popis, který se má zobrazit nástroj události před sestavením.
Použít v sestavení | Určuje, zda je tato událost sestavení vyloučena ze sestavení v aktuální konfiguraci.
Další soubory ke zkopírování | Určuje další soubory ke zkopírování do vzdáleného systému. Volitelně můžete zadat seznamu jako místní dvojice mapování vzdálených touto syntaxí: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kde místní soubor je možné zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému.

## <a name="pre-link-event"></a>Událost před propojením

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události před propojením.
Popis | Určuje popis, který se má zobrazit nástroj události před propojením.
Použít v sestavení | Určuje, zda je tato událost sestavení vyloučena ze sestavení v aktuální konfiguraci.
Další soubory ke zkopírování | Určuje další soubory ke zkopírování do vzdáleného systému. Volitelně můžete zadat seznamu jako místní dvojice mapování vzdálených touto syntaxí: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kde místní soubor je možné zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému.

## <a name="post-build-event"></a>Událost po sestavení

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události po sestavení.
Popis | Určuje popis, který se má zobrazit nástroj události po sestavení.
Použít v sestavení | Určuje, zda je tato událost sestavení vyloučena ze sestavení v aktuální konfiguraci.
Další soubory ke zkopírování | Určuje další soubory ke zkopírování do vzdáleného systému. Volitelně můžete zadat seznamu jako místní dvojice mapování vzdálených touto syntaxí: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kde místní soubor je možné zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému.

## <a name="remote-pre-build-event"></a>Vzdálená událost před sestavením

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro spuštění ve vzdáleném systému nástroje pre-build event.
Popis | Určuje popis, který se má zobrazit nástroj události před sestavením.
Použít v sestavení | Určuje, zda je tato událost sestavení vyloučena ze sestavení v aktuální konfiguraci.
Další soubory ke zkopírování | Určuje další soubory ke zkopírování ze vzdáleného systému. Volitelně lze zadat seznam jako vzdálené místních mapovacích dvojice touto syntaxí: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kde vzdálený soubor je možné zkopírovat do zadaného umístění na místním počítači.

## <a name="remote-pre-link-event"></a>Vzdálená událost před propojením

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro nástroj události před propojením ke spuštění ve vzdáleném systému.
Popis | Určuje popis, který se má zobrazit nástroj události před propojením.
Použít v sestavení | Určuje, zda je tato událost sestavení vyloučena ze sestavení v aktuální konfiguraci.
Další soubory ke zkopírování | Určuje další soubory ke zkopírování ze vzdáleného systému. Volitelně lze zadat seznam jako vzdálené místních mapovacích dvojice touto syntaxí: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kde vzdálený soubor je možné zkopírovat do zadaného umístění na místním počítači.

## <a name="remote-post-build-event"></a>Vzdálená událost po sestavení

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro nástroj události po sestavení ke spuštění ve vzdáleném systému.
Popis | Určuje popis, který se má zobrazit nástroj události po sestavení.
Použít v sestavení | Určuje, zda je tato událost sestavení vyloučena ze sestavení v aktuální konfiguraci.
Další soubory ke zkopírování | Určuje další soubory ke zkopírování ze vzdáleného systému. Volitelně lze zadat seznam jako vzdálené místních mapovacích dvojice touto syntaxí: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kde vzdálený soubor je možné zkopírovat do zadaného umístění na místním počítači.
