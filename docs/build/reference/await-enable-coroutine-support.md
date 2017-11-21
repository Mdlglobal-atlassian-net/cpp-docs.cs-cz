---
title: -await (povolit podporu coroutine) | Microsoft Docs
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /await
- -await
dev_langs: C++
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c49c55d8203797dfc8fbee881e5f521883daabb4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="await-enable-coroutine-support"></a>/ await (povolit podporu coroutine)  
  
Použití **/ await** – možnost kompilátoru povolit podpora kompilátoru pro coroutines.  
  
## <a name="syntax"></a>Syntaxe  
  
> / await  
  
## <a name="remarks"></a>Poznámky  
  
**/ Await** – možnost kompilátoru umožňuje podporu kompilátoru C++ coroutines a klíčová slova **co_await**, **co_yield**, a **co_return**. Tato možnost je ve výchozím nastavení vypnutý. Informace o podpoře pro coroutines v sadě Visual Studio najdete v tématu [blogu týmu Visual Studio](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/). Další informace o návrhu standardní coroutines najdete v tématu [N4628 práce koncept, technická specifikace pro rozšíření C++ pro Coroutines](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4628.pdf).  

**/ Await** možnost je k dispozici od verze sady Visual Studio 2015.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete váš projekt **stránky vlastností** dialogové okno.   
  
2. V části **vlastnosti konfigurace**, rozbalte **C/C++** složky a vyberte **příkazového řádku** stránku vlastností.  
  
3. Zadejte **/ await** – možnost kompilátoru v **další možnosti** pole. Zvolte **OK** nebo **použít** uložte provedené změny.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
  
[Možnosti kompilátoru](../../build/reference/compiler-options.md)   
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)