---
title: "Možnosti kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler
- IPF Visual C++ compiler
- Itanium Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 490814f85199450d4261bf4071184b75b5ea10c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-options"></a>Možnosti kompilátoru
cl.exe je nástroj, který řídí Microsoft C a C++ kompilátory a linkeru. cl.exe lze spustit pouze v operačních systémech, které podporují Microsoft Visual Studio.  
  
> [!NOTE]
>  Můžete spustit tento nástroj pouze z [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] příkazového řádku. Nelze ji spustit z příkazového řádku systému nebo v Průzkumníku souborů.  
  
 Kompilátory vytvořit soubory objektů (.obj) běžné objekt souboru formátu (COFF). Spustitelné soubory (.exe) nebo dynamické knihovny (DLL), který produkuje linkeru.  
  
 Všimněte si, že jsou všechny možnosti kompilátoru velká a malá písmena.  
  
 Chcete-li kompilovat bez propojení, použijte [/c](../../build/reference/c-compile-without-linking.md).  
  
## <a name="finding-an-option"></a>Možnosti hledání  
 Možnost konkrétní kompilátoru naleznete v tématu jednu z následujících seznamů:  
  
-   [Možnosti kompilátoru uvedené podle abecedy](../../build/reference/compiler-options-listed-alphabetically.md)  
  
-   [Možnosti kompilátoru uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md)  
  
## <a name="specifying-options"></a>Zadání možností  
 Téma pro každý – možnost kompilátoru popisuje, jak lze nastavit ve vývojovém prostředí. Informace o zadání možností mimo vývojového prostředí najdete v tématu:  
  
-   [Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)  
  
-   [Soubory příkazů CL](../../build/reference/cl-command-files.md)  
  
-   [Proměnné prostředí CL](../../build/reference/cl-environment-variables.md)  
  
## <a name="related-build-tools"></a>Související sestavovací nástroje  
 Použití [NMAKE](../../build/nmake-reference.md) k vytvoření výstupního souboru.  
  
 Použití [BSCMAKE](../../build/reference/bscmake-reference.md) pro podporu třída procházení.  
  
 [Možnosti linkeru](../../build/reference/linker-options.md) ovlivní také, jak je integrovaná vašeho programu.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz sestavení C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Rychlá kompilace](../../build/reference/fast-compilation.md)   
 [CL vyvolává Linker](../../build/reference/cl-invokes-the-linker.md)