---
title: -Qimprecise_fwaits (odebrání příkazů fwaits z bloků Try) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Qimprecise_fwaits
dev_langs:
- C++
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a688f4b9f8f3c9302bb6a49e4b0a94a0e0931b33
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378051"
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