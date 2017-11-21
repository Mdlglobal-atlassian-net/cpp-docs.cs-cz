---
title: "-GL (celková optimalizace programu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
dev_langs: C++
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20436df9fd2f54193183505eb56da7c7b3371164
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="gl-whole-program-optimization"></a>/GL (celková optimalizace programu)
Umožňuje optimalizace celého programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GL[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 Optimalizace celého programu umožňuje kompilátoru k provedení optimalizace s informacemi o na všechny moduly v programu. Bez optimalizace celého programu optimalizace se provádí na na základě modulu (kompilace).  
  
 Optimalizace celého programu ve výchozím nastavení a musí být explicitně povolené. Ale je také možné explicitně zakázat její **/GL-**.  
  
 S informacemi o všechny moduly můžete kompilátor:  
  
-   Optimalizujte použití registrů napříč hranicemi funkce.  
  
-   Proveďte lépe sledování změny globálních dat, a umožňují snížení počtu zatížení a úložiště.  
  
-   Se lépe daří sledování dereference možné sady položek upraveném ukazatel snížení počtu zatížení a úložiště.  
  
-   Vložené funkce v modulu i v případě, že funkce je definována v jiný modul.  
  
 soubory .obj vytvořeného s **/GL** nebudou k dispozici na takových nástrojů linkeru jako [nástroje EDITBIN](../../build/reference/editbin-reference.md) a [DUMPBIN](../../build/reference/dumpbin-reference.md).  
  
 Pokud je váš program s **/GL** a [/c](../../build/reference/c-compile-without-linking.md), propojovacího/ltgc by měl použít k vytvoření výstupního souboru.  
  
 [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) nelze použít s **/GL**  
  
 Formát souborů vytvořeného s **/GL** v aktuální verzi nemusí být přečíst další verze Visual C++. By neměl dodávat soubor LIB tvořená .obj soubory, které byly vytvořeny s **/GL** Pokud jste ochotni dodávat kopie souboru .lib pro všechny verze aplikace Visual C++ očekáváte, aby uživatelé používali, teď a v budoucnu.  
  
 soubory .obj vytvořeného s **/GL** a Předkompilované soubory hlaviček nesmí se použít k vytvoření souboru .lib, pokud soubor .lib bude propojený na stejný počítač, který vytváří **/GL** souboru .obj. Informace ze souboru .obj předkompilovaný hlavičkový soubor bude potřeba v době spojení.  
  
 Další informace o optimalizace, které jsou k dispozici a omezení optimalizace celého programu najdete v tématu [/ltgc](../../build/reference/ltcg-link-time-code-generation.md).  **/GL** také díky profil s průvodcem optimalizace, které jsou k dispozici; najdete v části/ltgc.  Při kompilaci pro optimalizace a pokud chcete, aby funkce řazení z váš profil na základě optimalizace na základě profilu, je nutné kompilovat s [/Gy](../../build/reference/gy-enable-function-level-linking.md) nebo možnost kompilátoru, která znamená /Gy.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  V tématu [/ltgc (vytváření kódu v době propojování)](../../build/reference/ltcg-link-time-code-generation.md) informace o tom, jak zadat **/GL** ve vývojovém prostředí.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)