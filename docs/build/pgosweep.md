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

Profilováním řízená optimalizace používají k zápisu všechna data profilu ze spuštěný program do souboru .pgc.

## <a name="syntax"></a>Syntaxe

> **pgosweep** [*options*] *image* *pgcfile*

### <a name="parameters"></a>Parametry

*Možnosti*<br/>
(Volitelné) Platné hodnoty pro *možnosti* jsou:

- **/?** nebo **/help** zobrazí zprávu nápovědy.

- **/noreset** zachová počet v datovými strukturami modulu CLR.

*image*<br/>
Úplná cesta souboru .exe nebo .dll, který byl vytvořen pomocí [/genprofile](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), nebo [/LTCG:PGINSTRUMENT](reference/ltcg-link-time-code-generation.md) možnost.

*pgcfile*<br/>
Soubor .pgc, ve kterém tento příkaz zapíše data počty.

## <a name="remarks"></a>Poznámky

**Pgosweep** příkaz funguje s programy, které byly vytvořeny pomocí [/genprofile nebo /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) možnost nebo zastaralá [/LTCG:PGINSTRUMENT](reference/ltcg-link-time-code-generation.md) možnost. Přeruší spuštěný program a zapisuje data profilu do nového souboru .pgc. Ve výchozím nastavení tento příkaz obnoví počty po každé operaci zápisu. Pokud zadáte **/noreset** možnosti příkazu poznamenejte si hodnoty, ale nelze je obnovit v běžící aplikaci. Tato možnost poskytuje duplicitních dat. Pokud později načíst data profilu.

Alternativní použití pro **pgosweep** je načíst informace o profilu pro normální provoz aplikace. Například můžete spustit **pgosweep** krátce po spuštění aplikace a zrušit tento soubor. To by odebrat profil data související s náklady na spuštění. Potom můžete spustit **pgosweep** před ukončením aplikace. Shromážděná data má teď informace z profilu pouze od doby, uživatel může pracovat s programem.

Pokud název souboru .pgc (s použitím *pgcfile* parametr) můžete použít standardní formát, který je *appname! n*.pgc. Pokud použijete tento formát, kompilátor automaticky vyhledá tato data v **/LTCG/useprofile** nebo **/LTCG:PGO** fáze. Pokud nepoužijete standardního formátu, je nutné použít [pgomgr](pgomgr.md) sloučit soubory .pgc.

> [!NOTE]
> Tento nástroj můžete spustit pouze z příkazového řádku pro vývojáře Visual Studio. Nelze provést toto spuštění z příkazového řádku systému nebo Průzkumníka souborů.

Informace o tom, jak zachytávat data profilu z v rámci spustitelný soubor najdete v tématu [PgoAutoSweep](pgoautosweep.md).

## <a name="example"></a>Příklad

V tomto ukázkovém příkazu **pgosweep** zapíše aktuální informace profilu pro myapp.exe myapp!1.pgc.

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Viz také:

[Optimalizace na základě profilu](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
