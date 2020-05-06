---
title: /GENPROFILE, -FASTGENPROFILE (generování profilace instrumentovaného sestavení)
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
ms.openlocfilehash: 19ddf56d92cc2d8fbbfaf635c8e1602443e35b5b
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825781"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE, -FASTGENPROFILE (generování profilace instrumentovaného sestavení)

Určuje generování souboru. pgd linkerem, který podporuje optimalizaci na základě profilu (PGO). **/GENPROFILE** a **/FASTGENPROFILE** používají jiné výchozí parametry. Pomocí **/GENPROFILE** můžete upřednostnit přesnost využití rychlosti a paměti během profilace. Pomocí **/FASTGENPROFILE** můžete upřednostnit menší využití paměti a zrychlit jejich přesnost.

## <a name="syntax"></a>Syntaxe

> **/GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [ **Přesná**|**Shoda] |** **MEMMAX =**_#_|**MEMMIN =**_#_| [**cesta k cestě**|**] |** [**TRACKEH** |**NOTRACKEH** ] | **PGD =**_filename_}] \
> **/FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [ **Přesná**|**Shoda] |** **MEMMAX =**_#_|**MEMMIN =**_#_| [**cesta k cestě**|**] |** [**TRACKEH** |**NOTRACKEH** ] | **PGD =**_filename_}]

### <a name="arguments"></a>Argumenty

Pro **/GENPROFILE** nebo **/FASTGENPROFILE**lze zadat kterýkoli z následujících argumentů. Argumenty, které jsou zde uvedeny, oddělené**|** znakem svislé čáry () se vzájemně vylučují. K oddělení možností použijte znak čárky (**,**).

**COUNTER32** &#124; **COUNTER64**<br/>
Použijte **COUNTER32** k určení použití 32 čítačů sondy a **COUNTER64** pro určení 64 čítačů testu paměti. Když zadáte **/GENPROFILE**, výchozí hodnota je **COUNTER64**. Když zadáte **/FASTGENPROFILE**, výchozí hodnota je **COUNTER32**.

**Přesný** &#124; **nepřesný**<br/>
Použijte **přesně** k zadání přístupných dat zabezpečených pro přístup z více vláken pro sondy. **Nepřesně** určuje nechráněné operace přírůstku pro sondy. Výchozí hodnota je **přesně**.

**MEMMAX**=*Hodnota*MEMMAX, **MEMMIN**=*hodnota* MEMMIN<br/>
Pomocí **MEMMAX** a **MEMMIN** určete maximální a minimální velikost rezervací pro školicí data v paměti. Hodnota je velikost paměti, která se má rezervovat v bajtech. Ve výchozím nastavení jsou tyto hodnoty určeny interní heuristickou.

**Cesta** &#124; **NOPATH** cesta <br/>
Použijte **cestu** k určení samostatné sady čítačů PGO pro každou jedinečnou cestu k funkci. Použijte **cestu** k určení pouze jedné sady čítačů pro každou funkci. Když zadáte **/GENPROFILE**, výchozí hodnota je **cesta** . Když zadáte **/FASTGENPROFILE**, výchozí hodnota je **cesta** .

**TRACKEH** &#124; **NOTRACKEH** <br/>
Určuje, zda se mají použít čítače navíc pro zachování přesného počtu, kdy jsou výjimky vyvolány během školení. Pomocí **TRACKEH** můžete určit nadbytečné čítače pro přesný počet. Použijte **NOTRACKEH** k určení jednoduchých čítačů pro kód, který nepoužívá zpracování výjimek nebo který ve školicích scénářích nenalezne výjimky.  Když zadáte **/GENPROFILE**, výchozí hodnota je **TRACKEH** . Když zadáte **/FASTGENPROFILE**, výchozí hodnota je **NOTRACKEH** .

**PGD**=*Název souboru* PGD<br/>
Určuje základní název souboru pro soubor. pgd. Ve výchozím nastavení Linker používá základní název spustitelného souboru bitové kopie s příponou. pgd.

## <a name="remarks"></a>Poznámky

Možnosti **/GENPROFILE** a **/FASTGENPROFILE** říká linkeru, aby vygeneroval soubor instrumentace potřebný k podpoře školení aplikací pro optimalizaci na základě profilu (PGO). Tyto možnosti jsou v aplikaci Visual Studio 2015 nové. Preferovat tyto možnosti jako zastaralé možnosti **/LTCG: PGINSTRUMENT**, **/PGD** a **/POGOSAFEMODE** a proměnné prostředí **POGOSAFEMODE**, **VCPROFILE_ALLOC_SCALE** a **VCPROFILE_PATH** . Informace profilování vygenerované školením aplikací se používají jako vstup k provádění optimalizací cíleného celého programu během sestavení. Můžete nastavit další možnosti pro řízení různých funkcí profilování pro výkon během školení a sestavení aplikace. Výchozí možnosti určené **/GENPROFILE** poskytují nejpřesnější výsledky, zejména pro velké komplexní aplikace s více vlákny. Možnost **/FASTGENPROFILE** používá jiné výchozí hodnoty pro nižší nároky na paměť a rychlejší výkon během školení na úkor přesnosti.

Informace profilování se zachycuje při spuštění instrumentované aplikace po sestavení pomocí **/GENPROFILE** z **/FASTGENPROFILE**. Tyto informace jsou zachyceny, když zadáte možnost linkeru [/USEPROFILE](useprofile.md) pro provedení kroku profilování a potom použijete k nastavení optimalizovaného kroku sestavení. Další informace o tom, jak ve shromážděných datech naučit svoji aplikaci a podrobnosti, najdete v tématu Optimalizace na základě [profilu](../profile-guided-optimizations.md).

Je nutné zadat také **/LTCG** při zadání **/GENPROFILE** nebo **/FASTGENPROFILE**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností**příkazový řádek**  > **linkeru** >  **vlastností konfigurace**.

1. Do pole **Další možnosti** zadejte možnosti a argumenty **/GENPROFILE** nebo **/FASTGENPROFILE** . Kliknutím na **tlačítko OK** uložte změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)<br/>
[/LTCG (generování kódu během propojování)](ltcg-link-time-code-generation.md)<br/>
