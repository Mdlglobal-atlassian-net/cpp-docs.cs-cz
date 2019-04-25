---
title: /GL (celková optimalizace programu)
ms.date: 11/04/2016
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: 6251209dac74a504bb0635f0c544c39935090a42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292130"
---
# <a name="gl-whole-program-optimization"></a>/GL (celková optimalizace programu)

Povolí optimalizaci celého programu.

## <a name="syntax"></a>Syntaxe

```
/GL[-]
```

## <a name="remarks"></a>Poznámky

Optimalizace celého programu umožňuje kompilátoru provést optimalizace s informacemi o na všechny moduly v programu. Bez optimalizace celého programu optimalizace provádějí základě modulu (kompilace).

Optimalizace celého programu je vypnuto ve výchozím nastavení a musí být explicitně povolené. Ale je také možné explicitně zakázat pomocí **/GL-**.

Informace o všech modulů kompilátor může:

- Optimalizujte využití registrů napříč hranicemi funkce.

- Proveďte úlohu lepší sledování změny globálních dat, umožňuje snížení počtu zatížení a úložiště.

- Proveďte úlohu lepší sledování možné sady položek upravil ukazatel přistoupit přes ukazatel, snížení počtu zatížení a úložiště.

- Vložené funkce v modulu i v případě, že funkce je definována v jiném modulu.

soubory .obj vytvořeného s **/GL** nebudou mít k dispozici takových nástrojů linkeru jako [EDITBIN](editbin-reference.md) a [DUMPBIN](dumpbin-reference.md).

Pokud kompilujete aplikace s **/GL** a [/c](c-compile-without-linking.md), by měl parametru/LTCG – možnost linkeru použijete k vytvoření výstupního souboru.

[/ Zi](z7-zi-zi-debug-information-format.md) nelze použít s   **/GL.**

Formát souborů vytvořenými pomocí **/GL** v aktuální verzi nemusí být čitelný v dalších verzích Visual C++. Neměli dodávat .lib soubor sestává z soubory .obj, které byly vytvořeny s **/GL** Pokud se nechcete dodávat kopie .lib soubor pro všechny verze sady Visual C++ očekáváte, že uživatelé používali, teď a v budoucnu.

soubory .obj vytvořeného s **/GL** a neměl by se předkompilované hlavičkové soubory .lib soubor sestavení, pokud bude propojena .lib soubor ve stejném počítači, který vytvořil **/GL** souboru .obj. Informace v souboru .obj předkompilovaného hlavičkového souboru bude potřeba v době spojení.

Další informace o dostupných s optimalizací a omezení optimalizace celého programu, najdete v článku [parametru/LTCG](ltcg-link-time-code-generation.md).  **/GL** také vytvoří profil s asistencí optimalizace k dispozici; viz parametru/LTCG.  Při kompilaci pro optimalizace a pokud chcete, aby funkce řazení z optimalizace na základě profilu na základě profilu, je nutné kompilovat s [/Gy](gy-enable-function-level-linking.md) nebo možnosti kompilátoru, který by naznačoval /Gy.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Zobrazit [parametru/LTCG (generování kódu při propojování odkaz)](ltcg-link-time-code-generation.md) informace o tom, jak určit **/GL** ve vývojovém prostředí.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
