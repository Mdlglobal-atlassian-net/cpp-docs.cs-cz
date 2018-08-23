---
title: -LN (vytvoření modulu MSIL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /LN
dev_langs:
- C++
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ca6d1933b684cc574bc4e0107b9f3f30364c908
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609459"
---
# <a name="ln-create-msil-module"></a>/LN (Vytvořit modul MSIL)
Určuje, že manifest sestavení by neměly být vložen do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/LN  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení **/LN** není platná (manifest sestavení je vložen do výstupního souboru).  
  
 Když **/LN** se používá jednu z [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) možnosti musí být rovněž použita.  
  
 Modul se nazývá spravovaný program, který nemá metadat sestavení v manifestu. Pokud kompilujete s [/c (Kompilovat bez propojení)](../../build/reference/c-compile-without-linking.md) a **/LN**, zadejte [parametr/noassembly (vytvoření modulu MSIL)](../../build/reference/noassembly-create-a-msil-module.md) ve fázi linkeru se vytvořit výstupní soubor.  
  
 Můžete vytvářet moduly, pokud budete chtít využít k vytváření sestavení s přístupem založených na komponentách.  Můžete tedy vytvářet typy a je zkompilovat do modulů.  Potom můžete generovat sestavení z jednoho nebo více modulů.  Další informace o vytvoření sestavení z modulů, naleznete v tématu [soubory .netmodule jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md) nebo [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker).  
  
 Výchozí přípona souboru pro modul je .netmodule.  
  
 Ve verzích Visual C++ před Visual C++ 2005, modul byl vytvořen s **/clr:noAssembly**.  
  
 Linkeru jazyka Visual C++ přijímá soubory .netmodule jako vstup a výstup souboru vytvořený pomocí linkeru bude sestavení nebo modul .NET s za běhu závislost na některý z modulů .NET, které byly vstup do linkeru.  Další informace najdete v tématu [soubory .netmodule jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
-   Zadejte [parametr/noassembly (vytvoření modulu MSIL)](../../build/reference/noassembly-create-a-msil-module.md) ve fázi linkeru se vytvořit výstupní soubor.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   Tato možnost kompilátoru nelze změnit prostřednictvím kódu programu.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)