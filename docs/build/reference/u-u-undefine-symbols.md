---
title: -U, -u (nedefinované symboly) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
dev_langs:
- C++
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 897ca229ec7312812b6f2bd2991bf519e98c836c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="u-u-undefine-symbols"></a>/U, /u (nedefinované symboly)
**/U** – možnost kompilátoru undefines zadaný symbol preprocesoru. **/U** – možnost kompilátoru undefines symboly specifické pro společnost Microsoft, které definuje kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/U[ ]symbol  
/u  
```  
  
## <a name="arguments"></a>Arguments  
 `symbol`  
 Symbol preprocesoru k nedefinované.  
  
## <a name="remarks"></a>Poznámky  
 Ani **/U** nebo **/u** možnost můžete nedefinované symbol vytvořili pomocí **#define** – direktiva.  
  
 **/U** možnost můžete nedefinované symbol, který byl předtím definovaný s použitím **/D** možnost.  
  
 Ve výchozím nastavení kompilátor definuje následující symboly specifické pro společnost Microsoft.  
  
|Symbol|Funkce|  
|------------|--------------|  
|_CHAR_UNSIGNED –|Výchozí znakový typ není přiřazen. Když definované [/J](../../build/reference/j-default-char-type-is-unsigned.md) je zadána možnost.|  
|_CPPRTTI –|Pro kód kompilovat s definována [GR](../../build/reference/gr-enable-run-time-type-information.md) možnost.|  
|_CPPUNWIND –|Pro kód kompilovat s definována [/EHsc](../../build/reference/eh-exception-handling-model.md) možnost.|  
|_DLL –|Když definované [/MD](../../build/reference/md-mt-ld-use-run-time-library.md) je zadána možnost.|  
|_M_IX86 –|Ve výchozím nastavení, definovaná na 600 pro x86 cíle.|  
|_MSC_VER –|Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md).|  
|_WIN32 –|Pro aplikace WIN32 definován. Vždy definována.|  
|_MT|Když definované [/MD nebo/MT](../../build/reference/md-mt-ld-use-run-time-library.md) je zadána možnost.|  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **Upřesnit** stránku vlastností.  
  
4.  Změnit **nedefinované Definice preprocesoru** nebo **nedefinované všechny definice preprocesoru** vlastnosti.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> nebo <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [/J (výchozí znakový typ není podepsán)](../../build/reference/j-default-char-type-is-unsigned.md)   
 [/GR (povolit informace běhového typu)](../../build/reference/gr-enable-run-time-type-information.md)   
 [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md)   
 [/MD, /MT, /LD (použití knihovny run-time)](../../build/reference/md-mt-ld-use-run-time-library.md)