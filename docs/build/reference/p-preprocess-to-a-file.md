---
title: "-P (předběžné zpracování souboru) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
dev_langs: C++
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f4de2f19820a846197806e0a24ddc213dd636c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="p-preprocess-to-a-file"></a>/P (předběžné zpracování souboru)
Upraví C a C++ zdrojových souborů a předběžně zpracované výstup zapisuje do souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/P  
```  
  
## <a name="remarks"></a>Poznámky  
 Soubor má stejný základní název jako zdrojový soubor a .i rozšíření. V procesu jsou prováděny všechny preprocesor – direktivy, jsou prováděny makro rozšíření a komentáře se odeberou. Chcete-li zachovat komentáře v předběžně zpracované výstup, použijte [/C (zachovat komentáře při předběžném zpracování)](../../build/reference/c-preserve-comments-during-preprocessing.md) možnost spolu s **/P**.  
  
 **/P** přidá `#line` direktivy pro výstup na začátku a konci jednotlivých součástí souborů a kolem řádky odebrat pomocí preprocesor – direktivy pro Podmíněná kompilace. Tyto direktivy přečíslování řádky předběžně zpracované souboru. Chyby generované během novější fáze zpracování v důsledku toho naleznete čísla řádků původní zdrojový soubor místo řádků v předběžně zpracované souboru. Chcete-li potlačit generování `#line` direktivy, použijte [/EP (předběžné zpracování do direktiv bez #line direktivy)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) a také **/P**.  
  
 **/P** možnost potlačí kompilace. I když používáte nevytváří soubor .obj [/Fo (název souboru objektů)](../../build/reference/fo-object-file-name.md). Soubor předběžně zpracované pro kompilaci musí odešlete znovu. **/P** také potlačí výstupní soubory z **/FA**, **/Fa**, a **/Fm** možnosti. Další informace najdete v tématu [/FA, /Fa (soubor výpis)](../../build/reference/fa-fa-listing-file.md) a [/Fm (název souboru mapování)](../../build/reference/fm-name-mapfile.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **preprocesor** stránku vlastností.  
  
4.  Změnit **generovat soubor zpracované** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## <a name="example"></a>Příklad  
 Upraví následující příkazový řádek `ADD.C`, zachová komentáře, přidá `#line` direktivy a zapíše výsledek do souboru, `ADD.I`:  
  
```  
CL /P /C ADD.C  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [/Fi (předběžné zpracování názvu výstupního souboru)](../../build/reference/fi-preprocess-output-file-name.md)