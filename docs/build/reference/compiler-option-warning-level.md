---
title: "-w,-W0,-W1, - W2,-W3, - W4,-w1,-w2,-w3,-w4,-Wall, -wd,-jsme -wo,. -Wv, - WX (úroveň upozornění) | Microsoft Docs"
ms.custom: 
ms.date: 01/31/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarningLevel
- VC.Project.VCCLWCECompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarnAsError
- VC.Project.VCCLWCECompilerTool.WarnAsError
- /wx
- VC.Project.VCCLWCECompilerTool.WarningLevel
- /wall
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- /Wv
- /w0
- /w1
- /w2
- /w3
- /w4
- /wd
- /we
- /wo
dev_langs:
- C++
helpviewer_keywords:
- /W1 compiler option [C++]
- w compiler option [C++]
- -wo compiler option [C++]
- Warning Level compiler option
- W1 compiler option [C++]
- -we compiler option [C++]
- /WX compiler option [C++]
- -wd compiler option [C++]
- WX compiler option [C++]
- wo compiler option [C++]
- Wall compiler option [C++]
- /w compiler option
- W2 compiler option [C++]
- -W2 compiler option [C++]
- wd compiler option [C++]
- /we compiler option [C++]
- we compiler option [C++]
- -W1 compiler option [C++]
- -W4 compiler option [C++]
- -Wall compiler option [C++]
- /Wall compiler option [C++]
- -W0 compiler option [C++]
- W0 compiler option [C++]
- -WX compiler option [C++]
- /wo compiler option [C++]
- W4 compiler option [C++]
- W3 compiler option [C++]
- /wd compiler option [C++]
- warnings, as errors compiler option
- /W3 compiler option [C++]
- /W0 compiler option [C++]
- /W4 compiler option [C++]
- -W3 compiler option [C++]
- -w compiler option [C++]
- /W2 compiler option [C++]
- /Wv compiler option [C++]
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be7e86065b52ee5c55058b9a672f3bf543454cf8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, nebo jsme /wo, /Wv, wdn (úroveň upozornění)

Určuje, jak kompilátor generuje upozornění pro danou kompilace.

## <a name="syntax"></a>Syntaxe

> **/w**  
> **/W0**  
> **/W1**  
> **/W2**  
> **/W3**  
> **/W4**  
> **/Wall**  
> **/WV**\[**:**_verze_]  
> **/WX**  
> **/W1**_upozornění_  
> **/W2**_upozornění_  
> **/w3**_upozornění_  
> **/W4**_upozornění_  
> **/WD**_upozornění_  
> **/we**_upozornění_  
> **/wo**_upozornění_  

## <a name="remarks"></a>Poznámky

Zadejte možnosti upozornění které kompilátoru upozornění k zobrazení a chování upozornění pro celý kompilace.

V následující tabulce jsou popsány možnosti upozornění a související argumenty:

