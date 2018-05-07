---
title: Obecné vlastnosti (Linux C++ projektem souboru pravidel) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 3dec6853-43f6-412b-9806-9bfad333a204
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: c0e0422859bc4053ea1e8fff424ff79c3b22f8b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="makefile-project-properties-linux-c"></a>Vlastnosti projektu souboru pravidel (Linux C++)

Toto je částečný seznam vlastností dostupných v projektu souboru pravidel Linux. Mnoho vlastností projektu souboru pravidel jsou shodné s vlastností projektu konzolové aplikace C++ Linux.

## <a name="general"></a>Obecné

Vlastnost | Popis | Možnosti
--- | ---| ---
Výstupní adresář | Určuje relativní cestu do výstupního adresáře. soubor; může obsahovat proměnné prostředí.
Zprostředkující adresáře | Určuje relativní cestu k adresáři pomocný soubor; může obsahovat proměnné prostředí.
Vytvoření souboru protokolu | Určuje soubor protokolu sestavení pro zápis, když sestavení protokolování je povolena.
Typ konfigurace | Určuje typ výstupu, který generuje tuto konfiguraci. | **Dynamické knihovny (.so)** -dynamické knihovny (.so)<br>**Statické knihovny (.a)** – statické knihovny (.a)<br>**Aplikace (.out)** -aplikace (.out)<br>**Makefile** -souboru pravidel<br>
Počítač vzdáleného sestavení | Cílový počítač nebo zařízení, které chcete použít pro vzdálené sestavení, nasazení a ladění.
Vzdálené sestavení kořenového adresáře | Určuje cestu k adresáři na vzdáleném počítači nebo zařízení.
Adresáři vzdáleného sestavení projektu | Určuje cestu k adresáři na vzdáleném počítači nebo zařízení pro projekt.

## <a name="debugging"></a>Ladění

V tématu [ladicího programu vlastnosti (Linux C++)](debugging-linux.md)

## <a name="copy-sources"></a>Kopírovat zdroje

V tématu [kopírovat zdroje vlastnosti projektu (Linux C++)](copy-sources-project.md).

## <a name="build-events"></a>Události sestavení

### <a name="pre-build-event"></a>Události před sestavením

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje události před sestavením.
Popis | Určuje popis události před sestavením nástroj k zobrazení.
Použití v sestavení | Určuje, zda je tato událost sestavení vyloučen ze sestavení pro aktuální konfiguraci.
Další soubory pro kopírování | Určuje další soubory zkopírovat do vzdáleného systému. Volitelně lze zadat seznam jako místní k párům vzdálené mapování pomocí syntaxe takto: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kam lze zkopírovat do místního souboru do zadaného umístění vzdáleného do vzdáleného systému.

### <a name="post-build-event"></a>Události po sestavení

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro spuštění nástroje události po sestavení.
Popis | Určuje popis události po sestavení nástroj pro zobrazení.
Použití v sestavení | Určuje, zda je tato událost sestavení vyloučen ze sestavení pro aktuální konfiguraci.
Další soubory pro kopírování | Určuje další soubory zkopírovat do vzdáleného systému. Volitelně lze zadat seznam jako místní k párům vzdálené mapování pomocí syntaxe takto: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, kam lze zkopírovat do místního souboru do zadaného umístění vzdáleného do vzdáleného systému.

### <a name="remote-pre-build-event"></a>Vzdálené události před sestavením

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek události před sestavením nástroje ke spuštění ve vzdáleném systému.
Popis | Určuje popis události před sestavením nástroj k zobrazení.
Použití v sestavení | Určuje, zda je tato událost sestavení vyloučen ze sestavení pro aktuální konfiguraci.
Další soubory pro kopírování | Určuje další soubory pro kopírování ze vzdáleného systému. Volitelně lze zadat seznam jako vzdálené k párům místních mapovacích pomocí syntaxe takto: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kam lze zkopírovat ke vzdálenému souboru do zadaného umístění v místním počítači.

### <a name="remote-post-build-event"></a>Vzdálené události po sestavení

Vlastnost | Popis
--- | ---
Příkazový řádek | Určuje příkazový řádek pro nástroj události po sestavení ke spuštění ve vzdáleném systému.
Popis | Určuje popis události po sestavení nástroj pro zobrazení.
Použití v sestavení | Určuje, zda je tato událost sestavení vyloučen ze sestavení pro aktuální konfiguraci.
Další soubory pro kopírování | Určuje další soubory pro kopírování ze vzdáleného systému. Volitelně lze zadat seznam jako vzdálené k párům místních mapovacích pomocí syntaxe takto: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, kam lze zkopírovat ke vzdálenému souboru do zadaného umístění v místním počítači.

## <a name="cc"></a>C/C++

### <a name="intellisense"></a>IntelliSense

IntelliSense vlastnosti lze nastavit na úrovni projektu nebo soubor následuje k modulu IntelliSense. Neovlivňují kompilace.

Vlastnost | Popis
--- | ---
Zahrnout cesty pro hledání | Určuje cestu zahrnutí vyhledávání pro vyřešení zahrnuté soubory.
Vynutit zahrnuje | Určuje soubory, které jsou vynucené zahrnuty.
Definice preprocesoru | Určuje, že preprocesor definuje používané ve zdrojové soubory.
Nedefinované Definice preprocesoru | Určuje, že jeden nebo více preprocesor undefines.     (/U[macro])
Další možnosti | Určuje dalších přepínačů, který se má použít technologii Intellisense, při analýze souborů C++.

### <a name="build"></a>Sestavení

Vlastnost | Popis
--- | ---
Sestavení příkazového řádku | Určuje příkazový řádek spustit pro příkaz 'Sestavení'.
Znovu vytvořit všechny příkazového řádku | Určuje příkazový řádek spustit pro příkaz 'Znovu vytvořit všechny'.
Vyčištění příkazového řádku | Určuje příkazový řádek spustit pro příkaz 'Vyčistit'.

### <a name="remote-build"></a>Vzdálené sestavení

Vlastnost | Popis
--- | ---
Sestavení příkazového řádku | Určuje příkazový řádek spustit pro příkaz 'Sestavení'. Je to provést ve vzdáleném systému.
Znovu vytvořit všechny příkazového řádku | Určuje příkazový řádek spustit pro příkaz 'Znovu vytvořit všechny'. Je to provést ve vzdáleném systému.
Vyčištění příkazového řádku | Určuje příkazový řádek spustit pro příkaz 'Vyčistit'. Je to provést ve vzdáleném systému.
Výstupy | Určuje výstupy generované vzdálené sestavení do vzdáleného systému.
