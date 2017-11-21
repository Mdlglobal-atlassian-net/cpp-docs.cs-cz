---
title: "-Fx (sloučení vloženého kódu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExpandAttributedSource
- /Fx
- VC.Project.VCCLCompilerTool.ExpandAttributedSource
dev_langs: C++
helpviewer_keywords:
- Fx compiler option [C++]
- -Fx compiler option [C++]
- injected code
- merging injected code
- /Fx compiler option [C++]
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 344d9ded0cdb77abfc2fa53ab4180f2e484b7dc9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fx-merge-injected-code"></a>/Fx (sloučení vloženého kódu)
Vytvoří kopii každý zdrojový soubor s vloženým kódem sloučeny do zdroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Fx  
```  
  
## <a name="remarks"></a>Poznámky  
 K rozlišení sloučené zdrojového souboru z původní zdrojový soubor **/Fx** přidá rozšíření .mrg mezi název souboru a příponu souboru. Například soubor s názvem MyCode.cpp obsahující kódu s atributy a vytvořené s **/Fx** vytvoří soubor s názvem MyCode.mrg.cpp obsahující následující kód:  
  
```  
//+++ Start Injected Code  
[no_injected_text(true)];      // Suppress injected text, it has   
                               // already been injected  
#pragma warning(disable: 4543) // Suppress warnings about skipping   
                               // injected text  
#pragma warning(disable: 4199) // Suppress warnings from attribute   
                               // providers  
//--- End Injected Code  
```  
  
 Do souboru .mrg se kód, který byl vložit z důvodu atribut oddělený následujícím způsobem:  
  
```  
//+++ Start Injected Code  
...  
//--- End Injected Code  
```  
  
 [No_injected_text –](../../windows/no-injected-text.md) atribut se vloží do souboru .mrg, což umožňuje pro kompilaci souboru .mrg bez textu se reinjected.  
  
 Je třeba si uvědomit, že má být reprezentace zdrojového kódu vloženy kompilátor .mrg zdrojový soubor. Soubor .mrg nemusí kompilovat nebo spustit přesně jako původní zdrojový soubor.  
  
 Makra nejsou v souboru .mrg rozšířit.  
  
 Pokud váš program obsahuje soubor hlaviček, který používá vložený kód **/Fx** generuje. soubor mrg.h této hlavičky. **/FX** nezahrnuje není sloučení souborů, které nepoužívají vloženého kódu.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **výstupní soubory** stránku vlastností.  
  
4.  Změnit **rozbalte s atributy zdroje** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)