---
title: Seznámení s kroky vlastního sestavení a událostí sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], events
- custom build steps [C++], customizing builds
- events [C++], build
- custom build steps [C++]
- build steps [C++]
- build events [C++], order of events and build steps
- build steps [C++], build events
- builds [C++], custom build steps
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16c1bdf088e0545292a672458c066364b5a47ff4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206292"
---
# <a name="understanding-custom-build-steps-and-build-events"></a>Seznámení s kroky vlastního sestavení a s událostmi sestavení
Z vývojového prostředí Visual C++ existují tři základní způsoby, jak přizpůsobit proces sestavení:  
  
 **Vlastní kroky sestavení**  
 Vlastní krok sestavení je pravidlo sestavení přidružené k projektu. Vlastní krok sestavení můžete zadat příkazový řádek ke spuštění jakékoli další vstupní nebo výstupní soubory a napište zprávu zobrazit. Další informace najdete v tématu [postupy: Přidání vlastní krok sestavení do projektů MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md).  
  
 **Vlastní sestavovací nástroje**  
 Pro vlastní nástroj sestavení je pravidlo sestavení přidružené k jedné nebo více souborů. Vlastní krok sestavení můžete předat vstupních souborů pro vlastní nástroj sestavení, což vede k jedné nebo více výstupních souborů. Například soubory nápovědy v aplikacích MFC jsou vybaveny pro vlastní nástroj sestavení. Další informace najdete v tématu [postupy: Přidání Build Tools vlastní do projektů MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md) a [zadání Custom Build Tools](../ide/specifying-custom-build-tools.md).  
  
 **Události sestavení**  
 Události sestavení umožňují přizpůsobit sestavení projektu. Existují tři události sestavení: *před sestavením*, *před propojením*, a *po sestavení*. Události sestavení umožňuje určit akci na určitou dobu v procesu sestavení. Můžete například použít událost sestavení zaregistrovat soubor s **regsvr32.exe** po dokončení sestavení projektu. Další informace najdete v tématu [určení událostí sestavení](../ide/specifying-build-events.md).  
  
 [Řešení potíží s přizpůsobením sestavení](../ide/troubleshooting-build-customizations.md) vám může pomoct zajistit, aby vaše vlastní kroky sestavení a události sestavení fungovaly podle očekávání.  
  
 Formát výstupu vlastního kroku sestavení nebo události sestavení můžete také zlepšují použitelnost nástroje. Další informace najdete v tématu [Formátovaní výstupu vlastního kroku sestavení nebo události sestavení](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md).  
  
 Události sestavení a vlastní kroky v uvedeném pořadí společně s další kroky sestavení spustit sestavení:  
  
1.  Událost před sestavením  
  
2.  Nástroj Custom build na jednotlivé soubory  
  
3.  MIDL  
  
4.  Kompilátor prostředků  
  
5.  Kompilátor C/C++  
  
6.  událost před propojením  
  
7.  Propojovací program nebo Librarian (podle potřeby)  
  
8.  Nástroj manifest  
  
9. Nástroje BSCMake  
  
10. Vlastní krok sestavení na projektu  
  
11. Událost po sestavení  
  
 `custom build step on the project` a `post-build event` spustit postupně po všech ostatních vytvoření zpracovává dokončit.  
  
## <a name="see-also"></a>Viz také  
 [Sestavení projektů C++ v sadě Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)   
 [Běžná makra pro příkazy a vlastnosti sestavení](../ide/common-macros-for-build-commands-and-properties.md)   
 [Dialogové okno pořadí sestavení nástroje](https://msdn.microsoft.com/6204c5b1-7ce9-4948-9ff6-0268642ee14c)