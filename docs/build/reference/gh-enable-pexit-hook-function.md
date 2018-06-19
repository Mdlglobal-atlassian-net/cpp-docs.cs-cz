---
title: -GH (Povolit funkce háku _pexit) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _pexit
dev_langs:
- C++
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57e11c27af36eb539b22f3833a73341ff3065e97
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374502"
---
# <a name="gh-enable-pexit-hook-function"></a>/GH (Povolit funkce háku _pexit)
Volání `_pexit` funkce na konci každé metody nebo funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GH  
```  
  
## <a name="remarks"></a>Poznámky  
 `_pexit` Funkce není součástí žádné knihovny a je na vás poskytují definici pro `_pexit`.  
  
 Pokud máte v úmyslu explicitně volání `_pexit`, není potřeba zadat prototypu. Funkce, musí se zobrazí jako by mělo následující prototyp, a musí push obsah všech registrů na záznam a pop obsah beze změny při ukončení:  
  
```  
void __declspec(naked) _cdecl _pexit( void );  
```  
  
 `_pexit` je podobná `_penter`; najdete v části [/Gh (Povolit _penter – funkce háku)](../../build/reference/gh-enable-penter-hook-function.md) příklad toho, jak k zápisu `_pexit` funkce.  
  
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