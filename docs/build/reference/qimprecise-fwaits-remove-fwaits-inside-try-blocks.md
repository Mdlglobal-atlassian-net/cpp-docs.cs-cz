---
title: "-Qimprecise_fwaits (odebrání příkazů fwaits z bloků Try) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Qimprecise_fwaits
dev_langs:
- C++
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 06c93e60530d870b05c601be4980308feb627b46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (odebrání příkazů fwaits z bloků Try)
Odebere `fwait` příkazy interní `try` blokuje při použití [/fp: kromě](../../build/reference/fp-specify-floating-point-behavior.md) – možnost kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Qimprecise_fwaits  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost nemá vliv, pokud **/fp: kromě** také není zadán. Pokud zadáte **/fp: kromě** možnost, budou vkládat kompilátor `fwait` kolem každého řádku kódu v příkazu `try` bloku. Tímto způsobem můžete kompilátor identifikovat konkrétní řádek kódu, který vytváří výjimku. **/ Qimprecise_fwaits** odebere interní `fwait` pokyny, ponechat pouze počká kolem `try` bloku. To zvyšuje výkon, ale pouze kompilátor bude moct Řekněme, který `try` bloku dojde k výjimce, ne kterém řádku.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)