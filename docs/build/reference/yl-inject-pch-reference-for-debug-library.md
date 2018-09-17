---
title: -Yl (Vložit referenci PCH knihovny ladění) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yl
dev_langs:
- C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 378d8e6b43a391c6d94c55b278bc71789981d9e3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712371"
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

**/Yl** – možnost kompilátoru vytvoří definici jedinečný symbolů v souboru předkompilované hlavičky vytvářeny instalační sadou [/Yc](../../build/reference/yc-create-precompiled-header-file.md) možnost. Odkazy na tento symbol se automaticky vloží do všech souborů, které zahrnují předkompilované hlavičky s použitím [/Yu](../../build/reference/yu-use-precompiled-header-file.md) – možnost kompilátoru. **/Yl** možnost je povolená ve výchozím nastavení při **/Yc** slouží k vytvoření souboru předkompilované hlavičky.

**/Yl**_název_ možnost se používá k vytvoření identifikovatelné symbolů v souboru předkompilované hlavičky. Kompilátor používá *název* argument jako součást názvu upravený symbol vytvoří, podobně jako `__@@_PchSym_@00@...@name`, kde řetězec znaků, tlačítko se třemi tečkami (...) představuje jedinečný generovaný kompilátorem. Pokud *název* je tento argument vynechán, kompilátor automaticky vygeneruje název symbolu. Za normálních okolností není potřeba znát název symbolu. Ale pokud váš projekt používá více než jeden soubor předkompilované hlavičky **/Yl**_název_ možnost může být užitečná k určení, který objekt soubory použití, které předkompilovanou hlavičku. Můžete použít *název* jako hledaný řetězec pro odkaz symbol najít v souboru výpisu paměti.

**/Yl-** zakazuje výchozí chování a nevystavuje identifikace symbolů v souboru předkompilované hlavičky. Zkompilované soubory, které zahrnují této předkompilované hlavičky Nezískávat běžné symbol odkazu.

Při **/Yc** nezadáte, všechny **/Yl** možnost nemá žádný vliv, ale pokud určena, musí se shodovat žádné **/Yl** možnost předána, když **/Yc** je zadat.

Pokud používáte **/Yl-**, **/Yc** a [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) možnosti k sestavení předkompilovaného hlavičkového souboru, informace o ladění jsou uloženy v souboru objekt použitý k vytvoření zdrojového souboru Předkompilované hlavičky, spíše než samostatné PDB soubor. Pokud tento soubor objektu poté je proveden součástí knihovny, [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) chyby nebo [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) upozornění může dojít v sestavení, které používají tuto knihovnu a předkompilovaného souboru hlaviček, pokud zdrojový soubor použili k vytvoření soubor předkompilované hlavičky nedefinuje žádné symboly samotný. Linker může vyloučit soubor objektu z odkazu, který spolu s související informace pro ladění, když nic do souboru objektu je odkazováno v klientovi knihovny. Chcete-li tento problém vyřešit, zadejte **/Yl** (nebo odebrat **/Yl-** možnost) při použití **/Yc** k vytvoření souboru předkompilované hlavičky. Tím se zajistí, že se soubor objektu z knihovny, který obsahuje informace o ladění propojí ve vašem buildu.

Další informace o předkompilovaných hlaviček naleznete v tématu:

- [/Y (předkompilované hlavičky)](../../build/reference/y-precompiled-headers.md)

- [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Přidat **/Yl**_název_ – možnost kompilátoru v **další možnosti** pole. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
