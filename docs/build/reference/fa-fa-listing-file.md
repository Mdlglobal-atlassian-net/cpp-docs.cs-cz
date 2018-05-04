---
title: / FA, /Fa (soubor seznamu) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
dev_langs:
- C++
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1840d2f2ff7d968fdcc19e2013a89af9cec32d24
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fa-fa-listing-file"></a>/FA, /Fa (soubor seznamu)
Vytvoří seznam obsahující assembleru kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
> **/FA**[**c**\][**s**\][**u**]  
> **/Fa**_pathname_  
  
## <a name="remarks"></a>Poznámky  
`/FA` – Možnost kompilátoru generuje soubor assembleru výpis pro každou jednotku překlad v kompilaci, která obvykle odpovídá jazyka C nebo C++ zdrojový soubor. Ve výchozím nastavení je pouze assembleru součástí výpis souboru, který je zakódován jako ANSI. Volitelné `c`, `s`, a `u` argumenty, které mají `/FA` řízení jestli počítač kódu nebo zdrojového kódu se výstup společně s assembleru výpis a jestli seznam zakódován pomocí kódování UTF-8.  
  
Ve výchozím nastavení každý soubor seznamu získá základní stejný název jako zdrojový soubor a má příponu .asm. Když je zahrnut kód počítač pomocí `c` možnost, soubor seznamu má příponu .cod. Můžete změnit název a příponu výpis souboru a adresáře, kde byl vytvořen pomocí `/Fa` možnost.  

### <a name="fa-arguments"></a>/FA argumenty  
žádná  
Pouze assembleru jazyk je uvedena na seznamu.  
  
`c`  
Volitelné. Zahrnuje zkompilovaný kód v ukázce.  
  
`s`  
Volitelné. Obsahuje zdrojový kód v ukázce.  
  
`u` Volitelný parametr. Kóduje soubor seznamu ve formátu UTF-8 a zahrnuje značku pořadí bajtů. Ve výchozím nastavení je soubor kódovaný jako ANSI. Použití `u` vytvořit soubor seznamu, který se zobrazí správně v libovolný systém, nebo pokud používáte Unicode zdrojové soubory kódu jako vstup pro kompilátor.  
  
Pokud oba `s` a `u` jsou zadané a pokud zdroj kódu soubor používá kódování Unicode jiného, než UTF-8, pak řádků kódu v souboru .asm nemusí být zobrazeny správně.  
  
### <a name="fa-argument"></a>/Fa argument  
žádná  
Jeden *zdroj*.asm soubor se vytvoří pro každou souboru zdrojového kódu v kompilace.  
  
*Název souboru* výpis soubor s názvem *filename*.asm je umístěn v aktuálním adresáři. To je platná pouze při kompilaci souboru jednoho zdrojového kódu.  
  
*filename.Extension*  
Výpis soubor s názvem *filename.extension* je umístěn v aktuálním adresáři. To je platná pouze při kompilaci souboru jednoho zdrojového kódu.  
  
*Adresář*\  
Jeden *source_file*.asm soubor je vytvořen a umístěny v zadané *directory* pro každého souboru zdrojového kódu v kompilace. Všimněte si požadované koncové zpětné lomítko. Jsou povolené jenom cesty na aktuálním disku.  
  
*adresář*\\*filename* výpis soubor s názvem *filename*.asm je umístěn v zadané *directory*. To je platná pouze při kompilaci souboru jednoho zdrojového kódu.  
  
*adresář*\\*filename.extension*  
Výpis soubor s názvem *filename.extension* je umístěn v zadané *directory*. To je platná pouze při kompilaci souboru jednoho zdrojového kódu.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Otevřete **C/C++** složky a vyberte **výstupní soubory** stránku vlastností.  
  
3.  Změnit **assembleru výstup** vlastnost nastavit `/FAc` a `/FAs` možnosti assembleru, počítače a zdrojový kód. Změnit **použití kódu Unicode pro výpis assembleru** vlastnost nastavit `/FAu` možnost pro výstup ANSI nebo UTF-8. Změnit **umístění seznamu ASM** nastavit `/Fa` možnost pro výpis název souboru a umístění.  
  
Všimněte si, jak nastavení **assembleru výstup** a **použití kódu Unicode pro výpis assembleru** může způsobit vlastnosti [příkazového řádku D9025 upozornění](../../error-messages/tool-errors/command-line-warning-d9025.md). Kombinování tyto možnosti v prostředí IDE, použijte **další možnosti** pole **příkazového řádku** vlastnost stránky místo.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> nebo <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>. Chcete-li určit `/FAu`, najdete v části <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="example"></a>Příklad  
Následující příkaz vytvoří kombinovaný zdroj a výpis kódu počítač s názvem HELLO.cod:  
  
```  
CL /FAcs HELLO.CPP  
```  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Určení názvu cesty](../../build/reference/specifying-the-pathname.md)