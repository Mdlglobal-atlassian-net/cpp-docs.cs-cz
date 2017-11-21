---
title: "-GR (povolit informace běhového typu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /gr
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
dev_langs: C++
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3420af666ac4b9dca648b780ae99e794265515bd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="gr-enable-run-time-type-information"></a>/GR (Povolit informace běhového typu)
Přidá kód ke kontrole typy objektů v době běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GR[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 Když **GR** zapnutý, kompilátor definuje `_CPPRTTI` makro preprocesoru. Ve výchozím nastavení **GR** zapnutý. **/GR-** zakáže informace běhového typu.  
  
 Použití **GR** Pokud kompilátor staticky nelze vyřešit typ objektu, který do vašeho kódu. Obvykle potřebujete **GR** při používá váš kód [dynamic_cast – operátor](../../cpp/dynamic-cast-operator.md) nebo [typeid](../../cpp/typeid-operator.md). Ale **GR** zvyšuje velikost oddílů .rdata vaší bitové kopie. Pokud váš kód nepoužívá **dynamic_cast** nebo **typeid**, **/GR-** může vytvořit bitovou kopii menší.  
  
 Další informace o kontrole běhového typu najdete v tématu [informací o typu Run-Time](../../cpp/run-time-type-information.md) v *referenční příručka jazyka C++*.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **jazyk** stránku vlastností.  
  
4.  Změnit **povolit informace o typu Run-Time** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)