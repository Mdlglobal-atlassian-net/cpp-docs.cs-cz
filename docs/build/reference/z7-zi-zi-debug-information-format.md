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
ms.openlocfilehash: e809c7af7465cde98db11eac8628b76d04f7e8b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316285"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (formát ladicích informací)

Určuje typ ladicích informací vytvářených pro program a zda tyto informace jsou uchovávány v souborech objektů nebo v souboru databáze (PDB) programu.

## <a name="syntax"></a>Syntaxe

> **/Z**{**7**|**i**|**I**}

## <a name="remarks"></a>Poznámky

Pokud kód je zkompilován a vytvořené v režimu ladění, kompilátor vytvoří názvy symbolů pro funkce a proměnné, informace o typu a umístění číslo řádku pro použití ladicím programem. Symbolickém ladění může být zahrnuté v souborech objektů (soubory .obj) produkované kompilátorem nebo v samostatném souboru PDB (soubor typu .pdb) pro spustitelný soubor.  Možnosti formátování informace o ladění jsou popsány v následujících částech.

### <a name="none"></a>Žádné

Ve výchozím nastavení Pokud není zadána žádná možnost formát informací ladění, kompilátor nevytváří žádné ladicí informace, kompilace je proto rychlejší.

### <a name="z7"></a>/Z7

**/Z7** možnost vytvoří soubory objektů, které také obsahují úplné symbolické ladicí informace pro použití s ladicím programem. Tyto soubory objektů a připravené spustitelný soubor může být podstatně větší než soubory, které mají žádné ladicí informace. Symbolické ladicí informace obsahují názvy a typy proměnných a také funkce a čísla řádků. Není vytvořen žádný soubor PDB.

Pro distributory ladicích verzí knihoven třetích stran je výhodné nemít soubor .pdb. Však soubory objektů pro předkompilované záhlaví jsou nezbytné během fáze propojení knihovny a pro ladění. Pokud existuje pouze typ informací (a žádný kód) do souboru .pch objektu, musíte taky použít [/Yl (Vložit referenci PCH knihovny ladění)](yl-inject-pch-reference-for-debug-library.md) možnost, která je povolena ve výchozím nastavení, při sestavování knihovny.

Zastaralá [/Gm (povolení minimálního opětovného sestavení)](gm-enable-minimal-rebuild.md) možnost není k dispozici při **/Z7** určena.

### <a name="zi"></a>/Zi

**/Zi** možnost vytváří samostatný soubor PDB, který obsahuje všechny symbolické ladicí informace pro použití s ladicím programem. Informace o ladění není zahrnutý v objektových souborů nebo spustitelného souboru, který je mezi nimi vlastně mnohem menší.

Použití **/zi** nemá vliv na optimalizaci. Ale **/zi** vyjadřuje **/debug**; viz [/Debug (Generovat ladicí informace)](debug-generate-debug-info.md) Další informace.

Pokud zadáte obě **/zi** a **/CLR**, <xref:System.Diagnostics.DebuggableAttribute> atribut není umístěn v metadatech sestavení. Pokud chcete, zadejte ho ve zdrojovém kódu. Tento atribut může ovlivnit výkon modulu runtime aplikace. Další informace o tom, jak **Debuggable** atributy ovlivňují výkon a jak můžete upravit dopad na výkon, naleznete v tématu [usnadnění bitové kopie k ladění](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

Kompilátor pojmenuje soubor PDB *projektu*.pdb. Pokud kompilujete soubor mimo projekt, kompilátor vytvoří soubor .pdb s názvem VC*x*.pdb, kde *x* zřetězení číslo hlavní verze a podverze kompilátoru verze používá. Kompilátor vloží název PDB a identifikační podpis časovým razítkem v každém souboru objektu vytvořené pomocí této možnosti, která odkazuje na umístění symbolických a číslo řádku informace o ladicím programu. Název a podpis v souboru PDB musí odpovídat spustitelný soubor symbolů, které mají být načteny v ladicím programu. Ladicí program WinDBG neodpovídající symboly můžete načíst pomocí `.symopt+0x40` příkazu. Visual Studio nemá podobné možnost načíst neodpovídající symboly.

Pokud vytvoříte knihovnu z objektů, které byly zkompilovány pomocí **/zi**, přidružený soubor PDB musí být k dispozici, když knihovně je spojena s programem. Proto při distribuci knihovny, musíte také distribuovat souboru PDB. Pokud chcete vytvořit knihovnu, která obsahuje informace o ladění bez použití souborů PDB, musíte vybrat **/Z7** možnost. Pokud použijete možnosti předkompilovaného záhlaví, ladicí informace pro předkompilované záhlaví a zbytek zdrojového kódu je umístěn v souboru PDB.

### <a name="zi"></a>/ZI

**/Zi** možnost je podobná **/zi**, vytvoří soubor .pdb ve formátu, který podporuje, ale [upravit a pokračovat](/visualstudio/debugger/edit-and-continue-visual-cpp) funkce. Pokud chcete použít ladění funkce upravit a pokračovat, musíte použít tuto možnost. Funkce upravit a pokračovat je užitečné pro produktivitu vývojářů, ale může způsobit problémy v kódu velikosti, výkon a kompilátoru shoda. Protože většina optimalizací nejsou kompatibilní s upravit a pokračovat, pomocí **/zi** zakáže všechny `#pragma optimize` příkazy ve vašem kódu. **/Zi** možnost je také kompatibilní s využitím [ &#95; &#95;řádku&#95; &#95; předdefinované makro](../../preprocessor/predefined-macros.md); kód zkompilovaný s **/zi** nelzepoužít.**&#95; &#95;Řádku&#95; &#95;** jako argumentu šablony bez typu, i když **&#95; &#95;řádku&#95; &#95;** lze použít v rozšíření makra.

**/Zi** možnost vynutí i [/Gy (povolení funkce propojení na úrovni)](gy-enable-function-level-linking.md) a [/FC (úplná cesta ze souboru zdrojového kódu v diagnostice)](fc-full-path-of-source-code-file-in-diagnostics.md) možnosti pro použití v kompilaci.

**/ Zi** není kompatibilní s [/CLR (kompilace Common Language Runtime)](clr-common-language-runtime-compilation.md).

> [!NOTE]
> **/Zi** možnost je dostupná v kompilátorech, které cílí na procesory x86 a x64 jenom; tato možnost kompilátoru není k dispozici v kompilátorech, které cílí na procesory ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Otevřít **vlastnosti konfigurace** > **C/C++** > **Obecné** stránku vlastností.

1. Upravit **formát informací o ladění** vlastnost. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)

