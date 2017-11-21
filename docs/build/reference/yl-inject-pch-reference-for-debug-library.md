---
title: "-Yi (Vložit referenci PCH ladicí knihovny) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /yi
dev_langs: C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 271681849d78eb8a6a4032bcbafbcc81b96c9f9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Vložit referenci PCH do ladicí knihovny)
Použít po vytvoření knihovny ladění, který používá předkompilovaných hlaviček a sestavení selže.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Ylsymbol  
```  
  
```  
/Yl-  
```  
  
## <a name="arguments"></a>Arguments  
 `symbol`  
 Libovolný symbol má být uložen v objektu modulu.  
  
 \-  
 Znaménkem minus (-), která explicitně zakáže **/Yl** – možnost kompilátoru.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, kompilátor použije **/Yl** možnost (bez zadání *symbol*). **/Yl** možnost umožňuje získat úplné informace o typech ladicího programu. **/Yl-** zakáže výchozí chování.  
  
 Když zkompilujete modul s **/Yc** a **/Yl**`symbol`, kompilátor vytvoří symbol podobná __ @@_PchSym\_@00@... @`symbol`, kde se třemi tečkami (...) představuje řetězec generované linkeru znaků a ukládá je v objektu modulu. Zdrojový soubor, který kompilujete s Tento předkompilovaných hlaviček odkazuje zadaný symbol, což způsobí, že linkeru zahrnuje modul objektu a jeho ladicí informace z knihovny.  
  
 Použití této možnosti může generovat LNK1211. Pokud zadáte [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) a [/Z7, / zi, /ZI (formát informace ladění)](../../build/reference/z7-zi-zi-debug-information-format.md) možnosti, kompilátor vytvoří předkompilovaný hlavičkový soubor, který obsahuje informace o ladění. Pokud ukládáte předkompilovaných hlaviček v knihovně, pomocí knihovny vytvářet modul objektu a zdrojový kód neodkazuje na žádné funkce, které definuje předkompilovaný hlavičkový soubor, může dojít k chybě.  
  
 Chcete-li problém vyřešit, zadejte **/Yl**`symbol`, kde `symbol` je název libovolný symbolu v knihovně, když vytvoříte předkompilovaný hlavičkový soubor, který neobsahuje žádné definice funkcí. Tato možnost instruuje kompilátor uložit informace o ladění do souboru předkompilovaných hlaviček.  
  
 Další informace o předkompilovaných hlaviček najdete v tématu:  
  
-   [/Y (předkompilované hlavičky)](../../build/reference/y-precompiled-headers.md)  
  
-   [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)