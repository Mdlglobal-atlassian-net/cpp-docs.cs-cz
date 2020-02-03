---
title: /w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (úroveň upozornění)
description: Odkaz na možnosti Microsoft C/C++ Compiler:/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV a/WX.
ms.date: 01/31/2020
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
ms.openlocfilehash: 80b6d0c1fe684de9af62683a75f0fd1107a94089
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972176"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (úroveň upozornění)

Určuje způsob, jakým kompilátor generuje upozornění pro danou kompilaci.

## <a name="syntax"></a>Syntaxe

> **/w**\
> **/W0**\
> **/W1**\
> **/W2**\
> **/W3**\
> **/W4**\
> **/Wall**\
> **/WV**\[ **:** _verze_] \
> **/WX**\
> \_Upozornění_ **/W1**
> \_Upozornění_ **/W2**
> \_Upozornění_ **/w3**
> \_Upozornění_ **/W4**
> \_Upozornění_ **/WD**
> \_Upozornění_ **/We**
> _Upozornění_ /WO

## <a name="remarks"></a>Poznámky

Možnosti upozornění určují, která upozornění kompilátoru se mají zobrazit, a chování upozornění pro celou kompilaci.

Možnosti upozornění a související argumenty jsou popsány v následujících tabulkách:

Možnost | Popis
------ | -----------
**/w** | Potlačí všechna upozornění kompilátoru.
**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4** | Určuje úroveň upozornění vygenerovaných kompilátorem. Platné úrovně upozornění jsou v rozsahu od 0 do 4:<br />**/W0** potlačí všechna upozornění. Je ekvivalentní k **/w**.<br />**/W1** zobrazí upozornění úrovně 1 (závažné). **/W1** je výchozí nastavení v kompilátoru příkazového řádku.<br />**/W2** zobrazí upozornění úrovně 1 a 2 (významné).<br />**/W3** zobrazí upozornění úrovně 1, Level 2 a Level 3 (kvalita výroby). **/W3** je výchozí nastavení v integrovaném vývojovém prostředí.<br />**/W4** zobrazí upozornění úrovně 1, úrovně 2 a 3 a veškerá upozornění úrovně 4 (informativní), která nejsou ve výchozím nastavení vypnutá. Tuto možnost doporučujeme použít k poskytnutí upozornění Lint jako. Pro nový projekt může být nejvhodnější používat **/W4** ve všech kompilacích. Tato možnost pomáhá zajistit nejmenší možné nedostatky v obtížném hledání kódu.
**/Wall** | Zobrazí všechna upozornění zobrazená v **/W4** a všechna ostatní upozornění, která **/W4** neobsahuje – například upozornění, která jsou ve výchozím nastavení vypnutá. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
**/WV**\[ **:** _verze_] | Zobrazí pouze upozornění zavedená ve verzi kompilátoru *verze* a starší. Tuto možnost můžete použít, chcete-li při migraci na novější verzi kompilátoru potlačit nová upozornění v kódu. Umožňuje zachovat existující proces sestavení při jejich opravě. Nepovinná *verze* parametru má formu *NN*\[.\[*mm* . *bbbbb*]], kde *NN* je hlavní číslo verze, *mm* je volitelné číslo dílčí verze a *bbbbb* je volitelným číslem sestavení kompilátoru. Použijte například **/WV: 17** , chcete-li zobrazit pouze upozornění zavedená v aplikaci Visual Studio 2012 (hlavní verze 17) nebo starší. To znamená, že zobrazí upozornění z jakékoli verze kompilátoru, která má hlavní číslo verze 17 nebo méně. Potlačí upozornění zavedená v Visual Studio 2013 (hlavní verze 18) a novější. Ve výchozím nastavení **/WV** používá aktuální číslo verze kompilátoru a nejsou potlačena žádná upozornění. Informace o tom, která upozornění jsou potlačena verzí kompilátoru, naleznete v tématu [Upozornění kompilátoru podle verze kompilátoru](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).
**/WX** | Zpracovává všechna upozornění kompilátoru jako chyby. Pro nový projekt může být nejvhodnější používat **/WX** ve všech kompilacích; řešení všech upozornění zajišťuje nejmenší možné nedostatky v obtížném hledání kódu.<br /><br /> Linker má také možnost **/WX** . Další informace naleznete v tématu [/WX (zpracovávání upozornění linkeru jako chyby)](wx-treat-linker-warnings-as-errors.md).

Následující možnosti se vzájemně vylučují. Poslední možnost, která je zadaná v této skupině, je ta, kterou jste použili:

