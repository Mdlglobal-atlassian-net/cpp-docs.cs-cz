---
title: -link (Pass možností Linkeru) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /link
dev_langs:
- C++
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b22e21022162a0f9f75e41e3e0bfdce348947e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="link-pass-options-to-linker"></a>/link (předání možností linkeru)
Jedna nebo více možností linkeru předá linkeru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/link linkeroptions  
```  
  
## <a name="arguments"></a>Arguments  
 `linkeroptions`  
 – Možnost linkeru nebo možnosti, které mají být předány linkeru.  
  
## <a name="remarks"></a>Poznámky  
 **/Link** možnost a její možnosti linkeru musí následovat za všechny názvy souborů a možností CL. Je vyžadován mezi mezeru **/link** a `linkeroptions`. Další informace najdete v tématu [nastavení možnosti Linkeru](../../build/reference/setting-linker-options.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte na tlačítko stránky vlastností linkeru.  
  
4.  Upravte některé vlastnosti.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   Tato možnost kompilátoru nelze změnit prostřednictvím kódu programu.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)