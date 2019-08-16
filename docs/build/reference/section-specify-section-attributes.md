---
title: /SECTION (Určit atributy oddílu)
ms.date: 12/29/2017
f1_keywords:
- /section
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.openlocfilehash: 0a52e9c9dcd53b01f17dc36825732b34771c75bb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492632"
---
# <a name="section-specify-section-attributes"></a>/SECTION (Určit atributy oddílu)

> **/Section:** _název_[[ **!** ] {**DEKPRSW**}] [ **, Align =** _Number_]

## <a name="remarks"></a>Poznámky

Možnost **/Section** změní atributy oddílu a přepíše přitom atributy nastavené při kompilaci souboru. obj pro oddíl.

*Oddíl* v přenositelném spustitelném souboru (PE) je pojmenovaný souvislý blok paměti, který obsahuje buď kód, nebo data. Některé oddíly obsahují kód nebo data, která program deklaruje a používá přímo, zatímco jiné oddíly dat jsou vytvořeny pro vás linkerem a správcem knihovny (lib. exe) a obsahují informace, které jsou pro operační systém zásadní. Další informace najdete v tématu [Formát PE](/windows/win32/Debug/pe-format).

Zadejte dvojtečku (:) a *název*oddílu. V *názvu* se rozlišují velká a malá písmena.

Nepoužívejte následující názvy, protože jsou v konfliktu se standardními názvy. Například. sdata se používá na platformách RISC:

- . arch

- . bss

- .data

- .edata

- .idata

- .pdata

- .rdata

- .reloc

- . rsrc

- . sbss

- .sdata

- .srdata

- .text

- .xdata

Zadejte jeden nebo více atributů pro oddíl. V níže uvedených znacích atributů se nerozlišují malá a velká písmena. Je nutné zadat všechny atributy, které má oddíl mít. znak vynechaného atributu způsobuje, že je bit atributu vypnutý. Pokud nezadáte R, W nebo E, stávající stav čtení, zápisu nebo spustitelného souboru zůstane beze změny.

Pro negaci atributu, před jeho znak vykřičníkem (!). Význam znaků atributů je zobrazen v této tabulce:

|Znak|Atribut|Význam|
|---------------|---------------|-------------|
|E|Spustit|Oddíl je spustitelný soubor|
|R|Číst|Povoluje operace čtení pro data|
|W|Write|Povoluje operace zápisu pro data|
|S|Shared|Sdílí oddíl mezi všemi procesy, které načítají obrázek.|
|D|Vypuštění|Označí oddíl jako zahozený.|
|K|Uložitelný|Označí oddíl jako neukládatelné do mezipaměti.|
|P|Stránkované|Označí oddíl jako nestránkový.|

K a P jsou neobvyklé v tom, že příznaky oddílu, které odpovídají, jsou používány v negativním smyslu. Pokud zadáte jednu z těchto možností v oddílu. text pomocí možnosti **/section:. text, k** , není v příznacích oddílu při spuštění [DUMPBIN](dumpbin-options.md) s možností [/Headers](headers.md) žádný rozdíl. oddíl byl již implicitně uložen do mezipaměti. Chcete-li odebrat výchozí hodnotu, zadejte **/section:. text,! K** místo toho. DUMPBIN odhalí charakteristiky oddílu, včetně "neuložený v mezipaměti".

Oddíl v souboru PE, který nemá sadu E, R nebo W, je pravděpodobně neplatný.

Argument **align =** _Number_ umožňuje zadat hodnotu zarovnání pro konkrétní oddíl. Argument _Number_ je v bajtech a musí být mocninou dvou. Další informace najdete v tématu [/align](align-section-alignment.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností**příkazový řádek** **linkeru** >  **vlastností** > konfigurace.

1. Zadejte možnost do pole **Další možnosti** . Kliknutím na **tlačítko OK** nebo **použít** provedete změnu.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
