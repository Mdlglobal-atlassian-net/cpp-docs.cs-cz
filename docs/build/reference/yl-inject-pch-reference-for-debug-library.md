---
title: -Yi (Vložit referenci PCH ladicí knihovny) | Microsoft Docs
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
ms.openlocfilehash: a73e79cd50343292ae63dfa831a7638d6444fc64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Vložit referenci PCH do ladicí knihovny)

**/Yl** možnost generuje jedinečné symbol v předkompilovaný hlavičkový soubor, a je ve všech objekt soubory, které používají předkompilovaných hlaviček vložit odkaz na tento symbol.

## <a name="syntax"></a>Syntaxe

>**/Yl**  
>**/Yl**_název_  
>**/Yl-**  

### <a name="arguments"></a>Arguments

*Jméno*  
Volitelné jméno používá jako součást jedinečný symbolu.

*\-*  
Explicitně zakáže pomlčkou (-) **/Yl** – možnost kompilátoru.

## <a name="remarks"></a>Poznámky

**/Yl** – možnost kompilátoru vytvoří definici jedinečný symbol v předkompilovaný hlavičkový soubor vytvořili pomocí [/Yc](../../build/reference/yc-create-precompiled-header-file.md) možnost. Odkazy na tento symbol jsou automaticky vložit v všechny soubory, které zahrnují předkompilovaných hlaviček pomocí [/Yu](../../build/reference/yu-use-precompiled-header-file.md) – možnost kompilátoru. **/Yl** ve výchozím nastavení je povolena možnost při **/Yc** se používá k vytvoření předkompilovaný hlavičkový soubor.

**/Yl**_název_ možnost se používá k vytvoření osobní symbol v předkompilovaný hlavičkový soubor. Kompilátor používá *název* argument jako část názvu dekorované symbol vytvoří, podobně jako \_ \_ @@ \_PchSym\_@00@... @ *název*, kde znak výpustky (...) představuje jedinečnou generované kompilátorem řetězec znaků. Pokud *název* je tento argument vynechán, kompilátor automaticky vygeneruje název symbolu. Za normálních okolností není potřeba znát název symbolu. Ale když projektu používá více než jeden soubor předkompilovaných hlaviček **/Yl**_název_ možnost může být užitečné k určení, který objekt soubory použití, která předkompilované hlavičky. Můžete použít *název* jako hledaný řetězec pro odkaz symbol najít v souboru výpisu.

**/Yl-** zakáže výchozí chování a nevystavuje identifikační symbol předkompilovaný hlavičkový soubor. Zkompilované soubory, které obsahují tento předkompilovaných hlaviček Nezískávat běžné symbol odkazu.

Když **/Yc** není zadán, všechny **/Yl** možnost nemá žádný vliv, ale pokud zadán, musí se shodovat žádné **/Yl** možnost předaná při **/Yc** je zadat.

Pokud používáte **/Yl-**, **/Yc** a [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) možnosti Vytvořit předkompilovaný hlavičkový soubor, informace o ladění je uložený v souboru objektu pro zdrojový soubor použitý k vytvoření Předkompilované hlavičky, nikoli soubor .pdb samostatné. Pokud se tento objekt soubor pak součást knihovny, [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) chyby nebo [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) upozornění se může objevit v sestavení, které používají tuto knihovnu a předkompilovaný hlavičkový soubor, pokud zdrojový soubor se používá k vytvoření předkompilovaný hlavičkový soubor nebyla definována žádné symboly. Linkeru mohou vyloučit soubor objektu z odkazu, který je společně s související informace pro ladění, když nic do souboru objektu se odkazuje v klientovi knihovny. Chcete-li tento problém vyřešit, zadejte **/Yl** (nebo odebrat **/Yl-** možnost) při použití **/Yc** vytvořit předkompilovaný hlavičkový soubor. Tím se zajistí, že soubor objektu z knihovny, který obsahuje informace o ladění získá propojené v buildu.

Další informace o předkompilovaných hlaviček najdete v tématu:

- [/Y (předkompilované hlavičky)](../../build/reference/y-precompiled-headers.md)

- [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Přidat **/Yl**_název_ – možnost kompilátoru v **další možnosti** pole. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
