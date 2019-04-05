---
title: /w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)
ms.date: 01/31/2018
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
ms.openlocfilehash: 7b5c19c95cff3058bb3dcc6640f8ab07cf01edd6
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040066"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)

Určuje, jak kompilátor vygeneruje upozornění pro dané kompilace.

## <a name="syntax"></a>Syntaxe

> **/w**
>  **/W0**
>  **/W1**
>  **/W2**
> **w3** 
>  **/W4**
>  **/wall**
>  **/WV:**\[**:**_verze _] **/WX**
>  **/w1**_upozornění_
>  **/w2** _ upozornění_
> **w3**_upozornění_
>  **/W4**_upozornění_ 
>  **/wd**_upozornění_
>  **/we**_upozornění_ 
>  **/wo**_upozornění_

## <a name="remarks"></a>Poznámky

Možnosti upozornění určují která kompilátoru upozornění k zobrazení a chování upozornění pro celý kompilace.

Možnosti upozornění a související argumenty jsou popsány v následující tabulce:

|Možnost|Popis|
------------|-----------------|
|**/w**|Potlačí všechna upozornění kompilátoru.|
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|Určuje úroveň upozornění generovaný kompilátorem. Platné upozornění úrovně rozsahu od 0 do 4:<br />**/ W0** potlačí všechna upozornění. Jedná se o ekvivalent k **/w**.<br />**/ W1** zobrazí upozornění úrovně 1 (závažnost). **/ W1** je výchozí nastavení kompilátoru příkazového řádku.<br />**/ W2** zobrazí úrovně 1 a upozornění úrovně 2 (důležité).<br />**/ W3** zobrazí na úrovni 1, úroveň 2 a 3 (produkční kvality) upozornění úrovně. **/ W3** je výchozí nastavení v integrovaném vývojovém prostředí.<br />**/ W4** zobrazí na úrovni 1, 2, úroveň a úroveň upozornění 3 a všechny úrovně 4 (informativní) upozornění, které nejsou ve výchozím nastavení vypnuta. Doporučujeme, abyste pomocí této možnosti můžete zadat lint jako upozornění. Pro nový projekt, může být vhodné použít **/W4** při všech kompilacích; tím se zajistí nejmíň vad kódu možné obtížné najít.|
|**/Wall**|Zobrazí všechna upozornění zobrazený **/W4** a všechna ostatní upozornění, která **/W4** nezahrnuje – například upozornění, které jsou ve výchozím nastavení vypnuta. Další informace najdete v tématu [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|**/ WV:**\[**:**_verze_]|Zobrazí pouze upozornění zavedená ve verzi kompilátoru *verze* a starší. Tato možnost slouží k potlačení nová upozornění v kódu při migraci na novější verzi kompilátoru a zachovat existující procesu sestavení v době, kdy je. Volitelný parametr *verze* má podobu *nn*[. *mm*[. *bbbbb*]] Pokud *nn* je číslo hlavní verze *mm* je volitelné vedlejší číslo verze, a *bbbbb* je číslo volitelné sestavení kompilátor. Například použít */Wv:17* zobrazit upozornění zavedená v sadě Visual Studio 2012 (to znamená všechny verze kompilátoru, který obsahuje číslo hlavní verze 17) nebo starší, ale potlačit upozornění zavedená v sadě Visual Studio 2013 (hlavní verze 18) a novější. Ve výchozím nastavení **/WV:** používá aktuální číslo verze kompilátoru a žádné upozornění jsou potlačeny. Informace o tom, které jsou potlačovány upozornění podle verze kompilátoru najdete v tématu [upozornění kompilátoru podle verze kompilátoru](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).|
|**/WX**|Zpracuje všechna upozornění kompilátoru jako chyby. Pro nový projekt, může být vhodné použít **/WX** při všech kompilacích; vyřešením všech upozornění zajistíte nejmíň vad kódu možné obtížné najít.<br /><br /> Propojovací program má také **/WX** možnost. Další informace najdete v tématu [/WX (zpracovávat upozornění Linkeru jako chyb)](wx-treat-linker-warnings-as-errors.md).|
|**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/w4**_nnnn_|Nastaví úroveň upozornění pro upozornění číslo určené parametrem _nnnn_. Tímto způsobem můžete změnit chování kompilátoru tohoto upozornění při nastavit konkrétní úroveň pro upozornění. Tyto možnosti můžete použít v kombinaci s jinými možnostmi upozornění k vynucení vlastní kódování standardy pro upozornění, místo výchozí hodnoty poskytovaný sadou Visual Studio.<br /><br /> Například **/w34326** způsobí, že C4326 generován jako upozornění úrovně 3 namísto úrovně 1. Pokud kompilujete pomocí **/w34326** možnost a **/W2** možnost C4326 negeneruje upozornění.|
|**/wd**_nnnn_|Potlačí případná upozornění kompilátoru, která je zadána _nnnn_.<br /><br /> Například **/wd4326** potlačí upozornění C4326 kompilátoru.|
|**/we**_nnnn_|Upozornění kompilátoru, která je zadána zpracovává _nnnn_ za chybu.<br /><br /> Například **/we4326** způsobí, že číslo upozornění C4326 zacházet jako chyba v kompilátoru.|
|**/wo**_nnnn_|Sestavy upozornění kompilátoru, který je určený _nnnn_ pouze jednou.<br /><br /> Například **/wo4326** způsobí, že upozornění C4326 hlášeno pouze jednou, při prvním jeho zjištění kompilátorem.|

Pokud použijete některou z možností upozornění při vytváření předkompilované hlavičky s použitím [/Yc](yc-create-precompiled-header-file.md) možnost jakékoli použití předkompilované hlavičky s použitím [/Yu](yu-use-precompiled-header-file.md) možnost způsobí, že tyto stejné možnosti upozornění platit znovu. Upozornění možnostmi nastavenými v předkompilované hlavičce pomocí jiné možnosti upozornění na příkazovém řádku můžete přepsat.

Můžete použít [varování #pragma](../../preprocessor/warning.md) směrnice řídit úroveň upozornění, který je uvedena v době kompilace v konkrétní zdrojové soubory.

Direktivy pragma upozornění ve zdrojovém kódu nejsou ovlivněny **/w** možnost.

[Vytvářet dokumentaci chyby](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) popisuje upozornění a úrovně varování a označuje, proč nemusí zkompilovat určité příkazy tak, jak zamýšlíte.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Chcete-li nastavit možnosti kompilátoru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Chcete-li nastavit **/W0**, **/W1**, **/W2**, **w3**, **/W4**, **/Wall**, **/WV:**, **/WX** nebo **/WX-** možnosti, vyberte **vlastnosti konfigurace** > **C / C++** > **Obecné** stránku vlastností.

   - Chcete-li nastavit **/W0**, **/W1**, **/W2**, **w3**, **/W4**, nebo **/Wall** upravit možnosti, **úroveň pro upozornění** vlastnost.

   - Chcete-li nastavit **/WX** nebo **/WX-** upravit možnosti, **zpracování upozornění jako chyby** vlastnost.

   - Nastavení jsou ve verzi **/WV:** možnost, zadejte číslo verze kompilátoru **verze upozornění** vlastnost.

1. Chcete-li nastavit **/wd** nebo **/we** možnosti, vyberte **vlastnosti konfigurace** > **C/C++**  >   **Pokročilé** stránku vlastností.

   - Chcete-li nastavit **/wd** možnosti, vyberte **zakázat specifická upozornění** vlastnost ovládací prvek rozevírací seznam a zvolte **upravit**. V textovém poli **zakázat specifická upozornění** dialogové okno, zadejte číslo varování. Pokud chcete zadat více než jedno upozornění, oddělte hodnoty středníky (**;**). Například chcete-li zakázat C4001 a C4010, zadejte **4001; 4010**. Zvolte **OK** uložte provedené změny a vraťte **stránky vlastností** dialogového okna.

   - Chcete-li nastavit **/we** volby, vyberte **považovat konkrétní upozornění jako chyby** vlastnost ovládací prvek rozevírací seznam a zvolte **upravit**. V textovém poli **považovat konkrétní upozornění jako chyby** dialogové okno, zadejte číslo varování. Pokud chcete zadat více než jedno upozornění, oddělte hodnoty středníky (**;**). Například C4001 a C4010 nakládat jako s chybami, zadejte **4001; 4010**. Zvolte **OK** uložte provedené změny a vraťte **stránky vlastností** dialogového okna.

1. Chcete-li nastavit **/wo** možnosti, vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** Stránka vlastností. Zadáním možnosti kompilátoru v **další možnosti** pole.

1. Zvolte **OK** uložte provedené změny.

### <a name="to-set-the-compiler-option-programmatically"></a>Programové nastavení parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>, a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
