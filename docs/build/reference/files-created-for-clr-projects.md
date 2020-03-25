---
title: Soubory vytvořené pro projekty CLR
ms.date: 11/04/2016
helpviewer_keywords:
- Visual Studio C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
ms.openlocfilehash: 45295a3395f19d32dbf29948e1cbd15cd844adb4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169003"
---
# <a name="files-created-for-clr-projects"></a>Soubory vytvořené pro projekty CLR

Při vytváření projektů pomocí C++ vizuálních šablon se v závislosti na šabloně, kterou použijete, vytvoří několik souborů. V následující tabulce jsou uvedeny všechny soubory, které jsou vytvořeny pomocí šablon projektů pro .NET Framework projekty.

|Název souboru|Popis souboru|
|---------------|----------------------|
|AssemblyInfo. cpp|Soubor, který obsahuje informace (tj. atributy, soubory, prostředky, typy, informace o verzích, podpisové informace atd.) pro úpravu metadat sestavení projektu. Další informace najdete v tématu [Koncepty sestavení](/dotnet/framework/app-domains/assembly-contents).|
|*ProjName*. asmx|Textový soubor, který odkazuje na spravované třídy, které zapouzdřují funkce webové služby XML.|
|*ProjName*. cpp|Hlavní zdrojový soubor a vstupní bod do aplikace, kterou pro vás vytvořila aplikace Visual Studio. Identifikuje soubor Project. dll a obor názvů projektu. Zadejte vlastní kód do tohoto souboru.|
|*ProjName*. vsdisco|Soubor nasazení XML obsahující odkazy na další prostředky, které popisují webovou službu XML.|
|*ProjName*. h|Hlavní zahrnutý soubor pro projekt, který obsahuje všechny deklarace, globální symboly a direktivy `#include` pro jiné soubory hlaviček.|
|*ProjName*. sln|Soubor řešení používaný ve vývojovém prostředí k uspořádání všech prvků projektu do jediného řešení.|
|*ProjName*. suo|Soubor možností řešení používaný ve vývojovém prostředí.|
|*ProjName*. vcxproj|Soubor projektu používaný ve vývojovém prostředí, ve kterém jsou uloženy informace specifické pro tento projekt.|
|Soubor Readme. txt|Soubor popisující každý soubor v projektu pomocí skutečných názvů souborů vytvořených šablonou.|
