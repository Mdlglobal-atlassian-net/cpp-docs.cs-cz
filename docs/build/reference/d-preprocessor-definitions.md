---
title: /D (definice preprocesoru)
ms.date: 09/18/2019
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
ms.openlocfilehash: b10d611d38508f5696dd3b72fb8458e9b61082c8
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230401"
---
# <a name="d-preprocessor-definitions"></a>/D (definice preprocesoru)

Definuje symbol předzpracování pro zdrojový soubor.

## <a name="syntax"></a>Syntaxe

> **/D** ]název | [`=` [{ | řetězec*číslo* }]] \`#` \[
> **/D** \[ ]název [[{`=` řetězecčíslo | }]] |  `"``#``"`

## <a name="remarks"></a>Poznámky

Tento symbol můžete použít spolu s `#if` nebo `#ifdef` ke kompilaci zdrojového kódu podmíněně. Definice symbolu zůstane v platnosti, dokud není znovu definována v kódu nebo není definována v `#undef` direktivě Code.

**/D** má stejný účinek jako `#define` direktiva na začátku souboru zdrojového kódu. Rozdíl je v tom, že na příkazovém řádku **/d** odstraní uvozovky a `#define` direktivu zachovává. Můžete mít prázdné znaky mezi **parametrem/d** a symbolem. Mezi symbolem a znaménkem rovnosti nebo mezi rovnítkem a libovolnou přiřazenou hodnotou nesmí být mezera.

K tomuto symbolu je standardně přidružena hodnota 1. Například `/D name` je ekvivalentem k `/D name=1`. V příkladu na konci tohoto článku se zobrazí definice `TEST` pro tisk. `1`

Při kompilaci pomocí `/D name=` dojde k tomu, že *název* symbolu nemá přidruženou hodnotu. Ačkoli lze tento symbol stále použít k podmíněné kompilaci kódu, nijak se nevyhodnotí. V příkladu, pokud kompilujete pomocí `/DTEST=`, dojde k chybě. Toto chování `#define` se podobá použití s hodnotou nebo bez ní.

Možnost **/d** nepodporuje definice maker podobných funkcím. Chcete-li vložit definice, které nelze definovat v příkazovém řádku, zvažte možnost kompilátoru [/Fi (název vynuceného souboru)](fi-name-forced-include-file.md) .

Chcete-li definovat další symboly, můžete použít příkaz **/d** několikrát na příkazovém řádku. Je-li stejný symbol definován více než jednou, je použita poslední definice.

Tento příkaz definuje symbol DEBUG v souboru TEST.c:

```cmd
CL /DDEBUG TEST.C
```

Tento příkaz odebere všechny výskyty klíčového slova `__far` v testu. c:

```cmd
CL /D __far= TEST.C
```

Proměnná prostředí **CL** nemůže být nastavena na řetězec, který obsahuje rovnítko. Chcete-li použít **/d** společně s proměnnou prostředí **CL** , je nutné zadat znak čísla (`#`) namísto znaménka rovná se:

```cmd
SET CL=/DTEST#0
```

Při definici symbolu předzpracování na příkazovém řádku pamatujte jak na pravidla analýzy kompilátoru, tak na pravidla analýzy prostředí. Například chcete-li v programu definovat symbol předběžného zpracování znaku procenta`%`(), zadejte do příkazového řádku dva znaky procenta (`%%`). Pokud zadáte pouze jeden, bude vyvolána chyba analýzy.

```cmd
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. V levém podokně vyberte možnost **Vlastnosti konfigurace**, **C/C++** , **preprocesor**.

1. V pravém podokně v pravém sloupci vlastnosti **Definice preprocesoru** otevřete rozevírací nabídku a vyberte možnost **Upravit**.

1. V dialogovém okně **Definice preprocesoru** přidejte (jeden na řádek), upravte nebo odstraňte jednu nebo více definic. Kliknutím na **tlačítko OK** uložte změny.

   V definicích, které tady zadáte, nemusíte vkládat předponu možnosti/D. Na stránce vlastností jsou definice odděleny středníky (`;`).

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.

## <a name="example"></a>Příklad

```cpp
// cpp_D_compiler_option.cpp
// compile with: cl /EHsc /DTEST cpp_D_compiler_option.cpp
#include <stdio.h>

int main( )
{
#ifdef TEST
    printf_s("TEST defined %d\n", TEST);
#else
    printf_s("TEST not defined\n");
#endif
}
```

```Output
TEST defined 1
```

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)\
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)\
[/FI (soubor vynuceného zahrnutí názvu)](fi-name-forced-include-file.md)\
[/U,/u (nedefinované symboly)](u-u-undefine-symbols.md)\
[#undef direktiva (CC++/)](../../preprocessor/hash-undef-directive-c-cpp.md)\
[#define – direktiva (C++)](../../preprocessor/hash-define-directive-c-cpp.md)
