---
title: Použití knihovny importu a souboru exportu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 946ef702d17762e6771bad206d0bfa682a61055e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378594"
---
# <a name="using-an-import-library-and-export-file"></a>Použití knihovny importu a souboru exportu
Když program na jiném programu, který také importovat z exportuje (spustitelného souboru nebo knihovny DLL), nebo pokud více než dva programy exportovat do a importovat od sebe navzájem, příkazy propojení tyto programy musí zohlednit kruhové exporty.  
  
 V případě, že bez kruhové exporty při propojování program, který používá exportuje z jiné aplikace, musíte zadat knihovny importu pro export program. Import knihovny pro export program se vytvoří při propojení tohoto programu exportu. Proto musí propojit export program před import programem. Například pokud TWO.dll importuje z ONE.dll, musíte nejdřív propojit ONE.dll a získání knihovny importu ONE.lib. Pak zadáte ONE.lib při propojování TWO.dll. Když linkeru vytváří TWO.dll, vytvoří také knihovny importu TWO.lib. Při propojování programů, které importovat z TWO.dll, použijte TWO.lib.  
  
 Ale v situaci, cyklické exportu, není možné propojit všechny konkrétní programy použití knihoven importovat z jiných aplikací. V příkladu už jsme probírali výše, pokud TWO.dll také exportuje do ONE.dll, nebude existovat knihovny importu pro TWO.dll ještě při ONE.dll souvisí. Pokud existují kruhové exporty, musíte použít LIB vytvořit knihovnu importu a exportu souboru pro jednu z aplikací.  
  
 Pokud chcete začít, vyberte jednu z programů, na který se má spustit LIB. V příkazu LIB seznam všech objektů a knihovny pro program a zadejte /DEF. Pokud program používá soubor .def nebo/export specifikace, zadejte tyto také.  
  
 Po vytvoření knihovny importu (LIB) a souboru exportu (.exp) pro program, pomocí knihovny importu při propojování další program nebo programy. PROPOJENÍ vytvoří knihovnu importu pro každý export program, který sestavuje. Například pokud spustíte LIB na objekty a exportuje pro ONE.dll, vytvoříte ONE.lib a ONE.exp. Teď můžete použít ONE.lib při propojování TWO.dll; Tento krok vytvoří také knihovny importu TWO.lib.  
  
 Nakonec propojte program, který jste začali s. V příkazu odkaz zadejte objekty a knihovny pro export, který program používá nebo knihovny pro program, .exp soubor, který LIB vytvořit pro program a knihovny importu. Chcete-li pokračovat v příkladu, obsahuje příkaz odkaz pro ONE.dll ONE.exp a TWO.lib, a také objekty a knihovny, které patří do ONE.dll. Nezadávejte souboru .def nebo/export specifikace v příkazu odkaz; Tyto nejsou potřeba, protože definice exportu jsou obsaženy v souboru .exp. Při propojení pomocí souboru .exp odkaz nevytvoří knihovnu importu, protože předpokládá, že jeden byla vytvořena, když .exp soubor byl vytvořen.  
  
## <a name="see-also"></a>Viz také  
 [Práce s knihovnami importu a soubory exportu](../../build/reference/working-with-import-libraries-and-export-files.md)