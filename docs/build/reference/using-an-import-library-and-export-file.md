---
title: Použití knihovny importu a souboru exportu
ms.date: 11/04/2016
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
ms.openlocfilehash: 030b792d4bbebecef9d9303238657a564a142ecf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810949"
---
# <a name="using-an-import-library-and-export-file"></a>Použití knihovny importu a souboru exportu

Když program na jiném programu, který také importy z exportuje (spustitelný soubor nebo knihovny DLL), nebo pokud více než dva programy exportovat a importovat od sebe navzájem, příkazy propojit tyto programy musí zohlednit kruhové exporty.

V případě, že bez kruhové exporty při propojení programu, který používá exportuje z jiné aplikace, musíte zadat knihovnu importu, exportu programu. Knihovnu importu, exportu programu je vytvořen při propojování export programu. Proto je třeba propojit export programu před importu programu. Například pokud TWO.dll importy z ONE.dll, je nutné nejprve propojit ONE.dll a získat knihovnu importu ONE.lib. Pak nastavíte ONE.lib při propojování TWO.dll. Když linker vytvoří TWO.dll, také vytvoří knihovnu importu TWO.lib. Používejte TWO.lib propojování programů, které importují z TWO.dll.

Ale v situaci, cyklické exportu, není možné propojit všechny vzájemně závislých aplikací pomocí knihovny importu z jiných aplikací. V příkladu jsme probírali výše, je-li TWO.dll také exportuje do ONE.dll, knihovnu importu pro TWO.dll nebude existovat, ale když ONE.dll propojen. Pokud kruhové exporty existuje, je nutné použít LIB vytvořit knihovnu importu a exportu souboru pro jeden z programů.

Pokud chcete začít, zvolte jednu z aplikací, ve kterém se spustí LIB. V příkazu LIB seznam všech objektů a knihovny pro program a určit /DEF. Pokud program používá .def souboru nebo specifikace/Export je přebytečný, zadejte je také.

Po vytvoření knihovnu importu (.lib) a souboru exportu (.exp) pro program, použít importovanou knihovnou při propojování na program nebo programy. Příkaz LINK vytvoří knihovnu importu pro každý export program, který sestaví. Například pokud spustíte LIB na objekty a exportuje pro ONE.dll, vytvoříte ONE.lib a ONE.exp. Teď můžete použít ONE.lib při propojování TWO.dll; Tento krok také vytvoří knihovnu importu TWO.lib.

A konečně propojte program, který jste začali. V příkazu LINK zadejte objekty a knihovny pro program souboru .exp LIB vytvořený pro program a knihovna importu nebo knihovny pro exporty používá tento program. Chcete-li pokračovat v příkladu, obsahuje odkaz pro ONE.dll ONE.exp a TWO.lib, jakož i objekty a knihovny, které patří do ONE.dll. V příkazu LINK; neurčí soubor .def nebo specifikaci/Export je přebytečný ty nejsou potřeba, protože definice exportu jsou obsaženy v souboru .exp. Při propojování pomocí souboru .exp odkaz nelze vytvořit knihovnu importu, protože předpokládá, že jedna byl vytvořen při vytvoření souboru .exp.

## <a name="see-also"></a>Viz také:

[Práce s knihovnami importu a soubory exportu](working-with-import-libraries-and-export-files.md)
