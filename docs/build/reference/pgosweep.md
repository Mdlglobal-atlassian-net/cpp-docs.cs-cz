---
title: pgosweep – | Microsoft Docs
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9680dc47d850bd49eff343c0e382b7132697858d
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="pgosweep"></a>pgosweep

Používá se v optimalizace na základě profilu zapsat všechna data profilu z spuštěným programem do souboru .pgc.

## <a name="syntax"></a>Syntaxe

> **pgosweep** [*options*] *image* *pgcfile*

### <a name="parameters"></a>Parametry

*možnosti* (volitelné)<br/>
Platné hodnoty pro *možnosti* jsou:

- **/?** nebo **/help** zobrazí zprávu nápovědy.

- **/noreset** zachovává počet v modulu runtime datové struktury.

*image*<br/>
Úplná cesta souboru .exe nebo .dll, který byl vytvořen pomocí [/GENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md), nebo [/LTCG:PGINSTRUMENT](ltcg-link-time-code-generation.md) možnost.

*pgcfile*<br/>
Soubor .pgc, kde tento příkaz zapíše data počty.

## <a name="remarks"></a>Poznámky

**Pgosweep –** příkaz lze použít na programy, které byly vytvořené pomocí [/GENPROFILE nebo /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) možnost nebo zastaralé [/LTCG:PGINSTRUMENT](ltcg-link-time-code-generation.md) možnost. To přerušení spuštěným programem a zapisuje data profilu do nového souboru .pgc. Ve výchozím nastavení příkaz obnoví počty po každé operaci zápisu. Pokud zadáte **/noreset** možnost příkaz záznam hodnoty, ale neprovádí vynulování je v běžící aplikaci. Tato možnost dává duplicitních dat. Pokud načíst data profilu později.

Alternativní použití pro **pgosweep –** je načíst informace o profilu právě k normálnímu fungování aplikace. Například můžete spustit **pgosweep –** krátce po spuštění aplikace a zahodit tento soubor. To by odeberte profil data související s náklady na spuštění. Potom můžete spustit **pgosweep –** před ukončením aplikace. Shromážděná data má teď informace o profilu pouze od okamžiku, že uživatel může komunikovat s programem.

Když zadáte název souboru .pgc (pomocí *pgcfile* parametr) můžete použít ve standardním formátu, který je *appname! n*.pgc. Pokud použijete tento formát, kompilátor automaticky vyhledá tato data v **/LTCG /USEPROFILE** nebo **/LTCG:PGO** fáze. Pokud použijete ve standardním formátu, musíte použít [pgomgr –](pgomgr.md) sloučit .pgc soubory.

> [!NOTE]
> Tento nástroj můžete spustit pouze z příkazového řádku vývojáře Visual Studio. Nelze ji spustit z příkazového řádku systému nebo v Průzkumníku souborů.

Informace o tom, jak zachytit profil data přímo z vašeho spustitelný soubor najdete v tématu [PgoAutoSweep](pgoautosweep.md).

## <a name="example"></a>Příklad

V tomto příkladu příkazu **pgosweep –** zapíše aktuální informace o profilu pro myapp.exe myapp!1.pgc.

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Viz také

[Optimalizace na základě profilu](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
