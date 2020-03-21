---
title: /Z7, /Zi, /ZI (formát ladicích informací)
ms.date: 04/08/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
helpviewer_keywords:
- C7 compatible compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.openlocfilehash: aeaf435874b6d6b9dbc8a3d12ec06d38bf33aaae
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078267"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (formát ladicích informací)

Určuje typ informací o ladění vytvořených pro program a zda jsou tyto informace uloženy v objektových souborech nebo v souboru databáze programu (PDB).

## <a name="syntax"></a>Syntaxe

> **/Z**{**7**|**i**|**i**}

## <a name="remarks"></a>Poznámky

Když je kód kompilován a sestaven v režimu ladění, kompilátor vytvoří názvy symbolů pro funkce a proměnné, informace o typu a umístění čísel řádků pro použití v ladicím programu. Tyto symbolické ladicí informace lze zahrnout buď do souborů objektů (soubory. obj) vytvořených kompilátorem, nebo v samostatném souboru PDB (soubor. pdb) pro spustitelný soubor.  Možnosti formátu ladicích informací jsou popsány v následujících částech.

### <a name="none"></a>Žádná

Ve výchozím nastavení, pokud není zadána možnost formátu ladicích informací, kompilátor nevytváří žádné ladicí informace, takže kompilace je rychlejší.

### <a name="z7"></a>/Z7

Možnost **/Z7** vytváří soubory objektů, které také obsahují úplné symbolické ladicí informace pro použití s ladicím programem. Tyto soubory objektů a sestavený spustitelný soubor mohou být podstatně větší než soubory, které nemají žádné informace o ladění. Symbolické ladicí informace obsahují názvy a typy proměnných a také funkce a čísla řádků. Nevytvoří se žádný soubor PDB.

Pro distributory ladicích verzí knihoven třetích stran je výhodná neexistence souboru PDB. Nicméně soubory objektů pro všechny předkompilované hlavičky jsou nezbytné během fáze propojení knihovny a pro ladění. Pokud jsou v souboru objektu. pch k dispozici pouze informace typu (a žádný kód), musíte také použít možnost [/yl (vložit odkaz PCH pro knihovnu ladění)](yl-inject-pch-reference-for-debug-library.md) , která je ve výchozím nastavení povolena při sestavení knihovny.

Nepoužívané možnosti [/GM (povolit minimální opětovné sestavení)](gm-enable-minimal-rebuild.md) nejsou k dispozici, pokud je zadána možnost **/Z7** .

### <a name="zi"></a>/Zi

Možnost **/Zi** vytvoří samostatný soubor PDB, který obsahuje všechny informace o symbolickém ladění pro použití s ladicím programem. Informace o ladění nejsou součástí souborů nebo spustitelného souboru objektů, což je mnohem menší.

Použití **/Zi** nemá vliv na optimalizace. Nicméně **/Zi** má za následek **/Debug**; Další informace naleznete v tématu [/Debug (generování informací o ladění)](debug-generate-debug-info.md) .

Když zadáte jak **/Zi** , tak i **/clr**, atribut <xref:System.Diagnostics.DebuggableAttribute> není umístěn v metadatech sestavení. Pokud chcete, musíte ho zadat ve zdrojovém kódu. Tento atribut může ovlivnit výkon modulu runtime aplikace. Další informace o tom, jak má **laditelné** atributy vliv na výkon a jak můžete změnit dopad na výkon, naleznete v tématu [usnadnění ladění obrázku](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

Kompilátor pojmenovává soubor PDB *Project*. pdb. Pokud kompilujete soubor mimo projekt, kompilátor vytvoří soubor PDB s názvem VC*x*. pdb, kde *x* je zřetězení čísla hlavní a podverze používané verze kompilátoru. Kompilátor vloží název PDB a identifikuje signaturu s časovým razítkem v každém souboru objektů vytvořeném pomocí této možnosti, která ukazuje ladicí program na umístění symbolického čísla a informace o čísle řádku. Název a signatura v souboru PDB se musí shodovat se spustitelným souborem pro symboly, které mají být načteny do ladicího programu. Ladicí program WinDBG může načíst neshodné symboly pomocí příkazu `.symopt+0x40`. V aplikaci Visual Studio není k dispozici podobná možnost načtení neodpovídajících symbolů.

Pokud vytvoříte knihovnu z objektů, které byly zkompilovány pomocí **/Zi**, musí být přidružený soubor. pdb k dispozici, když je knihovna propojena s programem. Proto při distribuci knihovny je nutné také distribuovat soubor PDB. Chcete-li vytvořit knihovnu, která obsahuje ladicí informace bez použití souborů PDB, je nutné vybrat možnost **/Z7** . Použijete-li možnosti předkompilovaných hlaviček, informace o ladění pro předkompilovanou hlavičku a zbytek zdrojového kódu jsou umístěny v souboru PDB.

### <a name="zi"></a>/ZI

Parametr **/Zi** je podobný jako **/Zi**, ale vytvoří soubor PDB ve formátu, který podporuje funkci [Upravit a pokračovat](/visualstudio/debugger/edit-and-continue-visual-cpp) . Chcete-li používat funkce pro ladění a pokračování pro ladění, je nutné použít tuto možnost. Funkce upravit a pokračovat je užitečná pro produktivitu vývojářů, ale může způsobovat problémy v rozsahu kódu, výkonu a souladu s kompilátorem. Vzhledem k tomu, že většina optimalizací není kompatibilní s úpravou a pokračováním, zakáže použití **/Zi** v kódu příkazy `#pragma optimize`. Možnost **/Zi** je také nekompatibilní s používáním [ &#95; &#95;předdefinovaného&#95; &#95; makra line](../../preprocessor/predefined-macros.md); kód kompilovaný pomocí **/Zi** nemůže používat **&#95; &#95;řádek&#95;** jako Netypový argument šablony, i když  **&#95; &#95;lze použít&#95; spojnici** v rozšířeních maker.

Možnost **/Zi** vynutí použití možnosti [/Gy (Povolit propojování na úrovni funkcí)](gy-enable-function-level-linking.md) a [/FC (úplná cesta k souboru zdrojového kódu v diagnostice)](fc-full-path-of-source-code-file-in-diagnostics.md) , která se má použít ve vaší kompilaci.

**/Zi** není kompatibilní s možností [/CLR (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md).

> [!NOTE]
> Možnost **/Zi** je k dispozici pouze v kompilátorech cílících na procesory x86 a x64; Tato možnost kompilátoru není dostupná v kompilátorech, které cílí na procesory ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Otevřete **Vlastnosti konfigurace** > **Obecné** stránce vlastností **CC++ /**  > .

1. Upravte vlastnost **formát ladicích informací** . Kliknutím na **tlačítko OK** uložte změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
