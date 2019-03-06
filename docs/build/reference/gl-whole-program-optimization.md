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
ms.openlocfilehash: b0aabdc1a2fb86479a165ae9559372316bd02260
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420671"
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

soubory .obj vytvořeného s **/GL** nebudou mít k dispozici takových nástrojů linkeru jako [EDITBIN](../../build/reference/editbin-reference.md) a [DUMPBIN](../../build/reference/dumpbin-reference.md).

Pokud kompilujete aplikace s **/GL** a [/c](../../build/reference/c-compile-without-linking.md), by měl parametru/LTCG – možnost linkeru použijete k vytvoření výstupního souboru.

[/ Zi](../../build/reference/z7-zi-zi-debug-information-format.md) nelze použít s   **/GL.**

Formát souborů vytvořenými pomocí **/GL** v aktuální verzi nemusí být čitelný v dalších verzích Visual C++. Neměli dodávat .lib soubor sestává z soubory .obj, které byly vytvořeny s **/GL** Pokud se nechcete dodávat kopie .lib soubor pro všechny verze sady Visual C++ očekáváte, že uživatelé používali, teď a v budoucnu.

soubory .obj vytvořeného s **/GL** a neměl by se předkompilované hlavičkové soubory .lib soubor sestavení, pokud bude propojena .lib soubor ve stejném počítači, který vytvořil **/GL** souboru .obj. Informace v souboru .obj předkompilovaného hlavičkového souboru bude potřeba v době spojení.

Další informace o dostupných s optimalizací a omezení optimalizace celého programu, najdete v článku [parametru/LTCG](../../build/reference/ltcg-link-time-code-generation.md).  **/GL** také vytvoří profil s asistencí optimalizace k dispozici; viz parametru/LTCG.  Při kompilaci pro optimalizace a pokud chcete, aby funkce řazení z optimalizace na základě profilu na základě profilu, je nutné kompilovat s [/Gy](../../build/reference/gy-enable-function-level-linking.md) nebo možnosti kompilátoru, který by naznačoval /Gy.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Zobrazit [parametru/LTCG (generování kódu při propojování odkaz)](../../build/reference/ltcg-link-time-code-generation.md) informace o tom, jak určit **/GL** ve vývojovém prostředí.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
