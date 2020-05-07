---
title: pgosweep
ms.date: 03/14/2018
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
ms.openlocfilehash: 3ba31671fc3794e1cc959d86d914ba1eef2e01e4
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341186"
---
# <a name="pgosweep"></a>pgosweep

Používá se v optimalizaci na základě profilu k zápisu všech dat profilu z běžícího programu do souboru. pgc.

## <a name="syntax"></a>Syntaxe

> **pgosweep** [*Možnosti*] *Obrázek* *pgcfile*

### <a name="parameters"></a>Parametry

*nastavení*<br/>
Volitelné Platné hodnoty pro *Možnosti* jsou:

- **/?** nebo **/help** zobrazí zprávu help.

- **/NORESET** zachovává počet v datových strukturách modulu runtime.

*obrazu*<br/>
Úplná cesta k souboru. exe nebo. dll, který byl vytvořen pomocí možnosti [/GENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)nebo [/LTCG: PGINSTRUMENT](reference/ltcg-link-time-code-generation.md) .

*pgcfile*<br/>
Soubor. pgc, kde tento příkaz zapisuje počty dat.

## <a name="remarks"></a>Poznámky

Příkaz **pgosweep** funguje na programech, které byly vytvořeny pomocí možnosti [/GENPROFILE nebo/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) , nebo zastaralé možnosti [/LTCG: PGINSTRUMENT](reference/ltcg-link-time-code-generation.md) . Přerušuje běžící program a zapíše data profilu do nového souboru. pgc. Ve výchozím nastavení příkaz obnoví počty po každé operaci zápisu. Pokud zadáte možnost **/NORESET** , příkaz zaznamená hodnoty, ale neobnoví je v běžícím programu. Tato možnost poskytuje duplicitní data při pozdějším načtení dat profilu.

Alternativním použitím **pgosweep** je načtení informací o profilu jenom pro normální fungování aplikace. Můžete například spustit **pgosweep** krátce po spuštění aplikace a zahodit tento soubor. Tím se odeberou data profilu spojená s náklady na spuštění. Pak můžete spustit **pgosweep** před ukončením aplikace. Shromážděná data nyní obsahují informace o profilu z času, kdy by uživatel mohl s programem pracovat.

Při pojmenování souboru. pgc (pomocí parametru *pgcfile* ) můžete použít standardní formát, který je *AppName! n*. pgc. Použijete-li tento formát, kompilátor automaticky vyhledá tato data ve fázi **/LTCG/USEPROFILE** nebo **/LTCG: PGO** . Pokud nepoužíváte standardní formát, je nutné použít [pgomgr](pgomgr.md) ke sloučení souborů. pgc.

> [!NOTE]
> Tento nástroj můžete spustit pouze z příkazového řádku pro vývojáře v aplikaci Visual Studio. Nemůžete ho spustit z příkazového řádku systému nebo z Průzkumníka souborů.

Informace o tom, jak zachytit profilová data v rámci spustitelného souboru, najdete v tématu [PgoAutoSweep](pgoautosweep.md).

## <a name="example"></a>Příklad

V tomto příkladu příkazu **pgosweep** zapisuje aktuální informace o profilu pro MyApp. exe do MyApp. 1. pgc.

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Viz také

[Optimalizace na základě profilu](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
