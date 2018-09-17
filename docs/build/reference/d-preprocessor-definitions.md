---
title: -D (Definice preprocesoru) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
dev_langs:
- C++
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19da0c8e29a27734b23a01a1b2d3ffaa64a7fe05
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713790"
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

**CL /D__far = TEST. C**

**CL** nelze nastavit proměnné prostředí na řetězec, který obsahuje rovnítko. Chcete-li použít **/D** spolu s **CL** prostředí proměnné, je nutné zadat znak čísla místo rovnítka:

```
SET CL=/DTEST#0
```

Při definici symbolu předzpracování na příkazovém řádku pamatujte jak na pravidla analýzy kompilátoru, tak na pravidla analýzy prostředí. Chcete-li například v programu definovat jako symbol předzpracování znak procenta (%), zadejte na příkazovém řádku dva znaky procenta (%%); pokud zadáte pouze jeden, dojde k chybě analýzy.

```
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. V levém podokně vyberte **vlastnosti konfigurace**, **C/C++**, **preprocesor**.

1. V pravém podokně klikněte v pravém sloupci **Definice preprocesoru** vlastnost, otevřete rozevírací nabídku a zvolte **upravit**.

1. V **Definice preprocesoru** dialogovém okně přidejte (jednu na každý řádek), upravit nebo odstranit jednu nebo víc definic. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.

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

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/ U, /u (nedefinované symboly)](../../build/reference/u-u-undefine-symbols.md)
[#undef – direktiva (C++)](../../preprocessor/hash-undef-directive-c-cpp.md)
[#define – direktiva (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)