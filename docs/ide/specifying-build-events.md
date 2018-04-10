---
title: Určení událostí sestavení | Microsoft Docs
ms.custom: ''
ms.date: 12/28/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-ide
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
dev_langs:
- C++
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
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 825eec000a2b08bd7a5a4d7769405df2f5570523
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="specifying-build-events"></a>Určení událostí sestavení

Události sestavení můžete použít k určení příkazy, které před začátkem sestavování před proces odkaz, nebo po dokončení sestavení.

Události sestavení jsou spuštěny pouze v případě, že sestavení úspěšně dosáhne těchto bodů v procesu sestavení. Pokud dojde k chybě v sestavení, *po sestavení* události nedojde; pokud dojde k chybě před fází propojení, ani *před propojením* ani *po sestavení* událostí nastane. Kromě toho, pokud žádné soubory musí být propojený, *před propojením* události nedojde. *Před propojením* událostí není k dispozici v projektech, které neobsahují krok propojení.

Pokud žádné soubory se musela být vytvořená, dojde k žádné události sestavení.

Obecné informace o událostech sestavení najdete v tématu [kroky sestavení vlastní pochopení a vytvoření události](../ide/understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-build-event"></a>K určení událostí sestavení

1. V **Průzkumníku**, vyberte projekt, pro který chcete určit událost sestavení.

1. Otevření projektu **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

1. V **události sestavení** složky, vyberte stránku vlastností události sestavení.

1. Zadejte vlastnosti související s událostí sestavení:

   - V **příkazového řádku**, jako kdyby byly ho zadat na příkazovém řádku zadejte příkaz. Zadejte platný příkaz nebo dávkového souboru a libovolný požadovaný vstupní nebo výstupní soubory. Zadejte **volání** dávky příkazu před název souboru batch zaručit, že jsou všechny následné příkazy provedeny.

      Více vstupních a výstupních souborů může být zadáno symbolicky s makry MSBuild. Informace o tom, jak zadat umístění souborů nebo názvy sad souborů najdete v tématu [běžné makra pro příkazy sestavení a vlastnosti](../ide/common-macros-for-build-commands-and-properties.md).

      Protože znak "%" je rezervován MSBuild, pokud zadáte proměnnou prostředí nahradit každý  **%**  znaku s **% 25** šestnáctková řídicí sekvence. Například nahradit **% WINDIR %** s **25WINDIR % 25**. MSBuild nahradí každý **% 25** pořadí se  **%**  znak před přistupuje k proměnné prostředí.

   - V **popis**, zadejte popis pro tuto událost. Popis vytištěn **výstup** okno, pokud dojde k této události.

   - V **vyloučeno ze sestavení**, zadejte **Ano** Pokud nechcete, aby událost pro spuštění.

## <a name="see-also"></a>Viz také

[Seznámení s kroky vlastního sestavení a s událostmi sestavení](../ide/understanding-custom-build-steps-and-build-events.md)  
[Běžná makra pro příkazy a vlastnosti sestavení](../ide/common-macros-for-build-commands-and-properties.md)  
[Řešení potíží s přizpůsobením sestavení](../ide/troubleshooting-build-customizations.md)  
