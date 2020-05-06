---
title: /Yl (Vložit referenci PCH do ladicí knihovny)
ms.date: 01/29/2018
f1_keywords:
- /yl
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
ms.openlocfilehash: 816ba66c94e616407a8891cd149a41e44e29358d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825714"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Vložit referenci PCH do ladicí knihovny)

Možnost **/yl** vygeneruje v souboru předkompilované hlavičky jedinečný symbol a odkaz na tento symbol je vložen ve všech objektových souborech, které používají předkompilovanou hlavičku.

## <a name="syntax"></a>Syntaxe

>**/Yl**\
>**/Yl**_Název_ /yl\
>**Parametr/yl-**

### <a name="arguments"></a>Argumenty

*Jméno*<br/>
Volitelný název, který se používá jako součást jedinečného symbolu.

*\-*<br/>
Pomlčka (-) explicitně zakáže možnost kompilátoru **/yl** .

## <a name="remarks"></a>Poznámky

Možnost kompilátoru **/yl** vytvoří jedinečnou definici symbolu v souboru předkompilované hlavičky vytvořené pomocí možnosti [/YC](yc-create-precompiled-header-file.md) . Odkazy na tento symbol jsou automaticky vloženy do všech souborů, které obsahují předkompilovanou hlavičku pomocí možnosti kompilátoru [/Yu](yu-use-precompiled-header-file.md) . Možnost **/yl** je ve výchozím nastavení povolená, když se **/YC** používá k vytvoření předkompilovaného hlavičkového souboru.

Možnost **/Yl**_název_ /yl se používá k vytvoření identifikovatelné značky v souboru předkompilované hlavičky. Kompilátor používá argument *název* jako součást názvu upraveného symbolu, který vytvoří, podobně jako `__@@_PchSym_@00@...@name`, kde tři tečky (...) představují jedinečný řetězec znaků generovaných kompilátorem. Pokud je argument *Name* vynechán, kompilátor automaticky vygeneruje název symbolu. Obvykle není nutné znát název symbolu. Pokud však váš projekt používá více než jeden soubor předkompilované hlavičky, možnost_názvu_ **/yl**může být užitečná k určení, které objekty soubory používají danou předkompilovanou hlavičku. Pokud chcete najít odkaz na symbol v souboru s výpisem paměti, můžete použít *název* jako hledaný řetězec.

**Parametr/yl-** zakáže výchozí chování a nevloží identifikační symbol do souboru předkompilované hlavičky. Zkompilované soubory, které obsahují tuto předkompilovanou hlavičku, nezískají společný odkaz na symbol.

Pokud není zadán parametr **/YC** , nebude mít žádná možnost **/yl** žádný vliv, ale pokud je zadaný, musí se shodovat s možností **/yl** předané při zadání **/YC** .

Použijete-li možnosti **parametr/yl-**, **/YC** a [/Z7](z7-zi-zi-debug-information-format.md) k sestavení předkompilovaného hlavičkového souboru, informace o ladění jsou uloženy v souboru objektu pro zdrojový soubor, který slouží k vytvoření předkompilované hlavičky, nikoli samostatného souboru PDB. Je-li tento soubor objektu následně součástí knihovny, může dojít k chybám [linkerů LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) nebo k upozornění [linkerů lnk4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) v sestaveních, která používají tuto knihovnu a soubor předkompilované hlavičky, pokud zdrojový soubor použitý k vytvoření souboru předkompilované hlavičky nedefinuje žádné symboly. Linker může vyloučí soubor objektu z odkazu spolu s přidruženými ladicími informacemi, pokud není v klientském souboru odkazováno na žádný objekt v objektu Library. Chcete-li tento problém vyřešit, zadejte **/yl** (nebo odeberte možnost **parametr/yl-** ) při použití **/YC** k vytvoření souboru předkompilované hlavičky. Tím se zajistí, že se soubor objektu z knihovny, která obsahuje ladicí informace, bude v sestavení propojen.

Další informace o předkompilovaných hlavičkách naleznete v tématu:

- [/Y (předkompilované hlavičky)](y-precompiled-headers.md)

- [Předkompilované hlavičkové soubory](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Konfigurace** > **příkazového řádku** **C/C++** > .

1. Přidejte možnost kompilátoru_název_ **/yl**do pole **Další možnosti** . Kliknutím na **tlačítko OK** uložte změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
