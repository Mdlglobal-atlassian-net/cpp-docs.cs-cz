---
title: "-Wp64 (zjištěny problémy s 64bitovou přenositelností) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
dev_langs: C++
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 34a505aec6619243e6f7822724f2c9d5944d3e90
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (Zjištěny problémy s 64bitovou přenositelností)

Tato možnost kompilátoru je zastaralé. Ve verzích sady Visual Studio před Visual Studio 2013, tato zjistí problémy s 64bitovou přenositelností v typy, které jsou také označené [__w64](../../cpp/w64.md) – klíčové slovo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Wp64  
```  
  
## <a name="remarks"></a>Poznámky  

Ve výchozím nastavení se ve verzích sady Visual Studio před Visual Studiu 2013 se **/Wp64** – možnost kompilátoru vypnuté v kompilátoru Visual C++, který sestaví x86 32-bit kód, a na ve Visual C++ compiler, vytvoří 64bitové x64 kódu.  
  
> [!IMPORTANT]
>  [/Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md) – možnost kompilátoru a [__w64](../../cpp/w64.md) – klíčové slovo v sadě Visual Studio 2010 a Visual Studio 2012 jsou zastaralé a nepodporují spouštění v sadě Visual Studio 2013. Pokud převedete projekt, který používá tento přepínač, přepínač se nemigruje během převodu. Chcete-li použít tuto možnost v sadě Visual Studio 2010 nebo Visual Studio 2012, musíte zadat přepínače kompilátoru pod **další možnosti** v **příkazového řádku** části vlastností projektu. Pokud použijete **/Wp64** – možnost kompilátoru do příkazového řádku kompilátoru problémy D9002 upozornění příkazového řádku. Místo použití tuto možnost a klíčové slovo rozpoznat problémy s 64bitovou přenositelností, použít – kompilátor Visual C++, která je cílena 64bitové platformě a zadejte [/W4](../../build/reference/compiler-option-warning-level.md) možnost. Další informace najdete v tématu [konfigurace Visual C++ pro 64bitové, x64 cíle](../../build/configuring-programs-for-64-bit-visual-cpp.md).  
  
Proměnné následující typy jsou testovány v 32bitové verzi operačního systému, jako kdyby byly se používají na 64bitový operační systém:  
  
-   int  
  
-   long  
  
-   ukazatel  
  
 Pokud zkompilujete pravidelně vaší aplikace pomocí kompilátoru, která vytvoří 64bitové x64 kódu, můžete jenom zakázat **/Wp64** v kompilaci vaše 32bitová verze protože 64bitový kompilátor zjistí všechny problémy. Další informace o tom, jak cílový Windows 64bitový operační systém najdete v tématu [konfigurace Visual C++ pro 64bitové, x64 cíle](../../build/configuring-programs-for-64-bit-visual-cpp.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno.  
  
     Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Změnit **další možnosti** políčko zahrnout **/Wp64**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>.  
  
## <a name="see-also"></a>Viz také  

[Možnosti kompilátoru](../../build/reference/compiler-options.md)   
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
[Konfigurace Visual C++ pro 64bitové, x64 cíle](../../build/configuring-programs-for-64-bit-visual-cpp.md)