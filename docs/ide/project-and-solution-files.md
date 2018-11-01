---
title: Soubory projektu a řešení
ms.date: 11/04/2016
f1_keywords:
- vc.files.projectandsolution
helpviewer_keywords:
- project files [C++]
- file types [C++], makefiles
- .sdf, browsing database file
- Makefile projects
- browsing database file, .sdf
- file types [C++], project files
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
ms.openlocfilehash: 8b84c28db2afb914a73a0cb4d0d778c99cfd6635
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616634"
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
|*Název_projektu*IDL|*Projname*|Zdroj|(Specifické pro projekt) Obsahuje popis jazyka IDL (Interface) zdrojový kód pro knihovnu typů ovládacího prvku. Tento soubor se používá ve Visual C++ generovat knihovnu typů. Vygenerovaný knihovna poskytuje rozhraní ovládacího prvku jiným klientům automatizace. Další informace najdete v tématu [soubor Interface Definition (IDL)](/windows/desktop/Rpc/the-interface-definition-language-idl-file) v sadě Windows SDK.|
|Readme.txt|*Projname*|Projekt|*Čtěte* souboru. Je generována pomocí Průvodce aplikací a popisuje soubory v projektu.|

## <a name="see-also"></a>Viz také

[Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)