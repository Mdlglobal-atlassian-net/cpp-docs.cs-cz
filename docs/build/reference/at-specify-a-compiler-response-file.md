---
title: "@ (Zadat soubor odezvy kompilátoru) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '@'
dev_langs: C++
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fcbadb55b2116b0939bbb954e4f544c40caacebb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="-specify-a-compiler-response-file"></a>@ (Zadat soubor odezvy kompilátoru)
Určuje soubor odezvy kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Textový soubor obsahující kompilátoru příkazy.  
  
## <a name="remarks"></a>Poznámky  
 Soubor odpovědí může obsahovat všechny příkazy, které zadáte v příkazovém řádku. To může být užitečné, pokud vaše argumenty příkazového řádku přesáhnout délku 127 znaků.  
  
 Není možné zadat  **@**  možnost ze souboru odpovědí. To znamená, že soubor odezvy nelze vložit jiný soubor odpovědi.  
  
 Z příkazového řádku můžete zadat možnosti tolik souboru odpovědí (například `@respfile.1 @respfile.2`) tak, jak chcete.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
-   Soubor odezvy z nelze zadat v rámci vývojového prostředí a musí být zadán v příkazovém řádku.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   Tato možnost kompilátoru nelze změnit prostřednictvím kódu programu.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)