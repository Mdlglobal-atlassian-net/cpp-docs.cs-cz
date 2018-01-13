---
title: "-Yi (Vložit referenci PCH ladicí knihovny) | Microsoft Docs"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /yl
dev_langs: C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6e777977f6d869d2bbc28d980f6445851e54396b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Vložit referenci PCH do ladicí knihovny)

**/Yl** možnost vytvoří společná značka pro předkompilovaný hlavičkový soubor a vloží odkazy na tento symbol v všechny soubory, které používají předkompilovaných hlaviček. To zpřístupní informace o dokončení typu předkompilovaných hlaviček symbolů pro všechny soubory, které používají předkompilovaných hlaviček v ladicím programu. Tato možnost je povolená ve výchozím nastavení. Použití této možnosti můžete zabránit chybami linkeru z důvodu chybějící informace o ladění do propojené knihovny, které použití předkompilovaných hlaviček.

## <a name="syntax"></a>Syntaxe

>**/Yl**  
>**/Yl**_název_  
>**/Yl-**  

### <a name="arguments"></a>Arguments

*Jméno*  
Volitelné jméno používá k definování symbol, který má být objekt uložené a odkazovaná v soubory, které definují nebo použití předkompilovaných hlaviček.

*\-*  
Explicitně zakáže pomlčkou (-) **/Yl** – možnost kompilátoru.

## <a name="remarks"></a>Poznámky

**/Yl** možnost umožňuje získat úplné informace o typech v předkompilovaných hlaviček v každý soubor, který zahrnuje předkompilovaných hlaviček ladicího programu. Tato možnost vytvoří název interní symbol, vloží do souboru objektu použitý k vytvoření předkompilovaných hlaviček podle definice symbolu [/Yc](../../build/reference/yc-create-precompiled-header-file.md) možnost a vloží odkaz na symbol v všechny soubory, které zahrnují předkompilovaných záhlaví s použitím [/Yu](../../build/reference/yu-use-precompiled-header-file.md) – možnost kompilátoru. Protože všechny zdrojové soubory, které používají předkompilovaných hlaviček odkazují pojmenované symbol, linkeru vždy propojí soubor objekt, který definuje symbol a přidružené předkompilovaných hlaviček ladicí informace. Tato možnost je povolená ve výchozím nastavení.

**/Yl**_název_ možnost se používá k vytvoření explicitně identifikační symbol pro předkompilovaný hlavičkový soubor. Kompilátor používá *název* argument pro vytvoření symbolu podobná \_ \_ @@ \_PchSym\_@00@... @*název* , kde řetězec znaků představuje linkeru generované třemi tečkami (...). Pokud je argument vynechán, kompilátor automaticky vygeneruje název symbolu.

**/Yl-** zakáže výchozí chování a nevystavuje identifikační symbol odkazu v objektu soubory, které zahrnují předkompilovaných hlaviček. Tato možnost může být vyžadováno pro soubory kompilovat bez přítomen předkompilovaný hlavičkový soubor.

Pokud používáte **/Yl-**, **/Yc** a [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) možnosti pro sestavení knihovny, kompilátor vytvoří soubor předkompilovaných hlaviček, který obsahuje informace o ladění uložených v objekt souboru nikoli soubor .pdb. [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) chyby nebo [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) upozornění se může objevit v sestavení, které knihovnu používají a předkompilovaných hlaviček, pokud zdrojový soubor se používá k vytvoření předkompilovaných hlaviček nedefinuje žádné symboly. Při nic do souboru objektu se odkazuje v klientovi knihovny, může linkeru vyloučit tento soubor knihovny objekt z odkazu, který je společně s ladicí informace o přidružených předkompilovaných hlaviček. Chcete-li problém vyřešit, zadejte **/Yl** při použití **/Yc** vytvořit předkompilovaný hlavičkový soubor a **/Yu** ji použít. Tím se zajistí, že souboru objektu, který obsahuje informace o ladění součástí buildu.

Další informace o předkompilovaných hlaviček najdete v tématu:

- [/Y (předkompilované hlavičky)](../../build/reference/y-precompiled-headers.md)

- [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **příkazového řádku** stránka vlastností v **C/C++** složky.

1. Přidat **/Yl**_název_ – možnost kompilátoru v **další možnosti** pole. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
