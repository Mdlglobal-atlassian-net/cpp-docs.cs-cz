---
title: "-LN (vytvořit modul MSIL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /LN
dev_langs:
- C++
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0278d59af9a62393f90a91655e3d7f0323e08118
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ln-create-msil-module"></a>/LN (Vytvořit modul MSIL)
Určuje, že manifest sestavení by neměly být vložen do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/LN  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení **/LN** není platný (manifest sestavení se vloží do výstupního souboru).  
  
 Když **/LN** se používá, mezi [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) možnosti musí být rovněž použit.  
  
 Spravovaný program, který nemá metadata sestavení v manifestu je volána modul. Pokud je kompilovat s [/c (Kompilovat bez propojení)](../../build/reference/c-compile-without-linking.md) a **/LN**, zadejte [/NOASSEMBLY (vytvořit modul MSIL)](../../build/reference/noassembly-create-a-msil-module.md) ve fázi linkeru pro vytvoření výstupního souboru.  
  
 Můžete vytvořit moduly, pokud budete chtít využít přístup podle součásti pro vytváření sestavení.  To znamená můžete vytvářet typy a kompilována moduly.  Potom můžete vygenerovat sestavení z jednoho nebo více modulů.  Další informace o vytváření sestavení z modulů najdete v tématu [.netmodule soubory jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md) nebo [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker).  
  
 Výchozí přípona souboru pro modul je .netmodule.  
  
 V [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] verze před Visual C++ 2005 modul byl vytvořen s **/clr:noAssembly**.  
  
 Visual C++ linkeru .netmodule soubory akceptuje jako vstupní a výstupní soubor vyprodukované linkeru bude sestavení nebo .netmodule s už závislost běhu na žádném z .netmodules, že se vstupní linkeru.  Další informace najdete v tématu [.netmodule soubory jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
-   Zadejte [/NOASSEMBLY (vytvořit modul MSIL)](../../build/reference/noassembly-create-a-msil-module.md) ve fázi linkeru pro vytvoření výstupního souboru.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   Tato možnost kompilátoru nelze změnit prostřednictvím kódu programu.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)