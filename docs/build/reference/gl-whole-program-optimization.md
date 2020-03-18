---
title: /GL (celková optimalizace programu)
ms.date: 11/04/2016
f1_keywords:
- /gl
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: 875865a32dcb80cb8a6d8fa53646260f3d9413a5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439651"
---
# <a name="gl-whole-program-optimization"></a>/GL (celková optimalizace programu)

Povoluje optimalizaci celého programu.

## <a name="syntax"></a>Syntaxe

```
/GL[-]
```

## <a name="remarks"></a>Poznámky

Optimalizace celého programu umožňuje kompilátoru provádět optimalizace s informacemi o všech modulech v programu. Bez optimalizace celého programu se optimalizace provádějí na jednotlivých modulech (kompilantu).

Optimalizace celého programu je ve výchozím nastavení vypnutá a je nutné ji explicitně povolit. Je ale také možné ji explicitně zakázat pomocí **/GL-** .

S informacemi o všech modulech může kompilátor:

- Optimalizujte použití registrů napříč hranicemi funkcí.

- Udělejte lepší úlohu sledování změn globálních dat, což umožňuje snížit počet načtených a uložených úložišť.

- Udělejte lepší úlohu sledování možných množin položek upravených pomocí ukazatele myši, čímž se sníží počet načtených a uložených úložišť.

- Vložení funkce v modulu i v případě, že je funkce definovaná v jiném modulu.

soubory. obj vytvořené s **/GL** nebudou k dispozici pro tyto nástroje linkeru jako [nástroje EDITBIN](editbin-reference.md) a [DUMPBIN](dumpbin-reference.md).

Pokud kompilujete program s **/GL** a [/c](c-compile-without-linking.md), měli byste použít možnost linkeru/LTCG k vytvoření výstupního souboru.

[/Zi](z7-zi-zi-debug-information-format.md) nelze použít s **/GL**

Formát souborů vytvořených pomocí **/GL** v aktuální verzi nemusí být čitelný v následujících verzích vizuálu C++. Neměli byste dodávat soubor. lib skládající se ze souborů. obj, které byly vytvořeny pomocí **/GL** , pokud nejste ochotni dodávat kopie souboru. lib pro všechny verze vizuálu C++ , které očekáváte, že uživatelé budou používat, a to v budoucnu.

soubory. obj vytvořené pomocí **/GL** a předkompilované hlavičkové soubory by neměly být použity k sestavení souboru. lib, pokud soubor. lib nebude propojen ve stejném počítači, který vytvořil soubor **/GL** . obj. Informace ze souboru předkompilovaného hlavičkového souboru. obj budou potřeba v době propojování.

Další informace o dostupných optimalizacích a omezeních celé optimalizace programu najdete v tématu [/LTCG](ltcg-link-time-code-generation.md).  **/GL** také zpřístupňuje optimalizaci na základě profilu. viz/LTCG.  Při kompilaci pro optimalizace na základě profilu a v případě, že chcete pořadí funkcí z optimalizace na základě profilu, je nutné kompilovat pomocí [/Gy](gy-enable-function-level-linking.md) nebo možnosti kompilátoru, která implikuje/Gy.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Informace o tom, jak zadat **/GL** ve vývojovém prostředí, najdete v tématu [/LTCG (generování kódu při propojování)](ltcg-link-time-code-generation.md) .

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
