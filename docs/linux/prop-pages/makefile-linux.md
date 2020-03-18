---
title: Obecné vlastnosti (projekt C++ makefile pro Linux) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 3dec6853-43f6-412b-9806-9bfad333a204
ms.openlocfilehash: 72a7919bc94be80acdbf7a2cef5b4a9875595545
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446147"
---
# <a name="makefile-project-properties-linux-c"></a>Vlastnosti projektu makefile (Linux C++)

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

Toto je částečný seznam vlastností, které jsou k dispozici v projektu souboru pravidel pro Linux. Mnoho vlastností projektu makefile je stejné jako vlastnosti projektu C++ konzolové aplikace pro Linux.

## <a name="general"></a>Obecné

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Výstupní adresář | Určuje relativní cestu k adresáři výstupního souboru. může obsahovat proměnné prostředí. |
| Zprostředkující adresář | Určuje relativní cestu k adresáři zprostředkujícího souboru. může obsahovat proměnné prostředí. |
| Soubor protokolu sestavení | Určuje soubor protokolu sestavení, do kterého se má zapisovat, pokud je povolené protokolování sestavení. |
| Typ konfigurace | Určuje typ výstupu, který tato konfigurace generuje. | **Dynamická knihovna (. so)** – dynamická knihovna (. so)<br>**Statická knihovna (. a)** – statická knihovna (. a)<br>**Aplikace (. out)** – aplikace (. out)<br>**Makefile** -makefile<br> |
| Vzdálený sestavovací počítač | Cílový počítač nebo zařízení, které se má použít pro vzdálené sestavení, nasazení a ladění. |
| Kořenový adresář vzdáleného buildu | Určuje cestu k adresáři na vzdáleném počítači nebo zařízení. |
| Adresář vzdáleného projektu sestavení | Určuje cestu k adresáři na vzdáleném počítači nebo zařízení pro daný projekt. |

## <a name="debugging"></a>Ladění

Viz [vlastnosti ladicího programu C++(Linux)](debugging-linux.md)

## <a name="copy-sources"></a>Kopírovat zdroje

Viz [Vlastnosti projektu kopírování zdrojů (Linux C++)](copy-sources-project.md).

## <a name="build-events"></a>Události sestavení

### <a name="pre-build-event"></a>Událost před sestavením

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události před sestavením. |
| Popis | Určuje popis, který má zobrazit nástroj události před sestavením. |
| Použít v buildu | Určuje, zda je tato událost sestavení vyloučena ze sestavení pro aktuální konfiguraci. |
| Další soubory ke zkopírování | Určuje další soubory ke zkopírování do vzdáleného systému. Volitelně lze seznam zadat jako místní pro páry vzdáleného mapování pomocí syntaxe, jako je tato: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kde lze místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému. |

### <a name="post-build-event"></a>Událost po sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události po sestavení. |
| Popis | Určuje popis pro zobrazení nástroje po sestavení události. |
| Použít v buildu | Určuje, zda je tato událost sestavení vyloučena ze sestavení pro aktuální konfiguraci. |
| Další soubory ke zkopírování | Určuje další soubory ke zkopírování do vzdáleného systému. Volitelně lze seznam zadat jako místní pro páry vzdáleného mapování pomocí syntaxe, jako je tato: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kde lze místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému. |

### <a name="remote-pre-build-event"></a>Vzdálená událost před sestavením

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události před sestavením ve vzdáleném systému. |
| Popis | Určuje popis, který má zobrazit nástroj události před sestavením. |
| Použít v buildu | Určuje, zda je tato událost sestavení vyloučena ze sestavení pro aktuální konfiguraci. |
| Další soubory ke zkopírování | Určuje další soubory ke zkopírování ze vzdáleného systému. Volitelně může být seznam poskytnutý jako dvojice mapování vzdálených na místní, a to pomocí syntaxe takto: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kde se dá vzdálený soubor zkopírovat do zadaného umístění v místním počítači. |

### <a name="remote-post-build-event"></a>Vzdálená událost po sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události po sestavení ve vzdáleném systému. |
| Popis | Určuje popis pro zobrazení nástroje po sestavení události. |
| Použít v buildu | Určuje, zda je tato událost sestavení vyloučena ze sestavení pro aktuální konfiguraci. |
| Další soubory ke zkopírování | Určuje další soubory ke zkopírování ze vzdáleného systému. Volitelně může být seznam poskytnutý jako dvojice mapování vzdálených na místní, a to pomocí syntaxe takto: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kde se dá vzdálený soubor zkopírovat do zadaného umístění v místním počítači. |

## <a name="cc"></a>C/C++

### <a name="intellisense"></a>IntelliSense

Vlastnosti technologie IntelliSense lze nastavit na úrovni projektu nebo souboru, aby poskytovaly modul IntelliSense. Neovlivňují kompilaci.

| Vlastnost | Popis |
|--|--|
| Cesta pro hledání vložených součástí | Určuje cestu pro vyhledávání vložených souborů pro řešení zahrnutých souborů. |
| Vynucené zahrnutí | Určuje soubory, které jsou vynuceně zahrnuté. |
| Definice preprocesoru | Určuje Definice preprocesoru používané zdrojovými soubory. |
| Zrušit Definice preprocesoru | Určuje jeden nebo více zrušení definujících preprocesoru.     (/U [makro]) |
| Další možnosti | Určuje další přepínače kompilátoru pro použití technologií IntelliSense při analýze C++ souborů. |

### <a name="build"></a>Sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek sestavení | Určuje příkazový řádek, který se má spustit pro příkaz Build. |
| Sestavit vše znovu z příkazového řádku | Určuje příkazový řádek pro spuštění příkazu znovu sestavit vše. |
| Příkazový řádek vyčištění | Určuje příkazový řádek pro spuštění příkazu vyčistit. |

### <a name="remote-build"></a>Vzdálené sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek sestavení | Určuje příkazový řádek, který se má spustit pro příkaz Build. Tato rutina se spouští ve vzdáleném systému. |
| Sestavit vše znovu z příkazového řádku | Určuje příkazový řádek pro spuštění příkazu znovu sestavit vše. Tato rutina se spouští ve vzdáleném systému. |
| Příkazový řádek vyčištění | Určuje příkazový řádek pro spuštění příkazu vyčistit. Tato rutina se spouští ve vzdáleném systému. |
| Výstupy | Určuje výstupy generované vzdáleným sestavením ve vzdáleném systému. |

::: moniker-end
