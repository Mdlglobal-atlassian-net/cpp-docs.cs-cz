---
title: Určení událostí sestavení
ms.date: 12/28/2017
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
helpviewer_keywords:
- Pre-Link event
- build events [C++], specifying
- custom build steps [C++], build events
- builds [C++], events
- events [C++], build
- builds [C++], customizing C++
- build events [C++]
- post-build events
ms.assetid: 788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc
ms.openlocfilehash: c8097e013f934c45b8e3860b8377bdb2bdb9d9a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315232"
---
# <a name="specifying-build-events"></a>Určení událostí sestavení

Použití událostí sestavení zadat příkazy, na kterých běží před začátkem sestavení před proces propojení nebo po dokončení sestavení.

Události sestavení jsou spouštěny pouze v případě, že se sestavení úspěšně dosáhne těchto bodů v procesu sestavení. Pokud dojde k chybě v sestavení, *po sestavení* události nedojde, pokud k této chybě dojde před propojovací fázi ani *před propojením* ani *po sestavení* událostí Vyvolá se v. Kromě toho, pokud chcete propojit, není třeba žádné soubory *před propojením* události nedochází. *Před propojením* událostí není k dispozici v projektech, které neobsahují krok propojování.

Pokud má být sestaven. není třeba žádné soubory, dojde k událostem žádná sestavení.

Obecné informace o události sestavení, naleznete v tématu [kroky sestavení vlastní principy a události sestavení](understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-build-event"></a>K určení událostí sestavení

1. V **Průzkumníka řešení**, vyberte projekt, pro které chcete k určení událostí sestavení.

1. Otevřete v projektu **stránky vlastností** dialogové okno. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](working-with-project-properties.md).

1. V **události sestavení** složky, vyberte stránku vlastností události sestavení.

1. Zadejte vlastnosti přidružené k události sestavení:

   - V **příkazového řádku**, jako kdyby byly jeho zadáním na příkazovém řádku zadejte příkaz. Zadejte platný příkaz nebo dávkový soubor a všechny povinné vstupní nebo výstupní soubory. Zadejte **volání** dávkového příkazu před název dávkového souboru zaručí, že jsou provedeny všechny následné příkazy.

      Více vstupních a výstupních souborů lze symbolicky s makry MSBuild. Informace o tom, jak zadat umístění souborů nebo názvy sad souborů najdete v tématu [sestavení běžná makra pro příkazy a vlastnosti](reference/common-macros-for-build-commands-and-properties.md).

      Protože znak '%' je vyhrazený nástroj MSBuild, pokud zadáte proměnnou prostředí nahraďte každé **%** řídicí znak s **% 25** šestnáctková řídicí sekvence. Nahraďte třeba **% WINDIR %** s **25WINDIR % 25**. Nástroj MSBuild nahradí každou **% 25** pořadí se **%** dříve, než přistupuje k proměnné prostředí.

   - V **popis**, zadejte popis pro tuto událost. Popis zobrazeny **výstup** okno, když dojde k této události.

   - V **vyloučeno ze sestavení**, zadejte **Ano** Pokud nechcete, aby událost pro spuštění.

## <a name="see-also"></a>Viz také:

[Seznámení s kroky vlastního sestavení a s událostmi sestavení](understanding-custom-build-steps-and-build-events.md)<br>
[Běžná makra pro příkazy a vlastnosti sestavení](reference/common-macros-for-build-commands-and-properties.md)<br>
[Řešení potíží s přizpůsobením sestavení](troubleshooting-build-customizations.md)
