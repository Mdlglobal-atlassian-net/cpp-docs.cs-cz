---
title: "-E (předběžné zpracování výstupu stdout) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /e
dev_langs: C++
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b3540a2d6d1c32a72d16cdb9bdab19aa18604021
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="e-preprocess-to-stdout"></a>/E (předběžné zpracování výstupu stdout)
Upraví C a C++ zdrojové soubory a zkopíruje předběžně zpracované soubory do standardního výstupního zařízení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/E  
```  
  
## <a name="remarks"></a>Poznámky  
 V tomto procesu všechny preprocesor – direktivy jsou prováděny postupně, jsou prováděny makro rozšíření a komentáře se odeberou. Chcete-li zachovat komentáře v předběžně zpracované výstup, použijte [/C (zachovat komentáře při předběžném zpracování)](../../build/reference/c-preserve-comments-during-preprocessing.md) i – možnost kompilátoru.  
  
 **/E** přidá `#line` direktivy pro výstup na začátku a konci jednotlivých součástí souborů a kolem řádky odebrat pomocí preprocesor – direktivy pro Podmíněná kompilace. Tyto direktivy přečíslování řádky předběžně zpracované souboru. Chyby generované během novější fáze zpracování v důsledku toho naleznete čísla řádků původní zdrojový soubor místo řádků v předběžně zpracované souboru.  
  
 **/E** možnost potlačí kompilace. Soubor předběžně zpracované pro kompilaci musí odešlete znovu. **/E** také potlačí výstupní soubory z **/FA**, **/Fa**, a **/Fm** možnosti. Další informace najdete v tématu [/FA, /Fa (soubor výpis)](../../build/reference/fa-fa-listing-file.md) a [/Fm (název souboru mapování)](../../build/reference/fm-name-mapfile.md).  
  
 Chcete-li potlačit `#line` direktivy, použijte [/EP (předběžné zpracování do direktiv bez #line direktivy)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) místo něj.  
  
 K odeslání předběžně zpracované výstup do souboru místo položky `stdout`, použijte [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) místo něj.  
  
 Chcete-li potlačit `#line` direktivy a odesílání předběžně zpracované výstup do souboru, použijte **/P** a **/EP** společně.  
  
 Nelze použít s předkompilovaných hlaviček **/E** možnost.  
  
 Všimněte si, že při předběžném zpracování do samostatného souboru, mezery nejsou vygenerované po tokeny. To mít za následek neplatný program nebo mít nezamýšleným vedlejší účinky. Úspěšně se zkompiluje následující program:  
  
```  
#define m(x) x  
m(int)main( )  
{  
   return 0;  
}  
```  
  
 Ale pokud zkompilujete pomocí:  
  
```  
cl -E test.cpp > test2.cpp  
```  
  
 `int main`v test2.cpp nesprávně bude `intmain`.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti**pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## <a name="example"></a>Příklad  
 Upraví následující příkazový řádek `ADD.C`, zachová komentáře, přidá `#line` direktivy a zobrazí výsledek do standardního výstupního zařízení:  
  
```  
CL /E /C ADD.C  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)