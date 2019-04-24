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
ms.openlocfilehash: 92e47836e0fdae077defa0fe35b515ab4ca20a66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316246"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Vložit referenci PCH do ladicí knihovny)

**/Yl** možnost generuje jedinečný symbol v předkompilovaného hlavičkového souboru a odkaz na tento symbol se vloží do všech objektových souborů, které používají předkompilované hlavičky.

## <a name="syntax"></a>Syntaxe

>**/Yl**
> **/Yl**_název_
> **/Yl-**

### <a name="arguments"></a>Arguments

*Jméno*<br/>
Volitelný název používá jako součást jedinečný symbol.

*\-*<br/>
Explicitně zakáže pomlčkou (-) **/Yl** – možnost kompilátoru.

## <a name="remarks"></a>Poznámky

**/Yl** – možnost kompilátoru vytvoří definici jedinečný symbolů v souboru předkompilované hlavičky vytvářeny instalační sadou [/Yc](yc-create-precompiled-header-file.md) možnost. Odkazy na tento symbol se automaticky vloží do všech souborů, které zahrnují předkompilované hlavičky s použitím [/Yu](yu-use-precompiled-header-file.md) – možnost kompilátoru. **/Yl** možnost je povolená ve výchozím nastavení při **/Yc** slouží k vytvoření souboru předkompilované hlavičky.

**/Yl**_název_ možnost se používá k vytvoření identifikovatelné symbolů v souboru předkompilované hlavičky. Kompilátor používá *název* argument jako součást názvu upravený symbol vytvoří, podobně jako `__@@_PchSym_@00@...@name`, kde řetězec znaků, tlačítko se třemi tečkami (...) představuje jedinečný generovaný kompilátorem. Pokud *název* je tento argument vynechán, kompilátor automaticky vygeneruje název symbolu. Za normálních okolností není potřeba znát název symbolu. Ale pokud váš projekt používá více než jeden soubor předkompilované hlavičky **/Yl**_název_ možnost může být užitečná k určení, který objekt soubory použití, které předkompilovanou hlavičku. Můžete použít *název* jako hledaný řetězec pro odkaz symbol najít v souboru výpisu paměti.

**/Yl-** zakazuje výchozí chování a nevystavuje identifikace symbolů v souboru předkompilované hlavičky. Zkompilované soubory, které zahrnují této předkompilované hlavičky Nezískávat běžné symbol odkazu.

Při **/Yc** nezadáte, všechny **/Yl** možnost nemá žádný vliv, ale pokud určena, musí se shodovat žádné **/Yl** možnost předána, když **/Yc** je zadat.

Pokud používáte **/Yl-**, **/Yc** a [/Z7](z7-zi-zi-debug-information-format.md) možnosti k sestavení předkompilovaného hlavičkového souboru, informace o ladění jsou uloženy v souboru objekt použitý k vytvoření zdrojového souboru Předkompilované hlavičky, spíše než samostatné PDB soubor. Pokud tento soubor objektu poté je proveden součástí knihovny, [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) chyby nebo [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) upozornění může dojít v sestavení, které používají tuto knihovnu a předkompilovaného souboru hlaviček, pokud zdrojový soubor použili k vytvoření soubor předkompilované hlavičky nedefinuje žádné symboly samotný. Linker může vyloučit soubor objektu z odkazu, který spolu s související informace pro ladění, když nic do souboru objektu je odkazováno v klientovi knihovny. Chcete-li tento problém vyřešit, zadejte **/Yl** (nebo odebrat **/Yl-** možnost) při použití **/Yc** k vytvoření souboru předkompilované hlavičky. Tím se zajistí, že se soubor objektu z knihovny, který obsahuje informace o ladění propojí ve vašem buildu.

Další informace o předkompilovaných hlaviček naleznete v tématu:

- [/Y (předkompilované hlavičky)](y-precompiled-headers.md)

- [Předkompilované soubory hlaviček](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Přidat **/Yl**_název_ – možnost kompilátoru v **další možnosti** pole. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
