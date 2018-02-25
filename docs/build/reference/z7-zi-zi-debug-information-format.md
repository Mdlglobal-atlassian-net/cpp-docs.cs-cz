---
title: "-Z7,. - Zi, - ZI (formát ladicích informací) | Microsoft Docs"
ms.custom: 
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6e3de89c5336cda98960b67b80932df8f67d183
ms.sourcegitcommit: 2cca90d965f76ebf1d741ab901693a15d5b8a4df
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/24/2018
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (formát ladicích informací)

Určuje typ ladění informace vytvořené k aplikaci a zda tyto informace jsou uchovávány v souborech objekt nebo v databázi (PDB) soubor programu.

## <a name="syntax"></a>Syntaxe

> **/Z**{**7**|**i**|**I**}  

## <a name="remarks"></a>Poznámky

Možnosti ladění informace o formátu jsou popsány v následujících částech.  
  
### <a name="none"></a>Žádné

Ve výchozím nastavení Pokud není zadána žádná možnost formátu informace ladění, kompilátor vytvoří žádné informace o ladění, takže kompilace je rychlejší.  
  
### <a name="z7"></a>/Z7

**/Z7** možnost vytváří *souboru objektu*, soubor, který má příponu .obj obsahující úplné symbolické ladicí informace pro použití s ladicím programem. Symbolické ladicí informace obsahuje názvy a typy proměnných, a také funkce a čísla řádků. Ne *soubor PDB*, vytvoří soubor s příponou PDB.

Pro distributorů knihoven jiných výrobců je výhodné nemá soubor PDB. Soubory objektů pro předkompilované hlavičky jsou však nutné během fáze propojení a pro ladění. Pokud je pouze soubory objektu zadejte informace (a žádný kód), musíte také použít [/Yl (Vložit referenci PCH knihovny ladění)](../../build/reference/yl-inject-pch-reference-for-debug-library.md) možnost, která je ve výchozím nastavení povolené.

### <a name="zi"></a>/Zi

**/Zi** možnost vytvoří soubor PDB, který obsahuje informace o typu a symbolické ladicí informace pro použití s ladicím programem. Symbolické ladicí informace obsahuje názvy a typy proměnných, a také funkce a čísla řádků.

Použití **/Zi** nemá vliv na optimalizace. Ale **/Zi** implikují **/debug**; najdete v části [/Debug (Generovat ladicí informace)](../../build/reference/debug-generate-debug-info.md) Další informace.

Když **/Zi** není zadaný, informace o typu je umístěn v souboru PDB a ne v souboru objektu.

Můžete použít [/Gm (povolit minimální sestavení)](../../build/reference/gm-enable-minimal-rebuild.md) společně s **/Zi**, ale **/Gm** není k dispozici při **/Z7** je zadán.

Pokud zadáte oba **/Zi** a **/CLR**, <xref:System.Diagnostics.DebuggableAttribute> atribut není umístěn v metadatech sestavení. Pokud ho chcete, zadejte ji ve zdrojovém kódu. Tento atribut může ovlivnit výkon modulu runtime aplikace. Další informace o tom, jak **Debuggable** atribut ovlivňuje výkon a jak můžete upravit dopad na výkon, najdete v části [snadněji bitové kopie pro ladění](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

### <a name="zi"></a>/ZI

**/ZI** možnost vytvoří soubor PDB ve formátu, který podporuje [upravit a pokračovat](/visualstudio/debugger/edit-and-continue-visual-cpp) funkce. Pokud chcete použít, úpravy a pokračujete v ladění, musíte použít tuto možnost. Funkce upravit a pokračovat je užitečné pro vývojáře produktivitu, ale může způsobit problémy v shoda s kompilátorem prostředí, kód velikost a výkon. Protože většina optimalizace nejsou kompatibilní s upravit a pokračovat, pomocí **/ZI** zakáže všechny `#pragma optimize` příkazů v kódu. **/ZI** možnost je také kompatibilní s použitím [&#95; &#95; Řádek &#95; &#95; Předdefinovaná makra](../../preprocessor/predefined-macros.md). Kód kompilovat s **/ZI** nelze použít **&#95; &#95; Řádek &#95; &#95;**  jako šablonu jiný typ argumentu, i když **&#95; &#95; Řádek &#95; &#95;**  je možné použít v makro rozšíření.

**/ZI** možnost vynutí i [/Gy (povolení propojení na úrovni funkcí)](../../build/reference/gy-enable-function-level-linking.md) a [/FC (úplná cesta z souboru zdrojového kódu v diagnostice)](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md) možnosti pro použití v kompilaci.

**/ZI** není kompatibilní s [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
> **/ZI** možnost je dostupná v kompilátory cílení x86 a x64 procesory jenom; tento – možnost kompilátoru není k dispozici v kompilátory cílení procesory ARM.

Kompilátor názvy soubor PDB *projektu*pdb. Pokud je soubor mimo projekt, kompilátor vytvoří soubor PDB s názvem VC*x*0.pdb, kde *x* je hlavní číslo verze verze sady Visual Studio používá. Kompilátor vloží název PDB do každého souboru .obj vytvořené pomocí této možnosti odkazující na umístění informací symbolický a číslo řádku ladicího programu. Pokud použijete tuto možnost, vaše soubory .obj jsou menší, protože ladicí informace jsou uloženy v souboru PDB místo soubory .obj.

Pokud objekty, které byly zkompilovány použití této možnosti vytvoříte knihovny, musí být na soubor .pdb přidružené k dispozici knihovny propojen s program. Proto pokud distribuujete knihovny, je nutné distribuovat PDB.

Pokud chcete vytvořit knihovnu, která obsahuje informace o ladění bez použití soubory PDB, je nutné vybrat do kompilátoru jazyka C kompatibilní 7.0 (**/Z7**) možnost. Pokud použijete možnosti předkompilovaných hlaviček, ladicí informace pro předkompilované hlavičky a zbytek zdrojový kód je umístěn v souboru PDB. **/Yd** možnost je ignorována, pokud je zadána možnost databáze programu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Otevřete **vlastnosti konfigurace** > **C/C++** > **Obecné** stránku vlastností.

1. Změnit **Debug Information Format** vlastnost. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  

