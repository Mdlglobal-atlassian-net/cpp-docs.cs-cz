---
title: Soubory projektu a řešení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.files.projectandsolution
dev_langs:
- C++
helpviewer_keywords:
- project files [C++]
- file types [C++], makefiles
- .sdf, browsing database file
- Makefile projects
- browsing database file, .sdf
- file types [C++], project files
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08cf1386ef177823c37bc285392309ec47f3c464
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33340694"
---
# <a name="project-and-solution-files"></a>Soubory projektu a řešení
Následující soubory se vytvoří při vytvoření projektu v sadě Visual Studio. Používají se ke správě souborů projektu v řešení.  
  
|Název souboru|Umístění adresáře|Umístění v Průzkumníku řešení|Popis|  
|--------------|------------------------|--------------------------------|-----------------|  
|*Solname*.sln|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Řešení* souboru. Slouží k uspořádání všechny elementy projektu nebo více projektů do jednoho řešení.|  
|*Projname*.suo|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Možnosti řešení* souboru. Ukládá vaše úpravy řešení tak, aby při každém otevření projektu nebo soubor v řešení, měl vzhled a chování, které chcete.|  
|*Projname*VCXPROJ|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Projektu* souboru. Ukládá informace specifické pro každý projekt. (V dřívějších verzích, byl tento soubor s názvem *Projname*.vcproj nebo *Projname*.dsp.) Příklad souboru projektu Visual C++, naleznete v části [soubory projektu](../ide/project-files.md).|  
|*Projname*.vcxitems|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Sdílené položky projektu* souboru. Tento projekt není sestaven.  Místo toho projekt lze odkazovat pomocí jiného projektu C++ a jeho soubory se stane součástí procesu sestavení odkazující projektu. Tímto lze sdílet společný kód s projekty C++ napříč platformami.|
|*Projname*SDF|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Procházení databáze* souboru. Podporuje funkce procházení a navigace například **definice Goto**, **najít všechny odkazy**, a **zobrazení tříd**. Je generován analýza soubory hlaviček.|  
|*Projname.* vcxproj.filters|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Filtry* souboru. Určuje, kde má být umístění souboru, který je přidán do řešení. Například soubor .h uveden **soubory hlaviček** uzlu.|  
|*Projname.* vcxproj.user|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Migrace uživatele* souboru. Po migraci projektu ze sady Visual Studio 2008, tento soubor obsahuje informace, které byl převeden ze všech souborů.|  
|*Projname*.idl|*Projname*|Zdroj|(Specifické pro projekt) Obsahuje popis jazyka IDL (Interface) zdrojový kód pro knihovnu typů ovládacích prvků. Tento soubor se používá ve Visual C++ pro generování knihovny typů. Vygenerovaná knihovna zpřístupní rozhraní ovládacího prvku pro ostatní klienty automatizace. Další informace najdete v tématu [soubor definice IDL (Interface)](http://msdn.microsoft.com/library/windows/desktop/aa378712) ve Windows SDK.|  
|Readme.txt|*Projname*|Projekt|*Soubor Readme* souboru. Je generována pomocí Průvodce aplikací a popisuje soubory v projektu.|  
  
## <a name="see-also"></a>Viz také  
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)