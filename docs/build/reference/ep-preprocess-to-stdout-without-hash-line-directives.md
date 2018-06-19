---
title: '-EP (předběžné zpracování do direktiv bez #line direktivy) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
dev_langs:
- C++
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38047fecbbd1bbaa87db3766b046efa8b446d93a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375380"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (předběžné zpracování do direktiv bez příkazů #line)
Upraví C a C++ zdrojové soubory a zkopíruje předběžně zpracované soubory do standardního výstupního zařízení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/EP  
```  
  
## <a name="remarks"></a>Poznámky  
 V procesu jsou prováděny všechny preprocesor – direktivy, jsou prováděny makro rozšíření a komentáře se odeberou. Chcete-li zachovat komentáře v předběžně zpracované výstup, použijte [/C (zachovat komentáře při předběžném zpracování)](../../build/reference/c-preserve-comments-during-preprocessing.md) možnost s **/EP**.  
  
 **/EP** možnost potlačí kompilace. Soubor předběžně zpracované pro kompilaci musí odešlete znovu. **/EP** také potlačí výstupní soubory z **/FA**, **/Fa**, a **/Fm** možnosti. Další informace najdete v tématu [/FA, /Fa (soubor výpis)](../../build/reference/fa-fa-listing-file.md) a [/Fm (název souboru mapování)](../../build/reference/fm-name-mapfile.md).  
  
 Chyby generované během novější fází zpracování naleznete čísla řádků předběžně zpracované souboru místo původní zdrojový soubor. Pokud chcete, aby čísla řádků, který bude odkazovat na původní zdrojový soubor, použijte [/E (předběžné zpracování výstupu stdout)](../../build/reference/e-preprocess-to-stdout.md) místo. **/E** přidá možnost `#line` direktivy pro výstup pro tento účel.  
  
 K odeslání předběžně zpracované výstup s `#line` direktivy, do souboru, použijte [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) místo něj.  
  
 K odeslání předběžně zpracované výstupu stdout, s `#line` direktivy, použijte **/P** a **/EP** společně.  
  
 Nelze použít s předkompilovaných hlaviček **/EP** možnost.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **preprocesor** stránku vlastností.  
  
4.  Změnit **generovat soubor zpracované** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkazový řádek upraví soubor `ADD.C`, zachová komentáře a zobrazí výsledek do standardního výstupního zařízení:  
  
```  
CL /EP /C ADD.C  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)