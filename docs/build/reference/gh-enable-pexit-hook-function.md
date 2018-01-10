---
title: "-GH (Povolit funkce háku _pexit) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _pexit
dev_langs: C++
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 02cfdd783a698a3397e84fa62b7252399570dc84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
  
 `_pexit`je podobná `_penter`; najdete v části [/Gh (Povolit _penter – funkce háku)](../../build/reference/gh-enable-penter-hook-function.md) příklad toho, jak k zápisu `_pexit` funkce.  
  
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