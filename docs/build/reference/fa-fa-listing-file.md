---
title: / FA, /Fa (soubor seznamu) | Dokumentace Microsoftu
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
ms.openlocfilehash: a4014c58a7e562aa632dba62dcac04c835352cbf
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101726"
---
# <a name="fa-fa-listing-file"></a>/FA, /Fa (soubor seznamu)

Vytvoří soubor výpisu obsahující kódu assembleru.

## <a name="syntax"></a>Syntaxe

> **/FA**[**c**\][**s**\][**u**] **/Fa**_cesta_

## <a name="remarks"></a>Poznámky

**/FA** – možnost kompilátoru soubor výpisu assembler generuje pro každou jednotku převodu při kompilaci, která obvykle odpovídá zdrojový soubor jazyka C nebo C++. Ve výchozím nastavení pouze assembler je součástí souboru výpisu, který je zakódován jako ANSI. Volitelný **c**, **s**, a **u** argumenty **/FA** ovládacího prvku určuje, zda počítač kódu nebo zdrojový kód se výstup spolu s assembler výpis, a určuje, zda je seznam kódováním UTF-8.

Ve výchozím nastavení každý soubor výpisu získá stejný základní název zdrojového souboru a má příponu .asm. Když je součástí pomocí strojového kódu **c** možnost, soubor výpisu má příponu COD. Můžete změnit název a příponu souboru výpisu a adresář, ve kterém je vytvořená pomocí **/Fa** možnost.

### <a name="fa-arguments"></a>/FA argumenty

žádná  
Ve výpisu je zahrnuta pouze assembleru jazyka.

**c**  
Volitelné. Zahrnuje strojového kódu v ukázce.

**s**  
Volitelné. Obsahuje zdrojový kód v ukázce.

**u**  
Volitelné. Zakóduje soubor výpisu ve formátu UTF-8 a obsahuje značku pořadí bajtů. Ve výchozím souboru kódováním ANSI. Použití `u` vytvoření souboru výpisu, který se zobrazí správně v libovolném systému, nebo pokud používáte Unicode souborů zdrojového kódu jako vstup do kompilátoru.

Pokud mají oba **s** a **u** jsou určené a pokud zdroj kód soubor používá kódování Unicode jiné než UTF-8, pak řádky kódu do souboru .asm nemusí být zobrazeny správně.

### <a name="fa-argument"></a>/Fa argument

žádná  
Jeden *zdroj*.asm soubor se vytvoří pro každý soubor zdrojového kódu dané kompilace.

*Název souboru*  
Soubor výpisu s názvem *filename*asm je umístěn v aktuálním adresáři. To platí jenom při kompilaci jeden zdrojový soubor kódu.

*filename.Extension*  
Soubor výpisu s názvem *filename.extension* je umístěn v aktuálním adresáři. To platí jenom při kompilaci jeden zdrojový soubor kódu.

*Adresář*__\\__  
Jeden *$source_file*.asm soubor je vytvořen a umístí v zadaném *directory* pro každý soubor zdrojového kódu dané kompilace. Poznámka: vyžaduje lomítkem. Jsou povolené jenom cesty na aktuálním disku.

*adresář*__\\__*název souboru*  
Soubor výpisu s názvem *filename*asm je umístěn v zadaném *directory*. To platí jenom při kompilaci jeden zdrojový soubor kódu.

*adresář*__\\__*filename.extension*  
Soubor výpisu s názvem *filename.extension* je umístěn v zadaném *directory*. To platí jenom při kompilaci jeden zdrojový soubor kódu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

2. Vyberte **vlastnosti konfigurace** > **C/C++** > **výstupní soubory** stránku vlastností.

3. Upravit **výstup assembleru** vlastnosti chcete nastavit **/FAC** a **/FAS** možnosti pro assembler, počítače a zdrojový kód. Upravit **použijte kódování Unicode pro výpis Assembler** vlastnosti chcete nastavit **/fau vytvořte** možnost pro výstup ANSI nebo UTF-8. Upravit **umístění seznamu ASM** nastavit **/Fa** možnost pro výpis název a umístění souboru.

Poznámka: Toto nastavení i **výstup assembleru** a **použijte kódování Unicode pro výpis Assembler** vlastnosti může způsobit [příkazového řádku D9025 upozornění](../../error-messages/tool-errors/command-line-warning-d9025.md). Chcete-li sloučit tyto možnosti v integrovaném vývojovém prostředí, použijte **další možnosti** pole v **příkazového řádku** místo toho stránce vlastností.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> nebo <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>. Chcete-li určit **/fau vytvořte**, naleznete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Příklad
Následující příkaz vytvoří kombinované zdroje a výpis strojového kódu s názvem HELLO.cod:

```cmd
CL /FAcs HELLO.CPP
```

## <a name="see-also"></a>Viz také

[Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
[Možnosti kompilátoru](../../build/reference/compiler-options.md)   
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
[Určení názvu cesty](../../build/reference/specifying-the-pathname.md)