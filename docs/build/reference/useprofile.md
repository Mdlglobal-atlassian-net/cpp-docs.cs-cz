---
title: / USEPROFILE (použití PGO data s LTCG) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- USEPROFILE
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156a571eaa3db31b8c5345f1550346503651665d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377990"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/ USEPROFILE (PGO spuštění v nouzovém režimu přístup z více vláken)

Tato – možnost linkeru společně s [/ltgc (vytváření kódu v době propojování](ltcg-link-time-code-generation.md) informuje linkeru pro sestavení pomocí optimalizace na základě profilu (PGO) Cvičná data.

## <a name="syntax"></a>Syntaxe

> **/ USEPROFILE**[**:**{**AGGRESSIVE**|**PGD =**_filename_}]

### <a name="arguments"></a>Arguments

**AGRESIVNÍ**<br/>
Tento volitelný argument určuje, že agresivní rychlost optimalizace by měl používat při generování optimalizovaného kódu.

**PGD**=*filename*<br/>
Určuje název základního souboru pro soubor .pgd. Ve výchozím nastavení používá linkeru název základní spustitelného souboru s příponou .pgd.

## <a name="remarks"></a>Poznámky

**/USEPROFILE** – možnost linkeru je použít v kombinaci s **/ltgc** ke generování nebo aktualizovat optimalizovaného sestavení na základě dat PGO školení. Jde o ekvivalent nepoužívané **/LTCG:PGUPDATE** a **/LTCG:PGOPTIMIZE** možnosti.

Volitelné **AGGRESSIVE** argument zakáže heuristiky velikost související se pokusit o optimalizovat pro rychlost. To může mít za následek optimalizace, které podstatně zvětšit velikost vašeho spustitelný soubor a nemusí výsledné zrychlit. Měli byste profilu a porovnejte výsledky používání a není **AGGRESSIVE**. Tento argument musí být zadán explicitně; ve výchozím nastavení není povolený.

**PGD** argument určuje nepovinný název souboru školení dat .pgd používat stejné jako v [/GENPROFILE nebo /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md). Jde o ekvivalent nepoužívané **/PGD** přepínače. Ve výchozím nastavení nebo pokud žádné *filename* není zadaný, .pgd soubor, který má stejný název základní jako spustitelný soubor se používá.

**/USEPROFILE** – možnost linkeru je nového ve Visual Studiu 2015.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **optimalizace** stránku vlastností.

1. V **vytvoření kódu v době odkaz** vlastnost, zvolte **vytvoření kódu v době použití odkaz (/ LTCG)**.

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte **/USEPROFILE** možnost a volitelné argumenty do **další možnosti** pole. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[/ GENPROFILE a /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md)<br/>
[Proměnné prostředí pro optimalizace na základě profilu](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
