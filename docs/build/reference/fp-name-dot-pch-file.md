---
title: "-Fp (název. Soubor pch) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- /fp
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
dev_langs: C++
helpviewer_keywords:
- Fp compiler option [C++]
- -Fp compiler option [C++]
- naming precompiler header files
- PCH files, naming
- names [C++], PCH
- .pch files, naming
- precompiled header files, naming
- /Fp compiler option [C++]
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 77ba54705ec4037f1c98a2ae1832dddcc551956e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fp-name-pch-file"></a>/Fp (název souboru .Pch)
Poskytuje název cesty pro předkompilované hlavičky místo použití výchozí název cesty.  
  
## <a name="syntax"></a>Syntaxe  
  
> **/Fp**_pathname_  
  
## <a name="remarks"></a>Poznámky  
 Pomocí této možnosti se [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) nebo [/Yu (Použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md) k zadání názvu cesty pro předkompilované hlavičky místo použití výchozí název cesty. Můžete také použít **/Fp** s **/Yc** k určení použití předkompilovaný hlavičkový soubor, který se liší od **/Yc***filename* argument a ze základní název zdrojového souboru.  
  
 Pokud nezadáte rozšíření jako součást s názvem cesty, se předpokládá, že rozšíření .pch. Pokud zadáte adresáři, aniž by název souboru, výchozí název souboru je VC*x*0.pch, kde *x* je hlavní verzi Visual C++ v použití.  
  
 Můžete také **/Fp** možnost s **/Yu**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **předkompilovaných hlaviček** stránku vlastností.  
  
4.  Změnit **předkompilovaný hlavičkový soubor** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>.  
  
## <a name="example"></a>Příklad  
 Pokud chcete vytvořit předkompilovaný hlavičkový soubor pro ladění verzi vašeho programu a jsou kompilování zdrojového kódu i soubory hlaviček, můžete například zadat příkaz:  
  
```  
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP  
```  
  
## <a name="example"></a>Příklad  
 Následující příkaz určuje použití předkompilovaných hlaviček soubor s názvem MYPCH.pch. Kompilátor předpokládá, že má byl zdrojový kód v PROG.cpp předkompilovaných prostřednictvím MYAPP.h a předkompilovaných kódu, které se nachází v MYPCH.pch. Používá obsah MYPCH.pch a zkompiluje zbytek PROG.cpp vytvoření souboru .obj. Výstup tohoto příkladu je soubor s názvem PROG.exe.  
  
```  
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP  
```  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Určení názvu cesty](../../build/reference/specifying-the-pathname.md)