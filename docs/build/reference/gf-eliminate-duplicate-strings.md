---
title: "-GF (odstranění duplicitních řetězců) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
dev_langs:
- C++
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d69e892fb9487b66da4dfa2a801bab302e962af7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (odstranění duplicitních řetězců)
Umožňuje kompilátor vytvoří jednu kopii identické řetězce v bitové kopii program a v paměti při spuštění. Toto je optimalizace názvem *sdružování řetězec* , můžete vytvořit menší programy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GF  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud používáte **/GF**, operační systém není prohození části řetězce paměti a může číst řetězce zpět ze souboru bitové kopie.  
  
 **/GF** fondy řetězce jen pro čtení. Pokud se pokusíte upravit řetězce v rámci **/GF**, dojde k chybě aplikace.  
  
 Řetězec sdružování umožňuje, co byly určený jako více ukazatele na více vyrovnávací paměti jako více ukazatele na jednu vyrovnávací paměť. V následujícím kódu `s` a `t` jsou inicializovány stejné řetězcem. Sdružování řetězců příčiny je tak, aby odkazoval na stejnou paměť:  
  
```  
char *s = "This is a character buffer";  
char *t = "This is a character buffer";  
```  
  
> [!NOTE]
>  [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) možnost použít pro upravit a pokračovat, automaticky nastaví **/GF** možnost.  
  
> [!NOTE]
>  **/GF** – možnost kompilátoru vytvoří adresovatelné sekci pro každého jedinečného řetězce. A ve výchozím nastavení, soubor objekt může obsahovat maximálně 65 536 adresovatelné oddíly. Pokud váš program obsahuje více než 65 536 řetězce, použijte [/bigobj](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md) – možnost kompilátoru vytvořit další části.  
  
 **/GF** je v ovlivňuje při [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) nebo **/O2** se používá.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **generování kódu** stránku vlastností.  
  
4.  Změnit **povolit sdružování řetězec** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)