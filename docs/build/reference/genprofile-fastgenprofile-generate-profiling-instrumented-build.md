---
title: / GENPROFILE, -fastgenprofile (generování profilace instrumentovaného sestavení)
ms.date: 03/14/2018
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
ms.openlocfilehash: e703c94d4a8b7cf7c70e68071959b775987f1710
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496444"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/ GENPROFILE, -fastgenprofile (generování profilace instrumentovaného sestavení)

Určuje generování souboru .pgd linkerem pro podporu profilováním řízené optimalizace (PGO). **/ GENPROFILE** a **/FASTGENPROFILE** používají různé výchozí parametry. Použití **/genprofile** , aby přesnosti upřednostnil před rychlostí a využití paměti během profilace. Použití **/FASTGENPROFILE** do menších využití paměti a rychlost upřednostnil před přesnosti.

## <a name="syntax"></a>Syntaxe

> **/ GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [**EXACT**|**NOEXACT**] | **MEMMAX =**_#_|**MEMMIN =**_#_| [**Cesta**|**NOPATH** ] | [**TRACKEH** |**NOTRACKEH** ] | **PGD =**_filename_}]<br/>
> **/ FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [**EXACT**|**NOEXACT**] | **MEMMAX =**_#_|**MEMMIN =**_#_| [**Cesta**|**NOPATH** ] | [**TRACKEH** |**NOTRACKEH** ] | **PGD =**_filename_}]

### <a name="arguments"></a>Arguments

Některý z následujících argumentů dají **/genprofile** nebo **/FASTGENPROFILE**. Zde uvedené argumenty oddělená znakem | (**|**) znaků se vzájemně vylučují. Čárkami (**,**) znak k oddělení možností.

**COUNTER32** &AMP;#124; **COUNTER64**<br/>
Použít **COUNTER32** použít, použijte 32bitový test čítačů a **COUNTER64** k určení testu 64-bit čítače. Pokud zadáte **/genprofile**, výchozí hodnota je **COUNTER64**. Pokud zadáte **/FASTGENPROFILE**, výchozí hodnota je **COUNTER32**.

**PŘESNÉ** &AMP;#124; **NOEXACT**<br/>
Použití **EXACT** k určení propojené přírůstky bezpečným pro vlákno pro testy. **NOEXACT** určuje operace Inkrementace nechráněné pro testy. Výchozí hodnota je **NOEXACT**.

**MEMMAX**=*hodnotu*, **MEMMIN**=*hodnota*<br/>
Použití **MEMMAX** a **MEMMIN** k určení rezervace maximální a minimální velikosti pro trénovací data v paměti. Hodnota je množství paměti pro rezervaci v bajtech. Ve výchozím nastavení tyto hodnoty jsou určeny interní heuristiky.

**CESTA** &AMP;#124; **NOPATH**  <br/>
Použití **cesta** zadat samostatnou sadu čítačů PGO pro každou jedinečnou cestu k funkci. Použití **NOPATH** zadat pouze jednu sadu čítačů pro každou funkci. Pokud zadáte **/genprofile**, výchozí hodnota je **cesta** . Pokud zadáte **/FASTGENPROFILE**, výchozí hodnota je **NOPATH** .

**TRACKEH** &AMP;#124; **NOTRACKEH**  <br/>
Určuje, jestli se má použít další čítače zachovat přesný počet, pokud jsou výjimky vyvolány během cvičení. Použití **TRACKEH** zadat další čítače pro přesný počet. Použít **NOTRACKEH** k určení jednoho čítače pro kód, který nepoužívá výjimky zpracování nebo, který není nastat výjimky ve vašich scénářích školení.  Pokud zadáte **/genprofile**, výchozí hodnota je **TRACKEH** . Pokud zadáte **/FASTGENPROFILE**, výchozí hodnota je **NOTRACKEH** .

**PGD**=*filename*<br/>
Určuje název základního souboru pro soubor .pgd. Ve výchozím nastavení používá propojovací program spustitelná image, která základní název souboru s příponou .pgd.

## <a name="remarks"></a>Poznámky

**/Genprofile** a **/FASTGENPROFILE** řekněte možnosti linkeru, aby generoval soubor profilování instrumentace potřeba k podpoře aplikace školení pro optimalizace na základě profilu (PGO). Tyto možnosti jsou nové v sadě Visual Studio 2015. Preferovat tyto možnosti se zastaralou **/LTCG:PGINSTRUMENT**, **/PGD** a **/POGOSAFEMODE** možnosti a **PogoSafeMode**,  **Vcprofile_alloc_scale –** a **vcprofile_path –** proměnné prostředí. Profilování informace generované aplikace školení se používá jako vstup provádět cílené optimalizace celého programu během sestavení. Můžete nastavit další možnosti ovládání různých funkcí profilování výkonu během cvičení aplikace a sestavení. Výchozí možnosti nastavené podle **/genprofile** poskytnout nejpřesnější možné výsledky, hlavně pro velké a komplexní vícevláknové aplikace. **/FASTGENPROFILE** možnost používá různé výchozí hodnoty pro nižší paměťové nároky a vyšší výkon při školení, ovšem na úkor přesnosti.

Informace pro profilaci jsou zachyceny po spuštění instrumentované aplikace po sestavení s použitím **/genprofile** z **/FASTGENPROFILE**. Tyto informace jsou zachyceny při zadávání [/useprofile](useprofile.md) – možnost linkeru provádět profilaci krok a pak použije k provedou kroky optimalizovaných sestavení. Další informace o tom, jak trénovat vaší aplikace a podrobnosti o shromážděných datech najdete v tématu [optimalizace na základě profilu](profile-guided-optimizations.md).

Musíte zadat také **parametru/LTCG** při zadání **/genprofile** nebo **/FASTGENPROFILE**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte **/genprofile** nebo **/FASTGENPROFILE** možnosti a argumenty do **další možnosti** pole. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[/LTCG (generování kódu během propojování)](../../build/reference/ltcg-link-time-code-generation.md)<br/>
