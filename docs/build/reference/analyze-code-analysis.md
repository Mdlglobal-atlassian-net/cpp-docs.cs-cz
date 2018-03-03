---
title: "-analyze (Analýza kódu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
dev_langs:
- C++
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba76ddd10866e414d9817f628c7a1aec019964de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="analyze-code-analysis"></a>/analyze (Analýza kódu)
Umožňuje zadat parametry pro analýzu a řízení kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only]  
```  
  
## <a name="arguments"></a>Arguments  
 /analyze  
 Zapne analýzu ve výchozím režimu. Výstup analýzy přejde na **výstup** okno jako další chybové zprávy. Použití **/ analyze –** explicitně vypnout analýzy.  
  
 /analyze:WX-  
 Určení **/ analyze: WX –** znamená, že upozornění analýzy kódu nejsou považovány za chyby při kompilaci pomocí **wdn**. Další informace najdete v tématu [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, nebo jsme /wo, /Wv, wdn (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md).  
  
 / analyze: protokolu`filename`  
 Analyzátor podrobné výsledky se zapisují jako XML soubor, který je zadán `filename`.  
  
 /analyze:quiet  
 Vypnutím analyzátor výstup do **výstup** okno.  
  
 / analyze: velikost zásobníku`number`  
 `number` Parametr, který se používá tato možnost určuje velikost v bajtech, pro které upozornění rámce zásobníku [C6262](/visualstudio/code-quality/c6262) se vygeneruje. Pokud tento parametr není zadán, má rámec zásobníku ve výchozím nastavení velikost 16 kB.  
  
 / analyze: max_paths`number`  
 `number` Parametr, který se používá tato možnost určuje maximální počet cesty kódu má být analyzován. Pokud tento parametr není zadán, je ve výchozím nastavení tento počet 256. Vyšší hodnoty provádějí důkladnější kontrolu, ale analýza může trvat déle.  
  
 /analyze:only  
 Kompilátor zpravidla generuje kód a po spuštění analýzy provádí další kontrolu syntaxe. **/ Analyze: pouze** možnost vypne Tento průchod generování kódu; díky tomu analysis rychlejší, ale nejsou vygenerované kompilace chyby a upozornění, které může byly zjištěny předejte generování kódu kompilátoru. Pokud program obsahuje chyby generování kódu, mohou být výsledky analýzy nespolehlivé; proto doporučujeme, abyste tento parametr použili pouze v případě, že kód již prošel kontrolou syntaxe generování kódu bez chyb.  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [analýzy kódu pro C/C++ – přehled](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) a [analýzy kódu pro C/C++ upozornění](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **analýza kódu** uzlu.  
  
4.  Vyberte **Obecné** stránku vlastností.  
  
5.  Změňte jednu nebo více **analýza kódu** vlastnosti.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)