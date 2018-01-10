---
title: "-diagnostiky (možnosti kompilátoru diagnostiky) | Microsoft Docs"
ms.custom: 
ms.date: 11/11/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
dev_langs: C++
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a1c893b530bfa895e5ec127bd0aea2fb0df4ff3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/Diagnostics (možnosti kompilátoru diagnostiky)  
  
Použití **/diagnostics** – možnost kompilátoru k určení zobrazení chyb a upozornění informace o umístění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/diagnostics:{caret|classic|column}
```  

## <a name="remarks"></a>Poznámky  
**/Diagnostics** – možnost kompilátoru ovládací prvky zobrazení informace o upozornění a chyby.  
  
**/Diagnostics:classic** je výchozí nastavení, která hlásí jenom číslo řádku kde byl nalezen problém.  
  
**/Diagnostics:column** možnost také obsahuje sloupec, kde byl nalezen problém. To vám může pomoct identifikovat konkrétní jazyk konstrukce nebo znak, který je příčinou problému.  
  
**/Diagnostics:caret** možnost obsahuje sloupec, kde problém byl nalezen a umístí šipka nahoru (^) v umístění v řádku kódu, kde byl zjištěn problém.  
  
Všimněte si, že v některých případech, kompilátor nezjistí kde došlo k problému. Chybí středník například nemusí zjistit, dokud symboly, které neočekávané byly zjištěny. Sloupec se použije v hlášení a vsuvka je umístěn, kde kompilátor zjistil, že něco byla chybná, což není vždy potřebujete-li provést vaší opravu.  
  
**/Diagnostics** možnost je k dispozici od Visual Studio 2017.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete váš projekt **stránky vlastností** dialogové okno.   
  
2. V části **vlastnosti konfigurace**, rozbalte **C/C++** složky a vyberte **Obecné** stránku vlastností.  
  
3. Použijte ovládací prvek rozevírací seznam v **diagnostiky formátu** možnost zobrazit pole a vyberte diagnostiky. Zvolte **OK** nebo **použít** uložte provedené změny.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)