|Možnost|Popis|
------------|-----------------|
|**/w**|Potlačí všechny upozornění kompilátoru.|
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|Určuje úroveň upozornění, která má být vygenerován kompilátorem. Platný upozornění úrovně rozsahu od 0 do 4:<br />**/ W0** potlačí všechny výstrahy. Jde o ekvivalent **/w**.<br />**/ W1** zobrazí upozornění úrovně 1 (závažné). **/ W1** je výchozí nastavení v kompilátoru příkazového řádku.<br />**/ W2** zobrazí úroveň 1 a 2 (důležité) upozornění úrovně.<br />**/ W3** zobrazí úrovně 1, úroveň 2 a 3 (produkční kvality) upozornění úrovně. **/ W3** je výchozí nastavení v IDE.<br />**/ W4** zobrazí úrovně 1, úroveň 2 a 3 upozornění úrovně a všechny úrovně 4 (informativní) upozornění, která nejsou ve výchozím nastavení vypnuté. Doporučujeme, abyste pomocí této možnosti můžete zadat jako hadříkem upozornění. Pro nový projekt, může být nejvhodnější použít **/W4** v všechny kompilace; tím bude zajištěno, nejmenší počet defektů možné pevný najít kódu.|
|**/Wall**|Zobrazí všechny výstrahy zobrazuje **/W4** a všechny další upozornění, **/W4** nezahrnuje – například upozornění, které jsou ve výchozím nastavení vypnuté. Další informace najdete v tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|**/WV**\[**:**_verze_]|Zobrazí pouze upozornění uvedených ve verzi kompilátoru *verze* a starší. Tuto možnost můžete použít k potlačení nové upozornění v kódu při migraci na novější verzi kompilátoru a zachování stávajícího procesu sestavení během opravit je. Volitelný parametr *verze* podobu  *nn* [. *mm*[. *bbbbb*]] kde  *nn*  je hlavní číslo verze, *mm* je číslo podverze volitelné a *bbbbb* je číslo sestavení volitelné kompilátoru. Například použít */Wv:17* zobrazit upozornění zavedená v sadě Visual Studio 2012 (to znamená, všechny verze kompilátoru, která má hlavní číslo verze 17) nebo dřívější, ale potlačení upozornění zavedená v sadě Visual Studio 2013 (hlavní verze 18) a novější. Ve výchozím nastavení **/Wv** používá, které jsou potlačovány aktuální číslo verze kompilátoru a žádné upozornění. Informace o tom, které jsou potlačovány upozornění kompilátoru verze najdete v tématu [upozornění kompilátoru kompilátoru verzí](../..//error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).|
|**/WX**|Zpracovává všechny kompilátoru upozornění jako chyby. Pro nový projekt, může být nejvhodnější použít **wdn** všechny kompilace; vyřešení všech upozornění zajišťuje nejmenší počet defektů možné pevný najít kódu.<br /><br /> Linkeru má také **wdn** možnost. Další informace najdete v tématu [wdn (považovat upozornění Linkeru jako chyby)](../../build/reference/wx-treat-linker-warnings-as-errors.md).|
|**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/w4**_nnnn_|Nastaví úroveň pro upozornění pro upozornění číslo zadané parametrem  _nnnn_ . Díky tomu můžete změnit chování kompilátoru pro upozornění, že pokud je konkrétní úroveň upozornění nastavena. Tyto možnosti můžete použít v kombinaci s jinými možnostmi upozornění k vynucení vlastní kódování standardy pro upozornění, místo výchozího pravidla stanovená v sadě Visual Studio.<br /><br /> Například **/w34326** způsobí, že C4326 má být vygenerován jako upozornění úroveň 3 místo úroveň 1. Pokud zkompilujete pomocí obou **/w34326** možnost a **/W2** možnost upozornění C4326 nevygenerovala.|
|**/wd**_nnnn_|Upozornění kompilátoru, která je zadána potlačí  _nnnn_ .<br /><br /> Například **/wd4326** potlačí kompilátoru upozornění C4326.|
|**/we**_nnnn_|Upozornění kompilátoru, která je zadána zpracovává  _nnnn_  za chybu.<br /><br /> Například **/we4326** způsobí, že číslo upozornění C4326 kompilátorem považován za chybu.|
|**/wo**_nnnn_|Sestavy kompilátoru se tedy upozornění určeného  _nnnn_  pouze jednou.<br /><br /> Například **/wo4326** příčiny upozornění C4326 k nahlášena pouze jednou, první je došlo kompilátorem.|

Pokud použijete některou z možností upozornění při vytváření předkompilovaných hlaviček pomocí [/Yc](../../build/reference/yc-create-precompiled-header-file.md) možnost jakékoli použití předkompilovaných hlaviček pomocí [/Yu](../../build/reference/yu-use-precompiled-header-file.md) možnost způsobí, že tyto stejné možnosti upozornění, pokud má být znovu. Můžete přepsat upozornění možnostmi nastavenými v předkompilovaných hlaviček pomocí jiné možnosti upozornění na příkazovém řádku.

Můžete použít [#pragma – upozornění](../../preprocessor/warning.md) – direktiva řídit úroveň upozornění, který je uvedený v době kompilace v konkrétní zdrojové soubory.

Direktivy pragma upozornění ve zdrojovém kódu jsou nemá vliv **/w** možnost.

[Sestavení chyby dokumentaci](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) popisuje upozornění a úrovně varování a označuje, proč nemusí některé příkazy zkompilovat jako, který chcete.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Nastavení možností kompilátoru ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Chcete-li nastavit **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, **/horní**m **/Wv**, **wdn** nebo **/WX-** možnosti, vyberte **vlastnosti konfigurace** > **C / C++** > **Obecné** stránku vlastností.

   - Chcete-li nastavit **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, nebo **/horní** upravit možnosti, **úroveň pro upozornění** vlastnost.

   - Chcete-li nastavit **wdn** nebo **/WX-** upravit možnosti, **zpracování upozornění jako chyby** vlastnost.

   - Nastavit verzi **/Wv** možnost, zadejte číslo verze kompilátoru v **upozornění verze** vlastnost.

1. Chcete-li nastavit **/wd** nebo **/we** možnosti, vyberte **vlastnosti konfigurace** > **C/C++**  >   **Rozšířené** stránku vlastností.

   - Chcete-li nastavit **/wd** vyberte možnost **zakázat konkrétní varování** vlastnost rozevírací nabídku ovládací prvek a potom zvolte **upravit**. Do textového pole v **zakázat konkrétní varování** dialogové okno, zadejte číslo upozornění. Pokud chcete zadat více než jeden upozornění, oddělte hodnoty středník (**;**). Například pokud chcete zakázat C4001 a C4010, zadejte **4001; 4010**. Zvolte **OK** chcete uložit provedené změny a vrátit **stránky vlastností** dialogové okno.

   - Chcete-li nastavit **/we** možnost, vyberte **považovat konkrétní upozornění jako chyby** vlastnost rozevírací nabídku ovládací prvek a potom zvolte **upravit**. Do textového pole v **považovat konkrétní upozornění jako chyby** dialogové okno, zadejte číslo upozornění. Pokud chcete zadat více než jeden upozornění, oddělte hodnoty středník (**;**). Například považovat za C4001 a C4010 chyby, zadejte **4001; 4010**. Zvolte **OK** chcete uložit provedené změny a vrátit **stránky vlastností** dialogové okno.

1. Chcete-li nastavit **/wo** vyberte možnost **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** Stránka vlastností. Zadejte možnost kompilátoru v **další možnosti** pole.

1. Zvolte **OK** uložte provedené změny.

### <a name="to-set-the-compiler-option-programmatically"></a>Nastavení možnosti kompilátoru prostřednictvím kódu programu

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>, a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
