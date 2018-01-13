---
title: "-FUNCTIONPADMIN (vytvořit bitovou kopii opravitelnou za provozu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /functionpadmin
dev_langs: C++
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f737cdb412420ffb87664024b2314941e67b045b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Vytvořit bitovou kopii s možností provádění oprav za běhu)
Připraví bitovou kopii pro opravy za provozu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/FUNCTIONPADMIN[:space]  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `space`(volitelné)  
 Velikost odsazení přidat na začátek jednotlivé funkce, 5, 6 nebo 16.  x86 obrázky vyžadují pět bajtů odsazení, x64 obrázky vyžadují 6 bajtů a obrazů sestavených pro třídu procesoru pro procesory Itanium vyžadují 16 bajtů odsazení na začátku každé funkce.  
  
 Ve výchozím nastavení kompilátor přidá správné množství místa na bitovou kopii, na základě typu počítače bitové kopie.  
  
 Aby linkeru k vytvoření bitovou kopii opravitelnou za provozu, soubory .obj musí sestavili jsme s [/hotpatch (vytvořit kopii opravitelnou za provozu)](../../build/reference/hotpatch-create-hotpatchable-image.md).  
  
 Při kompilování a propojit bitovou kopii pomocí jednoho volání cl.exe, **/hotpatch** znamená **/functionpadmin**.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)