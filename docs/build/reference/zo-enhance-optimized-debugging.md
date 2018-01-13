---
title: "-Zo (rozšířené optimalizované ladění) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- -Zo
- /Zo
dev_langs: C++
helpviewer_keywords:
- Zo compiler option [C++]
- /Zo compiler option [C++]
- -Zo compiler option [C++]
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 326bd1c6c435dec97c309014dfc81ca444cc5eb6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo (rozšířené optimalizované ladění)
Generuje rozšířené informace o ladění pro optimalizovaný kód v sestavení bez ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
/Zo[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 **/Zo** přepínače kompilátoru generuje rozšířené informace o ladění optimalizovaného kódu. Optimalizace může použít zaregistruje pro místní proměnné, uspořádat kód, vectorize smyčky a vložené funkce volání. Tyto optimalizace mohou skrývat vztah mezi zdrojový kód a kód zkompilovaný objekt. **/Zo** přepínač říká kompilátoru ke generování dalších informací o ladění pro místní proměnné a vložená funkce. Použijte zobrazíte proměnné v **automobily**, **místní hodnoty –**, a **sledovat** systému windows, když v průběhu optimalizovaného kódu v ladicím programu sady Visual Studio. Umožňuje také trasování zásobníku zobrazíte vložená funkce v ladicím programu WinDBG. Laděná sestavení, které mají zakázáno optimalizace ([/Od](../../build/reference/od-disable-debug.md)) nemusí Další ladicí informace, které jsou generovány při **/Zo** je zadán. Použití **/Zo** přepínač tak, aby verze konfigurace ladění s optimalizací zapnutý. Další informace o optimalizaci přepínače najdete v tématu [/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md). **/Zo** je povolena možnost ve výchozím nastavení v sadě Visual Studio, když zadáte informace o ladění s **/Zi** nebo **/Z7**. Zadejte **/Zo-** explicitně zakázat tento – možnost kompilátoru.  
  
 **/Zo** přepínač je k dispozici od verze Visual Studio 2013 Update 3 a nahradí dříve nedokumentovanými **/d2Zi+** přepínače.  
  
### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>Nastavení možnosti kompilátoru /Zo v sadě Visual Studio  
  
1.  Otevřete **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **vlastnosti konfigurace**, **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Změnit **další možnosti** vlastnost, aby zahrnovala `/Zo` a potom zvolte **OK**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md)   
 [/ Z7, / zi, /ZI (formát ladicích informací)](../../build/reference/z7-zi-zi-debug-information-format.md)   
 [Upravit a pokračovat](/visualstudio/debugger/edit-and-continue)