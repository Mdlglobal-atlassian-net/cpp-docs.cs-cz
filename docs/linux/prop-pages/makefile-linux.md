---
title: Obecné vlastnosti (projektu souboru pravidel C++ pro Linux) | Dokumentace Microsoftu
ms.date: 9/26/2017
ms.assetid: 3dec6853-43f6-412b-9806-9bfad333a204
ms.openlocfilehash: fb742d552d0b70ba5f5c406dd43bdf4cf8d1914b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524589"
---
# <a name="makefile-project-properties-linux-c"></a>Vlastnosti projektu souboru pravidel (Linux C++)

Toto je částečný seznam vlastností dostupných v projektu souboru pravidel pro Linux. Mnoho vlastností projektu souboru pravidel jsou stejné jako vlastnosti projektu aplikace konzoly C++ Linux.

## <a name="general"></a>Obecné

Vlastnost | Popis | Možnosti
--- | ---| ---
Výstupní adresář | Určuje relativní cestu k adresáři výstupního souboru; může obsahovat proměnné prostředí.
Zprostředkující adresář | Určuje relativní cestu k adresáři přechodového souboru; může obsahovat proměnné prostředí.
Soubor protokolu sestavení | Určuje soubor protokolu sestavení pro zápis při protokolování sestavení je povolená.
Typ konfigurace | Určuje typ výstupu generovaného touto konfigurací. | **Dynamická knihovna (.so)** – dynamická knihovna (.so)<br>**Statická knihovna (.a)** – statická knihovna (.a)<br>**Aplikace (.out)** – aplikace (.out)<br>**Soubor pravidel** -souboru pravidel<br>
Vzdálený sestavující počítač | Cílový počítač nebo zařízení pro vzdálené sestavení, nasazení a ladění.
Vzdálený Buildovací kořenový adresář | Určuje cestu k adresáři na vzdáleném počítači či zařízení.
Adresář projektu vzdáleného buildu | Určuje cestu k adresáři na vzdáleném počítači nebo zařízení pro tento projekt.

## <a name="debugging"></a>Ladění

Zobrazit [ladicího programu vlastnosti (Linux C++)](debugging-linux.md)

## <a name="copy-sources"></a>Kopírovat zdroje

Zobrazit [kopírování vlastností projektu (C++ pro Linux) zdrojů](copy-sources-project.md).

## <a name="build-events"></a>Události sestavení

### <a name="pre-build-event"></a>Událost před sestavením

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události před sestavením.
Popis | Určuje popis, který se má zobrazit nástroj události před sestavením.
Použít v sestavení | Určuje, zda je tato událost sestavení vyloučena ze sestavení v aktuální konfiguraci.
Další soubory ke zkopírování | Určuje další soubory ke zkopírování do vzdáleného systému. Volitelně můžete zadat seznamu jako místní dvojice mapování vzdálených touto syntaxí: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kde místní soubor je možné zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému.

### <a name="post-build-event"></a>Událost po sestavení

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek, který má spustit nástroj události po sestavení.
Popis | Určuje popis, který se má zobrazit nástroj události po sestavení.
Použít v sestavení | Určuje, zda je tato událost sestavení vyloučena ze sestavení v aktuální konfiguraci.
Další soubory ke zkopírování | Určuje další soubory ke zkopírování do vzdáleného systému. Volitelně můžete zadat seznamu jako místní dvojice mapování vzdálených touto syntaxí: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kde místní soubor je možné zkopírovat do zadaného vzdáleného umístění ve vzdáleném systému.

### <a name="remote-pre-build-event"></a>Vzdálená událost před sestavením

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro spuštění ve vzdáleném systému nástroje pre-build event.
Popis | Určuje popis, který se má zobrazit nástroj události před sestavením.
Použít v sestavení | Určuje, zda je tato událost sestavení vyloučena ze sestavení v aktuální konfiguraci.
Další soubory ke zkopírování | Určuje další soubory ke zkopírování ze vzdáleného systému. Volitelně lze zadat seznam jako vzdálené místních mapovacích dvojice touto syntaxí: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kde vzdálený soubor je možné zkopírovat do zadaného umístění na místním počítači.

### <a name="remote-post-build-event"></a>Vzdálená událost po sestavení

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro nástroj události po sestavení ke spuštění ve vzdáleném systému.
Popis | Určuje popis, který se má zobrazit nástroj události po sestavení.
Použít v sestavení | Určuje, zda je tato událost sestavení vyloučena ze sestavení v aktuální konfiguraci.
Další soubory ke zkopírování | Určuje další soubory ke zkopírování ze vzdáleného systému. Volitelně lze zadat seznam jako vzdálené místních mapovacích dvojice touto syntaxí: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kde vzdálený soubor je možné zkopírovat do zadaného umístění na místním počítači.

## <a name="cc"></a>C/C++

### <a name="intellisense"></a>IntelliSense

Vlastnosti technologie IntelliSense můžete nastavit na úrovni projektu nebo soubor k poskytování příčiny modul IntelliSense. Neovlivňují kompilace.

Vlastnost | Popis
--- | ---
Zahrnout cestu vyhledávání | Určuje cestu hledání pro zahrnuté soubory řešení.
Vynucené zahrnuje | Určuje soubory, které jsou Vynuceně zahrnuté.
Definice preprocesoru | Určuje direktivy preprocesoru define použité zdrojovými soubory.
Zrušit Definice preprocesoru | Určuje že jeden nebo více nedefinovaných hodnot preprocesoru.     (/U[makro]))
Další možnosti | Určuje další přepínače kompilátoru pro použití technologií IntelliSense při analýze souborů C++.

### <a name="build"></a>Sestavení

Vlastnost | Popis
--- | ---
Sestavení příkazového řádku | Určuje příkazový řádek pro spuštění příkazu "Sestavení".
Opětovné sestavení všech příkazového řádku | Určuje příkazový řádek pro spuštění příkazu "Sestavit vše znovu".
Příkazový řádek příkazu vyčistit | Určuje příkazový řádek pro spuštění příkazu "Clean".

### <a name="remote-build"></a>Vzdálený Buildovací

Vlastnost | Popis
--- | ---
Sestavení příkazového řádku | Určuje příkazový řádek pro spuštění příkazu "Sestavení". Provádí se ve vzdáleném systému.
Opětovné sestavení všech příkazového řádku | Určuje příkazový řádek pro spuštění příkazu "Sestavit vše znovu". Provádí se ve vzdáleném systému.
Příkazový řádek příkazu vyčistit | Určuje příkazový řádek pro spuštění příkazu "Clean". Provádí se ve vzdáleném systému.
Výstupy | Určuje výstupy generované vzdáleným sestavením ve vzdáleném systému.
