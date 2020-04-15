---
title: Obecné vlastnosti (linuxový projekt Makefile) Dokumenty společnosti Microsoft
ms.date: 06/07/2019
ms.assetid: 3dec6853-43f6-412b-9806-9bfad333a204
ms.openlocfilehash: 72a7919bc94be80acdbf7a2cef5b4a9875595545
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "79446147"
---
# <a name="makefile-project-properties-linux-c"></a>Vlastnosti projektu Makefile (Linux C++)

::: moniker range="vs-2015"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range=">=vs-2017"

Toto je částečný seznam vlastností dostupných v projektu Linux Makefile. Mnoho vlastností projektu Makefile je shodné s vlastnostmi projektu linuxové konzoly C++.

## <a name="general"></a>Obecné

| Vlastnost | Popis | Choices |
|--|--|--|
| Výstupní adresář | Určuje relativní cestu k adresáři výstupního souboru. mohou zahrnovat proměnné prostředí. |
| Zprostředkující adresář | Určuje relativní cestu k zprostředkujícímu adresáři souborů. mohou zahrnovat proměnné prostředí. |
| Soubor protokolu sestavení | Určuje soubor protokolu sestavení, do který se má zapisovat, když je povoleno protokolování sestavení. |
| Typ konfigurace | Určuje typ výstupu, který tato konfigurace generuje. | **Dynamická knihovna (.so)** - Dynamická knihovna (.so)<br>**Statická knihovna (.a)** - Statická knihovna (.a)<br>**Aplikace (.out)** - Aplikace (.out)<br>**Makefile** - Makefile<br> |
| Vzdálený stroj sestavení | Cílový počítač nebo zařízení, které se má použít pro vzdálené sestavení, nasazení a ladění. |
| Kořenový adresář vzdáleného sestavení | Určuje cestu k adresáři ve vzdáleném počítači nebo zařízení. |
| Vzdálený adresář projektu sestavení | Určuje cestu k adresáři ve vzdáleném počítači nebo zařízení projektu. |

## <a name="debugging"></a>Ladění

Viz [Vlastnosti ladicího programu (Linux C++)](debugging-linux.md)

## <a name="copy-sources"></a>Kopírovat zdroje

Viz [Kopírování zdrojů vlastností projektu (Linux C++)](copy-sources-project.md).

## <a name="build-events"></a>Události sestavení

### <a name="pre-build-event"></a>Událost předběžného sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje událostí před sestavením. |
| Popis | Určuje popis nástroje pro událost před sestavením, který se má zobrazit. |
| Použití v sestavení | Určuje, zda je tato událost sestavení vyloučena z sestavení pro aktuální konfiguraci. |
| Další soubory ke kopírování | Určuje další soubory, které mají být zkopírovány do vzdáleného systému. Volitelně může být seznam poskytnut jako místní dvojice vzdálenémapování pomocí syntaxe, jako je tato: fulllocalpath1;fullremotepath1;fulllocalpath2:=fullremotepath2, kde lze místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému. |

### <a name="post-build-event"></a>Událost po sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje události po sestavení. |
| Popis | Určuje popis nástroje události po sestavení, který se má zobrazit. |
| Použití v sestavení | Určuje, zda je tato událost sestavení vyloučena z sestavení pro aktuální konfiguraci. |
| Další soubory ke kopírování | Určuje další soubory, které mají být zkopírovány do vzdáleného systému. Volitelně může být seznam poskytnut jako místní dvojice vzdálenémapování pomocí syntaxe, jako je tato: fulllocalpath1;fullremotepath1;fulllocalpath2:=fullremotepath2, kde lze místní soubor zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému. |

### <a name="remote-pre-build-event"></a>Vzdálená událost předběžného sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje událostí před sestavením ve vzdáleném systému. |
| Popis | Určuje popis nástroje pro událost před sestavením, který se má zobrazit. |
| Použití v sestavení | Určuje, zda je tato událost sestavení vyloučena z sestavení pro aktuální konfiguraci. |
| Další soubory ke kopírování | Určuje další soubory, které mají být kopírovány ze vzdáleného systému. Volitelně může být seznam poskytnut jako vzdálený místním párům mapování pomocí syntaxe, jako je tato: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, kde lze vzdálený soubor zkopírovat do zadaného umístění v místním počítači. |

### <a name="remote-post-build-event"></a>Vzdálená událost po sestavení

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje událostí po sestavení ve vzdáleném systému. |
| Popis | Určuje popis nástroje události po sestavení, který se má zobrazit. |
| Použití v sestavení | Určuje, zda je tato událost sestavení vyloučena z sestavení pro aktuální konfiguraci. |
| Další soubory ke kopírování | Určuje další soubory, které mají být kopírovány ze vzdáleného systému. Volitelně může být seznam poskytnut jako vzdálený místním párům mapování pomocí syntaxe, jako je tato: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, kde lze vzdálený soubor zkopírovat do zadaného umístění v místním počítači. |

## <a name="cc"></a>C/C++

### <a name="intellisense"></a>IntelliSense

Vlastnosti IntelliSense lze nastavit na úrovni projektu nebo souboru a poskytnout tak vodítka k modulu IntelliSense. Nemají vliv na kompilaci.

| Vlastnost | Popis |
|--|--|
| Zahrnout cestu hledání | Určuje cestu hledání zahrnutí pro řešení zahrnutých souborů. |
| Vynucené zahrnutí | Určuje soubory, které jsou vynuceně zahrnuty. |
| Definice preprocesoru | Určuje preprocesor, který používá zdrojové soubory. |
| Nedefinovat definice preprocesoru | Určuje jeden nebo více nedefinuje jeden nebo více předprocesorových nedefinuje.     (/U[makro]) |
| Další možnosti | Určuje další přepínače kompilátoru, které má technologie IntelliSense používat při analýzách souborů jazyka C++. |

### <a name="build"></a>Sestavení

| Vlastnost | Popis |
|--|--|
| Sestavení příkazového řádku | Určuje příkazový řádek, který má být spuštěn pro příkaz Sestavit. |
| Znovu vytvořit všechny příkazové řádek | Určuje příkazový řádek, který má být spuštěn pro příkaz Znovu sestavit vše. |
| Čistý příkazový řádek | Určuje příkazový řádek, který má být spuštěn pro příkaz Vyčistit. |

### <a name="remote-build"></a>Vzdálené sestavení

| Vlastnost | Popis |
|--|--|
| Sestavení příkazového řádku | Určuje příkazový řádek, který má být spuštěn pro příkaz Sestavit. To se provádí ve vzdáleném systému. |
| Znovu vytvořit všechny příkazové řádek | Určuje příkazový řádek, který má být spuštěn pro příkaz Znovu sestavit vše. To se provádí ve vzdáleném systému. |
| Čistý příkazový řádek | Určuje příkazový řádek, který má být spuštěn pro příkaz Vyčistit. To se provádí ve vzdáleném systému. |
| Výstupy | Určuje výstupy generované vzdáleným sestavením vzdáleného systému. |

::: moniker-end
