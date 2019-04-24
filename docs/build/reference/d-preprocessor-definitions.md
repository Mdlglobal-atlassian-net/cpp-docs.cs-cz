---
title: /D (definice preprocesoru)
ms.date: 11/04/2016
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
ms.openlocfilehash: 18bbdb980c63b3c04b432602afb2402c5e2c42e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293963"
---
# <a name="d-preprocessor-definitions"></a>/D (definice preprocesoru)

Definuje symbol předzpracování pro zdrojový soubor.

## <a name="syntax"></a>Syntaxe

```
/Dname[= | # [{string | number}] ]
```

## <a name="remarks"></a>Poznámky

Můžete použít tento symbol spolu s `#if` nebo `#ifdef` k podmíněné kompilaci zdrojového kódu. Definice symbolu zůstává v platnosti, dokud se v kódu předefinována nebo není definovaná v kódu pomocí `#undef` směrnice.

**/D** má stejný účinek jako `#define` direktiv na začátku souboru zdrojového kódu, s výjimkou, že **/D** odstraní uvozovky na příkazovém řádku a `#define` je zachová.

K tomuto symbolu je standardně přidružena hodnota 1. Například **/D** `name` je ekvivalentní **/D**`name`**= 1**. V příkladu na konci tohoto článku, definice **testovací** se zobrazí pro tisk `1`.

Kompilace s použitím **/D** `name` **=** způsobí, že symbol nebude mít žádnou přidruženou hodnotu. Ačkoli lze tento symbol stále použít k podmíněné kompilaci kódu, nijak se nevyhodnotí. V příkladu, pokud kompilujete pomocí **/DTEST =**, dojde k chybě. Toto chování se podobá použití `#define` s nebo bez hodnoty.

Tento příkaz definuje symbol DEBUG v souboru TEST.c:

**CL /DDEBUG TESTU. C**

Tento příkaz odebere všechny výskyty klíčového slova `__far` v souboru TEST.c:

**CL /D__far=  TEST.C**

**CL** nelze nastavit proměnné prostředí na řetězec, který obsahuje rovnítko. Chcete-li použít **/D** spolu s **CL** prostředí proměnné, je nutné zadat znak čísla místo rovnítka:

```
SET CL=/DTEST#0
```

Při definici symbolu předzpracování na příkazovém řádku pamatujte jak na pravidla analýzy kompilátoru, tak na pravidla analýzy prostředí. Například, chcete-li definovat symbol předzpracování znak procenta (%) ve svém programu zadejte znak procenta dvou znaků (%) na příkazovém řádku: Pokud zadáte pouze jeden, jsou vydávány chybu analýzy.

```
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. V levém podokně vyberte **vlastnosti konfigurace**, **C/C++**, **preprocesor**.

1. V pravém podokně klikněte v pravém sloupci **Definice preprocesoru** vlastnost, otevřete rozevírací nabídku a zvolte **upravit**.

1. V **Definice preprocesoru** dialogovém okně přidejte (jednu na každý řádek), upravit nebo odstranit jednu nebo víc definic. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.

## <a name="example"></a>Příklad

```
// cpp_D_compiler_option.cpp
// compile with: /DTEST
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

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/U, /u (nedefinované symboly)](u-u-undefine-symbols.md)<br/>
[#undef – direktiva (C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br/>
[#define – direktiva (C++)](../../preprocessor/hash-define-directive-c-cpp.md)
