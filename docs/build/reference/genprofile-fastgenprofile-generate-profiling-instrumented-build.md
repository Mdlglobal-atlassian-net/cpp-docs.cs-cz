---
title: / GENPROFILE, /FASTGENPROFILE (Generovat profilace instrumentovaného sestavení) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b6174c1fdd53ec14f0cb63292a9036caabc98a7d
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/ GENPROFILE, /FASTGENPROFILE (Generovat profilace instrumentovaného sestavení)

Určuje generování souboru .pgd podle linkeru pro podporu optimalizace na základě profilu (PGO). **/ GENPROFILE** a **/FASTGENPROFILE** používat různé výchozí parametry. Použití **/GENPROFILE** k upřednostnit přesnost přes rychlost a použití paměti při vytváření profilu. Použití **/FASTGENPROFILE** k upřednostnit menší využití paměti a rychlost přes přesnost.

## <a name="syntax"></a>Syntaxe

> **/GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**]|[**EXACT**|**NOEXACT**]|**MEMMAX=**_#_|**MEMMIN=**_#_|[**PATH**|**NOPATH** ]|[**TRACKEH** |**NOTRACKEH** ]|**PGD=**_filename_}]<br/>
> **/FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**]|[**EXACT**|**NOEXACT**]|**MEMMAX=**_#_|**MEMMIN=**_#_|[**PATH**|**NOPATH** ]|[**TRACKEH** |**NOTRACKEH** ]|**PGD=**_filename_}]

### <a name="arguments"></a>Arguments

Některý z následujících argumentů může být určen k **/GENPROFILE** nebo **/FASTGENPROFILE**. Argumenty, které jsou zde uvedeny odděleny znakem (**|**) znak se vzájemně vylučují. Použít čárku (**,**) znak pro oddělení možností.

**COUNTER32** &AMP;#124; **COUNTER64**<br/>
Použít **COUNTER32** použít, použijte 32-bit test čítačů a **COUNTER64** k určení 64-bit test čítače. Pokud zadáte **/GENPROFILE**, výchozí hodnota je **COUNTER64**. Pokud zadáte **/FASTGENPROFILE**, výchozí hodnota je **COUNTER32**.

**PŘESNÉ** &AMP;#124; **NOEXACT**<br/>
Použití **EXACT** k určení interlocked přírůstcích vláken pro testy paměti. **NOEXACT** určuje nechráněné přírůstek operací pro testy paměti. Výchozí hodnota je **NOEXACT**.

**MEMMAX**=*hodnotu*, **MEMMIN**=*hodnota*<br/>
Použití **MEMMAX** a **MEMMIN** k určení rezervace maximální a minimální velikosti pro Cvičná data v paměti. Hodnota je množství paměti tak, aby vyhradil v bajtech. Ve výchozím nastavení tyto hodnoty jsou určeny interní heuristiky.

**PATH**  &#124; **NOPATH** <br/>
Použití **cesta** zadat samostatnou sadu čítačů PGO pro každý jedinečný cestu na funkci. Použití **NOPATH** zadat jen jednu sadu čítačů pro každou funkci. Pokud zadáte **/GENPROFILE**, výchozí hodnota je **CESTU** . Pokud zadáte **/FASTGENPROFILE**, výchozí hodnota je **NOPATH** .

**TRACKEH** &AMP;#124; **NOTRACKEH**  <br/>
Určuje, jestli se má používat další čítače zachovat aktuální přehled, pokud jsou výjimky vyvolány během cvičení. Použití **TRACKEH** zadat další čítače pro přesný počet. Použít **NOTRACKEH** k zadání jednoho čítače pro kód, který nepoužívá výjimka zpracování nebo které není dojde výjimky v vaše scénáře školení.  Pokud zadáte **/GENPROFILE**, výchozí hodnota je **TRACKEH** . Pokud zadáte **/FASTGENPROFILE**, výchozí hodnota je **NOTRACKEH** .

**PGD**=*filename*<br/>
Určuje název základního souboru pro soubor .pgd. Ve výchozím nastavení používá linkeru název základní spustitelné bitové kopie souboru s příponou .pgd.

## <a name="remarks"></a>Poznámky

**/GENPROFILE** a **/FASTGENPROFILE** říct možnosti linkeru pro generování souboru profilování instrumentace potřeba k podpoře aplikace školení pro optimalizace na základě profilu (PGO). Tyto možnosti jsou novinkou ve Visual Studiu 2015. Dáváte přednost těchto možností zastaralé **/LTCG:PGINSTRUMENT**, **/PGD** a **/POGOSAFEMODE** možnosti a **PogoSafeMode**,  **Vcprofile_alloc_scale –** a **vcprofile_path –** proměnné prostředí. Analytické informace generované školení aplikace se používá jako vstup pro provedení cílem optimalizace celého programu během sestavení. Můžete nastavit další možnosti k ovládání různých funkcí profilování výkonu během cvičení aplikace a sestavení. Výchozí možnosti určeného **/GENPROFILE** poskytují nejpřesnější výsledky, zejména pro složitých vícevláknové aplikace. **/FASTGENPROFILE** možnost využívá různé výchozí hodnoty pro dosažení vyššího výkonu během cvičení za cenu přesnost a nižší nároky na paměť.

Profilace informace zachycenou při spuštění aplikace instrumentované po vytvoření pomocí **/GENPROFILE** z **/FASTGENPROFILE**. Tyto informace je zachycení, když zadáte [/USEPROFILE](useprofile.md) – možnost linkeru provést profilace krok a pak se použije pro Průvodce krok optimalizovaného sestavení. Další informace o tom, jak cvičení vaší aplikace a podrobnosti o shromažďovaných datech najdete v tématu [optimalizace na základě profilu](profile-guided-optimizations.md).

Musíte zadat také **/ltgc** při zadání **/GENPROFILE** nebo **/FASTGENPROFILE**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte **/GENPROFILE** nebo **/FASTGENPROFILE** možnosti a argumenty do **další možnosti** pole. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[/LTCG (generování kódu během propojování)](../../build/reference/ltcg-link-time-code-generation.md)<br/>
