---
title: -errorReport (sestava s chybami kompilátoru) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
- /errorreport
dev_langs:
- C++
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67e87143d31de98039f5d679c102a5815dd87abb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377245"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (sestava s interními chybami kompilátoru)
Umožňuje zadat informace o chybě (LED) interní kompilátoru přímo společnosti Microsoft.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## <a name="arguments"></a>Arguments  
 **None**  
 Zprávy o chybách interní kompilátoru nebudou shromažďovány nebo odesílány do společnosti Microsoft.  
  
 **prompt**  
 Dotaz, zda chcete poslat zprávu, když obdrží vnitřní chyby kompilátoru. **řádku** je výchozí hodnota při kompilaci aplikace ve vývojovém prostředí.  
  
 **Fronty**  
 Fronty zprávy o chybách. Když se přihlásíte pomocí oprávnění správce, tak, aby ohlásíte případných selhání od posledního byly přihlášení, zobrazí se okno (nezobrazí se výzva k odeslání zpráv o selhání více než jednou za tři dní). **fronty** je výchozí hodnota při kompilaci aplikace na příkazovém řádku.  
  
 **Odeslat**  
 Pokud je povoleno oznamování pomocí nastavení systému zasílání zpráv o chybách systému Windows automaticky odesílá zprávy o chybách interní kompilátoru společnosti Microsoft.  
  
## <a name="remarks"></a>Poznámky  
 Vnitřní chyba kompilátoru (LED) nastává kompilátor nemůže zpracovat soubor zdrojového kódu. Když dojde LED, kompilátor nevytváří výstupní soubor nebo užitečnou diagnostiku, můžete použít k opravě kódu.  
  
 V dřívějších verzích když jste získali LED, jste doporučujeme, aby volání služby Microsoft Product Support Services nahlásit problém. S **/errorreport**, můžete zadat informace LED přímo společnosti Microsoft. Zprávy o chybách může pomoct zlepšit budoucí vydání kompilátoru.  
  
 Schopnost uživatele odesílat zprávy závisí na oprávnění zásad počítače a uživatele.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **Upřesnit** stránku vlastností.  
  
4.  Změnit **zasílání zpráv o chybách** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)