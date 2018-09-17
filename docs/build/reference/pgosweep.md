---
title: pgosweep | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed12828d9170aac576a97c63b9988bb4b303ef58
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711913"
---
# <a name="pgosweep"></a>pgosweep

Profilováním řízená optimalizace používají k zápisu všechna data profilu ze spuštěný program do souboru .pgc.

## <a name="syntax"></a>Syntaxe

> **pgosweep** [*možnosti*] *image* *pgcfile*

### <a name="parameters"></a>Parametry

*Možnosti*<br/>
(Volitelné) Platné hodnoty pro *možnosti* jsou:

- **/?** nebo **/help** zobrazí zprávu nápovědy.

- **/noreset** zachová počet v datovými strukturami modulu CLR.

*Bitové kopie*<br/>
Úplná cesta souboru .exe nebo .dll, který byl vytvořen pomocí [/genprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md), nebo [/LTCG:PGINSTRUMENT](ltcg-link-time-code-generation.md) možnost.

*pgcfile*<br/>
Soubor .pgc, ve kterém tento příkaz zapíše data počty.

## <a name="remarks"></a>Poznámky

**Pgosweep** příkaz funguje s programy, které byly vytvořeny pomocí [/genprofile nebo /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) možnost nebo zastaralá [/LTCG:PGINSTRUMENT](ltcg-link-time-code-generation.md) možnost. Přeruší spuštěný program a zapisuje data profilu do nového souboru .pgc. Ve výchozím nastavení tento příkaz obnoví počty po každé operaci zápisu. Pokud zadáte **/noreset** možnosti příkazu poznamenejte si hodnoty, ale nelze je obnovit v běžící aplikaci. Tato možnost poskytuje duplicitních dat. Pokud později načíst data profilu.

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
