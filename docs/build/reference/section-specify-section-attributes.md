---
title: / SECTION (určit atributy oddílu) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /section
dev_langs:
- C++
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d9b0a724f0e9156c81db20bf283e4418dd2f22d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379520"
---
# <a name="section-specify-section-attributes"></a>/SECTION (Určit atributy oddílu)

> **/ SECTION:**_název_, [[**!**] {**DEKPRSW**}] [**, ALIGN =**_číslo_]

## <a name="remarks"></a>Poznámky

**/SECTION** možnost změní atributy oddílu, přepsání atributy nastavená, pokud bylo kompilováno souboru .obj pro oddíl.

A *části* v přenosné spustitelný soubor (PE) je soubor s názvem souvislý blok paměti, která obsahuje kód nebo data. Některé části obsahují kód nebo data, která váš program deklarovaný a používá přímo, zatímco ostatní datové části jsou pro vás vytvořené linkeru a Správce knihovny (lib.exe) a obsahují informace, které jsou zásadní pro operační systém. Další informace najdete v tématu [PE formátu](https://msdn.microsoft.com/library/windows/desktop/ms680547).

Zadejte dvojtečkou (:) a oddíl *název*. *Název* je malá a velká písmena.

Nepoužívejte následující názvy, jako jsou v konfliktu se standardní názvy. Například .sdata se používá na RISC platformách:

- .arch

- .BSS

- .data –

- .edata

- .idata

- .pdata

- .rdata

- .reloc

- .rsrc

- .sbss

- .sdata

- .srdata

- .text

- .xdata

Zadejte jeden nebo více atributů pro oddíl. Atribut znaky, uvedené níže, se nerozlišují malá a velká písmena. Je nutné zadat všechny atributy, které chcete oddílu, který má být; znak není uveden atribut způsobí, že daný atribut bit vypnout. Pokud nezadáte R, W nebo E, existující pro čtení, zápisu nebo spustitelný soubor stavu zůstává beze změny.

Chcete-li negate atribut, uveďte před jeho znak s vykřičníkem (!). V této tabulce jsou uvedeny významy atribut znaků:

|Znak|Atribut|Význam|
|---------------|---------------|-------------|
|E|Spuštění|V části je spustitelný soubor|
|R|Číst|Umožňuje operace čtení dat|
|W|Write|Umožňuje operací zápisu na data|
|S|Shared|Sdílené složky v části mezi všechny procesy, které načíst obrázek|
|D|Discardable|Označí části jako discardable|
|K|Lze uložit do mezipaměti|Označí části jako není lze uložit do mezipaměti|
|P|Stránkovatelné|Označí části jako není stránkovatelné|

Tisíc a P se neobvyklé, že část příznaky, které odpovídají na ně se používají v tom smyslu, záporné. Pokud zadáte jeden z nich na části text s použitím **/SECTION:.text, K** možnost, není žádný rozdíl v části Příznaky při spuštění [DUMPBIN](../../build/reference/dumpbin-options.md) s [/HEADERS](../../build/reference/headers.md)možnost; v části se již implicitně ukládá do mezipaměti. Odebrání výchozího, zadejte **/SECTION:.text,! K** místo. DUMPBIN zjistí vlastnosti oddílu, včetně "Není mezipaměti."

Oddíl v souboru PE, který nemá E, R nebo W nastavit je pravděpodobně neplatná.

**ALIGN =**_číslo_ argument umožňuje určit hodnotu zarovnání pro konkrétní oddíl. _Číslo_ argument je v bajtech a musí být násobek dvou. V tématu [/ALIGN](../../build/reference/align-section-alignment.md) Další informace.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte možnost v **další možnosti** pole. Zvolte **OK** nebo **použít** na použití změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)  
[Možnosti linkeru](../../build/reference/linker-options.md)  