Možnost | Popis
------ | -----------
**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/w4**_nnnn_ | Nastaví úroveň upozornění pro číslo upozornění určené parametrem _nnnn_. Tyto možnosti umožňují změnit chování kompilátoru pro toto upozornění, když je nastavena konkrétní úroveň upozornění. Tyto možnosti můžete použít v kombinaci s dalšími možnostmi upozornění k vykonání vlastních standardů kódování pro upozornění, nikoli výchozích hodnot poskytovaných sadou Visual Studio.<br /><br /> Například **/w34326** způsobí, že C4326 se vygeneruje jako upozornění úrovně 3 namísto úrovně 1. Pokud kompilujete pomocí možnosti **/w34326** a možnosti **/W2** , není vygenerováno upozornění C4326.
**/wd**_nnnn_ | Potlačí upozornění kompilátoru, které je určeno v rámci _nnnn_.<br /><br /> Například **/wd4326** potlačí upozornění kompilátoru na C4326.
**/We**_nnnn_ | Zpracovává upozornění kompilátoru, které je určeno jako chyba v rámci rozhraní _nnnn_ .<br /><br /> Například **/we4326** způsobí, že se číslo upozornění C4326, které kompilátor považuje za chybu.
**/WO**_nnnn_ | Oznamuje upozornění kompilátoru, které je určeno _nnnn_ pouze jednou.<br /><br /> Například **/wo4326** způsobí, že upozornění C4326 bude oznámeno pouze jednou, při prvním výskytu kompilátorem.

Pokud při vytváření předkompilované hlavičky použijete nějaké možnosti upozornění, tato nastavení se zachovají. Použití předkompilované hlavičky znovu vloží stejné možnosti upozornění. Chcete-li přepsat možnosti upozornění předkompilovaných hlaviček, nastavte jinou možnost upozornění na příkazovém řádku.

Můžete použít direktivu [upozornění #pragma](../../preprocessor/warning.md) k řízení úrovně upozornění, která je hlášena v době kompilace v určitých zdrojových souborech.

Direktivy pragma warning ve zdrojovém kódu nejsou ovlivněny možností **/w** .

[Dokumentace k chybám sestavení](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) popisuje výstrahy a úrovně varování a označuje, proč se některé příkazy nemůžou kompilovat podle vašich záměrů.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Nastavení možností kompilátoru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Chcete-li nastavit možnosti **/W0**, **/W1**, **/W2**, **/w3**, **/W4**, **/Wall**, **/WV**, **/WX**nebo **/WX-** , vyberte možnost **Vlastnosti konfigurace** > **CC++ /**  > **Obecné**.

   - Chcete-li nastavit možnosti **/W0**, **/W1**, **/W2**, **/w3**, **/W4**nebo **/Wall** , upravte vlastnost **úroveň upozornění** .

   - Chcete-li nastavit možnosti **/WX** nebo **/WX-** , upravte vlastnost **považovat upozornění za chyby** .

   - Chcete-li nastavit verzi pro možnost **/WV** , zadejte číslo verze kompilátoru ve vlastnosti **verze upozornění** .

1. Chcete-li nastavit možnosti **/WD** nebo **/We** , vyberte položku **Vlastnosti konfigurace** > stránce **Upřesnit** vlastnost **jazyka C/C++**  > .

   - Chcete-li nastavit možnost **/WD** , vyberte ovládací prvek rozevírací seznam **Zakázat specifická upozornění** a pak zvolte možnost **Upravit**. Do pole upravit v dialogovém okně **Zakázat specifická upozornění** zadejte číslo upozornění. Chcete-li zadat více než jedno upozornění, oddělte hodnoty pomocí středníku ( **;** ). Chcete-li například zakázat C4001 i C4010, zadejte **4001; 4010**. Kliknutím na **tlačítko OK** uložte změny a vraťte se do dialogového okna **stránky vlastností** .

   - Chcete-li nastavit možnost **/We** , vyberte ovládací prvek rozevírací seznam pro **považovat specifická upozornění jako chyby** a pak zvolte možnost **Upravit**. Do pole upravit v dialogovém okně **zpracovat konkrétní upozornění jako chyby** zadejte číslo upozornění. Chcete-li zadat více než jedno upozornění, oddělte hodnoty pomocí středníku ( **;** ). Pokud například chcete s C4001 a C4010 nakládat jako s chybami, zadejte **4001; 4010**. Kliknutím na **tlačítko OK** uložte změny a vraťte se do dialogového okna **stránky vlastností** .

1. Chcete-li nastavit možnost **/WO** , vyberte položku **Vlastnosti konfigurace** > stránce vlastností **příkazového řádku** **jazyka C/C++**  > . Zadejte možnost kompilátoru do pole **Další možnosti** .

1. Kliknutím na **tlačítko OK** uložte změny.

### <a name="to-set-the-compiler-option-programmatically"></a>Chcete-li nastavit možnost kompilátoru programově

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

\ [možností kompilátoru MSVC](compiler-options.md)
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
