---
title: -D (Definice preprocesoru) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08812cdd0a4ffb27b387cce8cfb26e72ef80770a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="d-preprocessor-definitions"></a>/D (definice preprocesoru)
Definuje symbol předzpracování pro zdrojový soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Dname[= | # [{string | number}] ]  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít tento symbol společně s `#if` nebo `#ifdef` Podmíněná kompilace zdrojového kódu. Definice symbolu zůstává v platnosti, dokud je předefinovat v kódu nebo není definována v kódu pomocí `#undef` – direktiva.  
  
 **/D** má stejně, jako `#define` direktivy na začátku souboru zdrojového kódu, vyjma toho, že **/D** odstraní uvozovek na příkazovém řádku a `#define` je uloží.  
  
 K tomuto symbolu je standardně přidružena hodnota 1. Například **/D** `name` je ekvivalentní **/D**`name`**= 1**. V příkladu na konci tohoto článku, definice **TEST** se zobrazí tisku `1`.  
  
 Kompilování pomocí **/D** `name`  **=**  způsobí, že symbol, který má mít žádné přidružené hodnoty. Ačkoli lze tento symbol stále použít k podmíněné kompilaci kódu, nijak se nevyhodnotí. V příkladu, pokud zkompilujete pomocí **/DTEST =**, dojde k chybě. Toto chování se podobá použití `#define` s nebo bez hodnoty.  
  
 Tento příkaz definuje symbol DEBUG v souboru TEST.c:  
  
 **CL /DDEBUG TEST. C**  
  
 Tento příkaz odebere všechny výskyty klíčového slova `__far` v TEST.c:  
  
 **CL /D__far = TEST. C**  
  
 **CL** proměnnou prostředí nelze nastavit na řetězec, který obsahuje znaménko rovná se. Chcete-li použít **/D** společně s **CL** prostředí proměnné, je nutné zadat znaménko čísla místo znaménku rovná:  
  
```  
SET CL=/DTEST#0  
```  
  
 Při definici symbolu předzpracování na příkazovém řádku pamatujte jak na pravidla analýzy kompilátoru, tak na pravidla analýzy prostředí. Chcete-li například v programu definovat jako symbol předzpracování znak procenta (%), zadejte na příkazovém řádku dva znaky procenta (%%); pokud zadáte pouze jeden, dojde k chybě analýzy.  
  
```  
CL /DTEST=%% TEST.C  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  V levém podokně vyberte **vlastnosti konfigurace**, **C/C++**, **preprocesor**.  
  
3.  V pravém podokně klikněte v pravém sloupci **Definice preprocesoru** vlastnost, otevřete rozevírací nabídku a vyberte **upravit**.  
  
4.  V **Definice preprocesoru** dialogové okno, přidat (jeden na každý řádek), upravit nebo odstranit jednu nebo víc definic. Zvolte **OK** uložte provedené změny.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.  
  
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
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [/ U, /u (nedefinované symboly)](../../build/reference/u-u-undefine-symbols.md)   
 [#undef – direktiva (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)   
 [#define – direktiva (C++)](../../preprocessor/hash-define-directive-c-cpp.md)