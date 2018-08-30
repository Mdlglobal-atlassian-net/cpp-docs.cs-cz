---
title: Soubory projektu a řešení | Dokumentace Microsoftu
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
ms.openlocfilehash: 282fd41602b70f743926b0fe5322346e9cdfd3fc
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203292"
---
# <a name="project-and-solution-files"></a>Soubory projektu a řešení
Následující soubory jsou vytvořeny při vytvoření projektu v sadě Visual Studio. Používají se ke správě souborů projektu v řešení.  
  
|Název souboru|Umístění adresáře|Umístění v Průzkumníku řešení|Popis|  
|--------------|------------------------|--------------------------------|-----------------|  
|*Solname*.sln|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Řešení* souboru. Uspořádá všechny prvky projektu nebo více projektů do jednoho řešení.|  
|*Název_projektu*.suo|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Možnosti řešení* souboru. Vlastní nastavení pro toto řešení ukládá tak, aby při každém otevření projektu nebo souboru v řešení, měl vzhled a chování, které chcete.|  
|*Název_projektu*.vcxproj|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Projektu* souboru. Ukládají se informace specifické pro každý projekt. (V dřívějších verzích se tento soubor s názvem *název_projektu*.vcproj nebo *název_projektu*.dsp.) Příklad souboru projektu Visual C++, naleznete v tématu [soubory projektu](../ide/project-files.md).|  
|*Název_projektu*.vcxitems|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Sdílené položky projektu* souboru. Tento projekt není sestaven.  Místo toho jiný projekt C++ mohou odkazovat projekt a jeho soubory se stanou součástí procesu sestavení odkazující projekt. To je možné sdílet společný kód s multiplatformní projekty C++.|
|*Název_projektu*SDF|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Databáze procházení* souboru. Podporuje vyhledávání a navigace funkce, jako **Goto definice**, **najít všechny odkazy**, a **zobrazení tříd**. Je generována pomocí analýzy soubory hlaviček.|  
|*Název_projektu.* vcxproj.filters|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Filtry* souboru. Určuje umístění souboru, který je přidán do řešení. Například soubor hlaviček je umístěn **hlavičkové soubory** uzlu.|  
|*Název_projektu.* vcxproj.user|*Projname*|Nezobrazuje se v Průzkumníku řešení|*Uživatele migrace* souboru. Po migraci oznámení projekt ze sady Visual Studio 2008, tento soubor obsahuje informace, které se převedl ze všech souborů.|  
|*Název_projektu*IDL|*Projname*|Zdroj|(Specifické pro projekt) Obsahuje popis jazyka IDL (Interface) zdrojový kód pro knihovnu typů ovládacího prvku. Tento soubor se používá ve Visual C++ generovat knihovnu typů. Vygenerovaný knihovna poskytuje rozhraní ovládacího prvku jiným klientům automatizace. Další informace najdete v tématu [soubor Interface Definition (IDL)](https://msdn.microsoft.com/library/windows/desktop/aa378712) v sadě Windows SDK.|  
|Readme.txt|*Projname*|Projekt|*Čtěte* souboru. Je generována pomocí Průvodce aplikací a popisuje soubory v projektu.|  
  
## <a name="see-also"></a>Viz také  
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)