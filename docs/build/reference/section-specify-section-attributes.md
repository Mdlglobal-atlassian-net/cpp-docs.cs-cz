---
title: / SECTION (určení atributů oddílu) | Dokumentace Microsoftu
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
ms.openlocfilehash: bf762718e507309e47d36b06baacf54c6cb01e3e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713722"
---
# <a name="section-specify-section-attributes"></a>/SECTION (Určit atributy oddílu)

> **/ SECTION:**_název_, [[**!**] {**DEKPRSW**}] [**, ZAROVNAT =**_číslo_]

## <a name="remarks"></a>Poznámky

**/SECTION** možnost změní atributy oddílu a přepíše přitom atributy nastavené při kompilaci souboru obj části.

A *části* v přenosného spustitelného (PE) soubor je pojmenovaný blok souvislé paměti, která obsahuje kód nebo data. Některé části obsahují kód nebo data, která váš program deklarovaný a používá přímo, zatímco ostatní datové části se za vás vytvoří služba linkeru a knihovny správce (lib.exe) a obsahují informace, které jsou důležité pro operační systém. Další informace najdete v tématu [formátu PE](/windows/desktop/Debug/pe-format).

Zadejte dvojtečku (:) a oddíl *název*. *Název* je velká a malá písmena.

Nepoužívejte následující názvy, protože jsou v konfliktu s názvy standardní. .Sdata. je třeba použít na RISC platformách:

- .arch

- .BSS

- .data

- .edata

- .idata

- .pdata

- .rdata

- .reloc

- .rsrc

- .sbss

- .sdata.

- .srdata

- .text

- .xdata

Zadejte jeden nebo více atributů pro oddíl. Atribut znaků, tady, se nerozlišují malá a velká písmena. Je nutné zadat všechny atributy, které chcete, aby oddílu, který má k dispozici. znak není uveden atribut způsobí, že tento atribut bit jej nejprve vypnout. Pokud nezadáte R, W nebo E, existující pro čtení, zápis, nebo spustitelný soubor stavu zůstává beze změny.

Chcete-li negate – atribut, před jeho znak s vykřičníkem (!). Význam atribut znaky jsou uvedené v této tabulce:

|Znak|Atribut|Význam|
|---------------|---------------|-------------|
|E|Spuštění|V části je spustitelný|
|R|Číst|Umožňuje čtení operací s daty|
|W|Write|Umožňuje operací zápisu na data|
|S|Shared|Sdílené složky v části mezi všechny procesy, které načtení obrázku|
|D|Discardable|Označí jako discardable části|
|K|Možné ukládat do mezipaměti|Označí oddílu jako není možné ukládat do mezipaměti|
|P|Stránkované|Označí oddíl jako nejsou stránkované|

K a P neobvyklá v tom, že část příznaky, které odpovídají na ně se používají v tom smyslu, záporná. Pokud zadáte jednu položku na části .text pomocí **/SECTION:.text, K** možnost, není žádný rozdíl v příznacích části při spuštění [DUMPBIN](../../build/reference/dumpbin-options.md) s [/HEADERS](../../build/reference/headers.md)možnost; v části již implicitně ukládá do mezipaměti. Chcete-li odebrat výchozí nastavení, zadejte **/SECTION:.text,! K** místo. DUMPBIN – zobrazí vlastnosti oddílu, včetně "Není v mezipaměti."

Oddíl v souboru PE, která nemá E, R nebo W, nastavte je pravděpodobně neplatná.

**ZAROVNAT =**_číslo_ argument umožňuje zadat hodnotu zarovnání pro konkrétní části. _Číslo_ argument je vyjádřen v bajtech a musí být mocninou čísla 2. Zobrazit [/ALIGN](../../build/reference/align-section-alignment.md) Další informace.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Zvolte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte parametr do **další možnosti** pole. Zvolte **OK** nebo **použít** na použití změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
