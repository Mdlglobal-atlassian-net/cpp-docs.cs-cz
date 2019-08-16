---
title: Soubory projektu a řešení
ms.date: 05/06/2019
helpviewer_keywords:
- project files [C++]
- file types [C++], makefiles
- .sdf, browsing database file
- Makefile projects
- browsing database file, .sdf
- file types [C++], project files
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
ms.openlocfilehash: 73d1733afde9dd62081d071df025c76bba5729d1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492658"
---
# <a name="project-and-solution-files"></a>Soubory projektu a řešení

Následující soubory jsou vytvořeny při vytváření projektu v aplikaci Visual Studio. Používají se ke správě souborů projektu v řešení.

|Bitmap|Umístění adresáře|Umístění Průzkumník řešení|Popis|
|--------------|------------------------|--------------------------------|-----------------|
|*Solname*. sln|*Projname*|Nezobrazuje se v Průzkumník řešení|Soubor *řešení* . Uspořádá všechny prvky projektu nebo více projektů do jednoho řešení.|
|*ProjName*. suo|*Projname*|Nezobrazuje se v Průzkumník řešení|Soubor *možností řešení* . Ukládá vaše vlastní nastavení pro řešení, takže pokaždé, když otevřete projekt nebo soubor v řešení, má vzhled a chování, které chcete.|
|*ProjName*. vcxproj|*Projname*|Nezobrazuje se v Průzkumník řešení|Soubor *projektu* . Ukládá informace specifické pro každý projekt. (V dřívějších verzích byl tento soubor nazván *ProjName*. vcproj nebo *ProjName*. DSP.) Příklad souboru C++ projektu (. vcxproj) naleznete v tématu [Project Files](project-files.md).|
|*ProjName*. vcxitems|*Projname*|Nezobrazuje se v Průzkumník řešení|Soubor *projektu sdílených položek* . Tento projekt není sestaven.  Místo toho může být projekt odkazován jiným C++ projektem a jeho soubory se stanou součástí procesu sestavení referenčního projektu. To lze použít ke sdílení společného kódu s projekty pro různé platformy C++ .|
|*Projname*.sdf|*Projname*|Nezobrazuje se v Průzkumník řešení|Soubor *databáze procházení* . Podporuje procházení a navigační funkce, jako je například **definice goto**, **vyhledání všech odkazů**a **zobrazení tříd**. Vygeneruje se pomocí analýzy hlavičkových souborů.|
|*ProjName*. vcxproj. filters|*Projname*|Nezobrazuje se v Průzkumník řešení|Soubor *filtrů* . Určuje, kam umístit soubor, který je přidán do řešení. Například soubor. h je umístěn v uzlu **soubory hlaviček** .|
|*ProjName*. vcxproj. User|*Projname*|Nezobrazuje se v Průzkumník řešení|Soubor *uživatele migrace* . Po migraci projektu ze sady Visual Studio 2008 tento soubor obsahuje informace, které byly převedeny z libovolného souboru. vsprops.|
|*ProjName*. idl|*Projname*|Source|(Specifické pro projekt) Obsahuje zdrojový kód IDL (Interface Description Language) pro knihovnu typů ovládacího prvku. Tento soubor používá vizuál C++ k vygenerování knihovny typů. Vygenerovaná knihovna zpřístupňuje rozhraní ovládacího prvku jiným klientům automatizace. Další informace naleznete v tématu [soubor definice rozhraní (IDL)](/windows/win32/Rpc/the-interface-definition-language-idl-file) v Windows SDK.|
|Readme.txt|*Projname*|Project|Soubor *Readme* . Vygeneruje ho Průvodce aplikací a popisuje soubory v projektu.|

## <a name="see-also"></a>Viz také:

[Typy souborů vytvořených pro projekty sady C++ Visual Studio](file-types-created-for-visual-cpp-projects.md)
