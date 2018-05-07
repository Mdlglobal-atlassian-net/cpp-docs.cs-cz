---
title: Seznámení s kroky vlastního sestavení a událostí sestavení | Microsoft Docs
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
ms.openlocfilehash: a50c0cf224104f720a73a4830405e7114cda74ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="understanding-custom-build-steps-and-build-events"></a>Seznámení s kroky vlastního sestavení a s událostmi sestavení
Z ve vývojovém prostředí Visual C++, existují tři základní způsoby, jak přizpůsobit procesu sestavení:  
  
 **Vlastní kroky sestavení**  
 Vlastní krok sestavení je pravidlo sestavení spojené s projektem. Vlastní krok sestavení můžete zadat příkazový řádek provést žádné další vstupní nebo výstupní soubory a zobrazit zprávu. Další informace najdete v tématu [postupy: Přidání vlastního kroku sestavení do projektů MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md).  
  
 **Vlastní sestavovací nástroje**  
 Vlastní sestavovací nástroje je pravidlo sestavení přidružený jeden nebo více souborů. Vlastní krok sestavení může předat vstupní soubory nástroji vlastní sestavení, jehož výsledkem je jeden nebo více výstupních souborů. Například soubory nápovědy v aplikaci MFC jsou vytvořeny pomocí vlastní sestavovací nástroje. Další informace najdete v tématu [postupy: Přidání vlastního nástroje sestavení do projektů MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md) a [zadání nástroje sestavení vlastní](../ide/specifying-custom-build-tools.md).  
  
 **Události sestavení**  
 Události sestavení umožňují přizpůsobit sestavení projektu. Existují tři události sestavení: *před sestavením*, *před propojením*, a *po sestavení*. Události sestavení umožňuje určit akci na konkrétní čas v procesu sestavení. Můžete například využít událost sestavení pro registraci soubor s **regsvr32.exe** po dokončení sestavení projektu. Další informace najdete v tématu [určení událostí sestavení](../ide/specifying-build-events.md).  
  
 [Řešení potíží s přizpůsobením sestavení](../ide/troubleshooting-build-customizations.md) vám může pomoct zajistit, aby kroky vlastního sestavení a události sestavení fungovaly podle očekávání.  
  
 Formát výstupu vlastního kroku sestavení nebo události sestavení můžete také rozšířit použitelnost nástroj. Další informace najdete v tématu [Formátovaní výstupu vlastního kroku sestavení nebo události sestavení](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md).  
  
 Události sestavení a vlastní sestavení kroky spustit v následujícím pořadí spolu s jinými kroky sestavení:  
  
1.  Události před sestavením  
  
2.  Vlastní nástroje na jednotlivé soubory sestavení  
  
3.  MIDL  
  
4.  Kompilátor prostředků  
  
5.  Kompilátor C/C++  
  
6.  událost před propojením  
  
7.  Linkeru nebo Librarian (případně)  
  
8.  Nástroj manifest  
  
9. BSCMake  
  
10. Vlastní krok sestavení v projektu  
  
11. Události po sestavení  
  
 `custom build step on the project` a `post-build event` spuštěny postupně po jiných sestavení zpracovává dokončit.  
  
## <a name="see-also"></a>Viz také  
 [Sestavení projektů C++ v sadě Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)   
 [Běžné makra pro příkazy a vlastnosti sestavení](../ide/common-macros-for-build-commands-and-properties.md)   
 [Dialogové okno nástroje sestavení pořadí](http://msdn.microsoft.com/en-us/6204c5b1-7ce9-4948-9ff6-0268642ee14c)