---
title: -WX (zpracovávat upozornění Linkeru jako chyby) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /WX
dev_langs:
- C++
helpviewer_keywords:
- /WX linker option
- -WX linker option
- WX linker option
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 686b17a3db00175340e3490241c6c2e9f9325225
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377284"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX (Zpracovávat upozornění linkeru jako chyby)
```  
/WX[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 /WX způsobí, že žádná výstupní soubor do vyvolala v případě linkeru vygeneruje upozornění.  
  
 Toto je podobná **wdn** pro kompilátor (najdete v části [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, nebo jsme /wo, /Wv, wdn (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md) Další informace). Ale zadání **wdn** pro kompilace není určeno, který **wdn** také bude platit pro fázi odkaz; je nutné explicitně zadat **wdn** pro jednotlivé nástroje.  
  
 Ve výchozím nastavení **wdn** není funkční. Zacházet s upozornění linkeru jako chyby, zadejte **wdn**. **/WX:No** je stejný jako bez zadání **wdn**.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)