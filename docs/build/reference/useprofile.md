---
title: / USEPROFILE (použití PGO dat pomocí LTCG)
ms.date: 03/14/2018
f1_keywords:
- USEPROFILE
ms.openlocfilehash: 7bc0033ae5ef512cbd2e2063c5cb9bd9b061c180
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816526"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/ USEPROFILE (spustit PGO v nouzovém režimu vlákno)

Tohoto parametru linkeru spolu s [parametru/LTCG (generování kódu při propojování odkaz](ltcg-link-time-code-generation.md) přikazuje linkeru, aby sestavení pomocí profilováním řízené optimalizace (PGO) trénovací data.

## <a name="syntax"></a>Syntaxe

> **/ USEPROFILE**[**:**{**AGGRESSIVE**|**PGD =**_filename_}]

### <a name="arguments"></a>Arguments

**AGRESIVNÍ**<br/>
Tento nepovinný argument určuje, že optimalizací pro rychlost agresivní má být použito při generování optimalizovaného kódu.

**PGD**=*filename*<br/>
Určuje název základního souboru pro soubor .pgd. Ve výchozím nastavení používá propojovací program název základní spustitelného souboru s příponou .pgd.

## <a name="remarks"></a>Poznámky

**/Useprofile** – možnost linkeru se používá spolu s **parametru/LTCG** vytvořit nebo aktualizovat optimalizovaných sestavení podle PGO trénovací data. Je ekvivalentem zastaralá **/LTCG:PGUPDATE** a **/LTCG:PGOPTIMIZE** možnosti.

Volitelný **AGGRESSIVE** argument zakáže velikost související heuristiku k pokusu o optimalizovat rychlost. Výsledkem může být optimalizace, které podstatně zvýšit velikost spustitelný soubor a nemusí výsledný zrychlit. By měl profil a porovnejte výsledky pomocí a bez použití **AGGRESSIVE**. Tento argument musí být zadané explicitně; ve výchozím nastavení není povoleno.

**PGD** argument určuje nepovinný název pro soubor .pgd trénovací data chcete použít, stejně jako ve [/genprofile nebo /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md). Je ekvivalentem zastaralá **/PGD** přepnout. Ve výchozím nastavení nebo pokud žádná *filename* není zadán, soubor .pgd, který má stejný základní název jako spustitelný soubor se používá.

**/Useprofile** – možnost linkeru Novinky v sadě Visual Studio 2015.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **optimalizace** stránku vlastností.

1. V **generování kódu při propojování** vlastnost, zvolte **použijte generování kódu při propojování (/ LTCG)**.

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte **/useprofile** možnost a nepovinné argumenty do **další možnosti** pole. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/ GENPROFILE a /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optimalizace na základě profilu](../profile-guided-optimizations.md)<br/>
[Proměnné prostředí pro optimalizace na základě profilu](../environment-variables-for-profile-guided-optimizations.md)<br/>
