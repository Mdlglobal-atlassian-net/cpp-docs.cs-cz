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

Události sestavení lze použít k určení příkazů, které jsou spuštěny před zahájením sestavení, před procesem propojení nebo po dokončení sestavení.

Události sestavení jsou spouštěny pouze v případě, že sestavení úspěšně dosáhne těchto bodů v procesu sestavení. Pokud dojde k chybě v sestavení, událost *po sestavení* neproběhne; Pokud dojde k chybě před fází propojení, nedojde k události před *propojením* ani *po sestavení* . Kromě toho, pokud není potřeba propojit žádné soubory, neproběhne událost *před propojením* . Událost *před propojením* není k dispozici také v projektech, které neobsahují krok propojení.

Pokud není nutné sestavit žádné soubory, nedošlo k žádné události sestavení.

Obecné informace o událostech sestavení naleznete v tématu [porozumění vlastním krokům sestavení a událostem sestavení](understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-build-event"></a>Určení události sestavení

1. V **Průzkumník řešení**vyberte projekt, pro který chcete zadat událost sestavení.

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](working-with-project-properties.md).

1. Ve složce **události sestavení** vyberte stránku vlastností události sestavení.

1. Zadejte vlastnosti přidružené k události sestavení:

   - V **příkazovém řádku**zadejte příkaz, jako kdybyste ho zadali v příkazovém řádku. Zadejte platný příkaz nebo dávkový soubor a všechny požadované vstupní nebo výstupní soubory. Před názvem dávkového souboru zajistěte, aby se zajistilo, že se budou spouštět všechny následné příkazy, zadáním příkazu Batch pro **volání** .

      Více vstupních a výstupních souborů lze zadat symbolické pomocí maker nástroje MSBuild. Informace o tom, jak určit umístění souborů nebo názvy sad souborů, naleznete v tématu [společná makra pro příkazy a vlastnosti sestavení](reference/common-macros-for-build-commands-and-properties.md).

      Vzhledem k tomu, že je znak% rezervován nástrojem MSBuild, pokud zadáte proměnnou prostředí, nahraďte každý **%** řídicí znak znakem **%25** v šestnáctkové řídicí sekvenci. Například nahraďte **% windir%** za **% 25WINDIR %25**. Nástroj **%** MSBuild nahradí každé **%25** sekvence znakem před tím, než přistupuje k proměnné prostředí.

   - Do **Popis**zadejte popis této události. Popis je vytištěn do okna **výstup** , když dojde k této události.

   - V seznamu **vyloučeno ze sestavení**zadejte **Ano** , pokud nechcete, aby se událost spustila.

## <a name="see-also"></a>Viz také

[Seznámení s kroky vlastního sestavení a s událostmi sestavení](understanding-custom-build-steps-and-build-events.md)<br>
[Společná makra pro příkazy a vlastnosti sestavení](reference/common-macros-for-build-commands-and-properties.md)<br>
[Řešení potíží s přizpůsobením sestavení](troubleshooting-build-customizations.md)
