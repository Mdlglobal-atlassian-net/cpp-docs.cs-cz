---
title: -Zg (Generovat prototypy funkcí) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zg
dev_langs:
- C++
helpviewer_keywords:
- Zg compiler option [C++]
- /Zg compiler option [C++]
- function prototypes, generate function prototypes compiler option
- -Zg compiler option [C++]
- generate function prototypes compiler option
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8288da0981878b17ad0c2091bf2a45569b51740d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="zg-generate-function-prototypes"></a>/Zg (Generovat prototypy funkcí)
Odebrat. Vytvoří prototyp funkce pro každou funkci definovanou v zdrojový soubor, ale nejde kompilovat zdrojový soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Zg  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost kompilátoru již není k dispozici. Byla odebrána v sadě Visual C++ 2015. Tato stránka zůstane uživatelé starší verzí aplikace Visual C++.  
  
 Prototyp funkce zahrnuje návratový typ funkce a typ seznam argumentů. Seznam typů argument je vytvořený z typy formální parametry funkce. Všechny prototypy funkcí již existuje ve zdrojovém souboru budou ignorovány.  
  
 Seznam prototypy se zapíše na standardní výstup. Tento seznam může být vhodné ověřit, jestli jsou kompatibilní skutečných argumentů a formální parametry funkce. V seznamu můžete uložit přesměrováním standardní výstup do souboru. Pak můžete použít **#include** aby seznam prototypy funkcí součástí zdrojového souboru. To způsobí, že kompilátoru provést kontrola argument typu.  
  
 Pokud použijete **/Zg** možnost a váš program obsahuje formální parametry, které obsahují struktura, enum, nebo typu union (nebo odkazy na tyto typy), deklaraci každý struktura, výčet nebo union typ musí mít značku (název). V následující ukázce názvu značky je `MyStruct`.  
  
```C  
// Zg_compiler_option.c  
// compile with: /Zg  
typedef struct MyStruct { int i; } T2;  
void f2(T2 * t) {}  
```  
  
 **/Zg** možnost se nepoužívá v sadě Visual Studio 2005 a byla odebrána v sadě Visual Studio 2015. Kompilátor Visual C++ má odebranou podporu pro starší, stylu jazyka C kód. Seznam – možnosti kompilátoru zastaralé, najdete v části **zastaralé a odebrat – možnosti kompilátoru** v [kompilátoru možnosti uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)