---
title: Události vzdáleného sestavení (Linux C++)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 4a3e9019d4dacc3d494feb5d6de8f5c2247e4d12
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441508"
---
# <a name="build-event-properties-linux-c"></a>Vlastnosti události sestavení (Linux C++)

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="pre-build-event"></a>Událost před sestavením

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události před sestavením. |
| Popis | Určuje popis, který má zobrazit nástroj události před sestavením. |
| Použít v buildu | Určuje, zda je tato událost sestavení vyloučena ze sestavení pro aktuální konfiguraci. |
| Další soubory ke zkopírování | Určuje další soubory ke zkopírování do vzdáleného systému. Volitelně můžete zadat místní a vzdálené páry mapování pomocí syntaxe takto: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kde se dá místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému. |

## <a name="pre-link-event"></a>Událost před propojením

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události před propojením. |
| Popis | Určuje popis, který má zobrazit nástroj události před propojením. |
| Použít v buildu | Určuje, zda je tato událost sestavení vyloučena ze sestavení pro aktuální konfiguraci. |
| Další soubory ke zkopírování | Určuje další soubory ke zkopírování do vzdáleného systému. Volitelně můžete zadat místní a vzdálené páry mapování pomocí syntaxe takto: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kde se dá místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému. |

## <a name="post-build-event"></a>Událost po sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události po sestavení. |
| Popis | Určuje popis pro zobrazení nástroje po sestavení události. |
| Použít v buildu | Určuje, zda je tato událost sestavení vyloučena ze sestavení pro aktuální konfiguraci. |
| Další soubory ke zkopírování | Určuje další soubory ke zkopírování do vzdáleného systému. Volitelně můžete zadat místní a vzdálené páry mapování pomocí syntaxe takto: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kde se dá místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému. |

## <a name="remote-pre-build-event"></a>Vzdálená událost před sestavením

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události před sestavením ve vzdáleném systému. |
| Popis | Určuje popis, který má zobrazit nástroj události před sestavením. |
| Použít v buildu | Určuje, zda je tato událost sestavení vyloučena ze sestavení pro aktuální konfiguraci. |
| Další soubory ke zkopírování | Určuje další soubory ke zkopírování ze vzdáleného systému. Volitelně můžete zadat páry mapování Remote to local pomocí syntaxe takto: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kde se dá vzdálený soubor zkopírovat do zadaného umístění v místním počítači. |

## <a name="remote-pre-link-event"></a>Vzdálená událost před propojením

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události před propojením ve vzdáleném systému. |
| Popis | Určuje popis, který má zobrazit nástroj události před propojením. |
| Použít v buildu | Určuje, zda je tato událost sestavení vyloučena ze sestavení pro aktuální konfiguraci. |
| Další soubory ke zkopírování | Určuje další soubory ke zkopírování ze vzdáleného systému. Volitelně můžete zadat páry mapování Remote to local pomocí syntaxe takto: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kde se dá vzdálený soubor zkopírovat do zadaného umístění v místním počítači. |

## <a name="remote-post-build-event"></a>Vzdálená událost po sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události po sestavení ve vzdáleném systému. |
| Popis | Určuje popis pro zobrazení nástroje po sestavení události. |
| Použít v buildu | Určuje, zda je tato událost sestavení vyloučena ze sestavení pro aktuální konfiguraci. |
| Další soubory ke zkopírování | Určuje další soubory ke zkopírování ze vzdáleného systému. Volitelně můžete zadat páry mapování Remote to local pomocí syntaxe takto: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kde se dá vzdálený soubor zkopírovat do zadaného umístění v místním počítači. |

::: moniker-end
