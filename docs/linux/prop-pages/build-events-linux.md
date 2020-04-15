---
title: Události vzdáleného sestavení (Linux C++)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 4a3e9019d4dacc3d494feb5d6de8f5c2247e4d12
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "79441508"
---
# <a name="build-event-properties-linux-c"></a>Vytváření vlastností událostí (Linux C++)

::: moniker range="vs-2015"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="pre-build-event"></a>Událost předběžného sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje událostí před sestavením. |
| Popis | Určuje popis nástroje pro událost před sestavením, který se má zobrazit. |
| Použití v sestavení | Určuje, zda je tato událost sestavení vyloučena z sestavení pro aktuální konfiguraci. |
| Další soubory ke kopírování | Určuje další soubory, které mají být zkopírovány do vzdáleného systému. Volitelně zadejte místní dvojice mapování vzdáleného mapování pomocí syntaxe, jako je tato: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, kde lze místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému. |

## <a name="pre-link-event"></a>Událost před propojením

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje události před propojením. |
| Popis | Určuje popis nástroje pro události před propojením, který se má zobrazit. |
| Použití v sestavení | Určuje, zda je tato událost sestavení vyloučena z sestavení pro aktuální konfiguraci. |
| Další soubory ke kopírování | Určuje další soubory, které mají být zkopírovány do vzdáleného systému. Volitelně zadejte místní dvojice mapování vzdáleného mapování pomocí syntaxe, jako je tato: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, kde lze místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému. |

## <a name="post-build-event"></a>Událost po sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje události po sestavení. |
| Popis | Určuje popis nástroje události po sestavení, který se má zobrazit. |
| Použití v sestavení | Určuje, zda je tato událost sestavení vyloučena z sestavení pro aktuální konfiguraci. |
| Další soubory ke kopírování | Určuje další soubory, které mají být zkopírovány do vzdáleného systému. Volitelně zadejte místní dvojice mapování vzdáleného mapování pomocí syntaxe, jako je tato: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, kde lze místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému. |

## <a name="remote-pre-build-event"></a>Vzdálená událost předběžného sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje událostí před sestavením ve vzdáleném systému. |
| Popis | Určuje popis nástroje pro událost před sestavením, který se má zobrazit. |
| Použití v sestavení | Určuje, zda je tato událost sestavení vyloučena z sestavení pro aktuální konfiguraci. |
| Další soubory ke kopírování | Určuje další soubory, které mají být kopírovány ze vzdáleného systému. Volitelně zadejte vzdálené na místní dvojice mapování pomocí syntaxe, jako je tato: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, kde lze vzdálený soubor zkopírovat do zadaného umístění v místním počítači. |

## <a name="remote-pre-link-event"></a>Vzdálená událost předběžného propojení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje událostí před propojením ve vzdáleném systému. |
| Popis | Určuje popis nástroje pro události před propojením, který se má zobrazit. |
| Použití v sestavení | Určuje, zda je tato událost sestavení vyloučena z sestavení pro aktuální konfiguraci. |
| Další soubory ke kopírování | Určuje další soubory, které mají být kopírovány ze vzdáleného systému. Volitelně zadejte vzdálené na místní dvojice mapování pomocí syntaxe, jako je tato: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, kde lze vzdálený soubor zkopírovat do zadaného umístění v místním počítači. |

## <a name="remote-post-build-event"></a>Vzdálená událost po sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje událostí po sestavení ve vzdáleném systému. |
| Popis | Určuje popis nástroje události po sestavení, který se má zobrazit. |
| Použití v sestavení | Určuje, zda je tato událost sestavení vyloučena z sestavení pro aktuální konfiguraci. |
| Další soubory ke kopírování | Určuje další soubory, které mají být kopírovány ze vzdáleného systému. Volitelně zadejte vzdálené na místní dvojice mapování pomocí syntaxe, jako je tato: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, kde lze vzdálený soubor zkopírovat do zadaného umístění v místním počítači. |

::: moniker-end
