---
title: "-Qimprecise_fwaits (odebrání příkazů fwaits z bloků Try) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Qimprecise_fwaits
dev_langs: C++
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9aa09590e1ede80107a085c03528b4c9089885bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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