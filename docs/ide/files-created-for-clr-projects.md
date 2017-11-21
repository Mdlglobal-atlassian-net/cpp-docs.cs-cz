---
title: "Soubory vytvořené pro projekty CLR | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Visual C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 355b22ecf40251e3bb0b9910660e56bf9fe763a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="files-created-for-clr-projects"></a>Soubory vytvořené pro projekty CLR
Použijete-li vytvořit projekty Visual C++ šablony, jsou vytvořeny několik souborů, v závislosti na šablonu, kterou používáte. Následující tabulka uvádí všechny soubory, které jsou vytvořené pomocí šablon projektu pro projekty rozhraní .NET Framework.  
  
|Název souboru|Popis souboru|  
|---------------|----------------------|  
|AssemblyInfo.cpp|Soubor, který obsahuje informace (atributy, soubory, prostředky, typy, informace o správě verzí, podpisové informace atd.) pro úpravu metadat sestavení projektu. Další informace najdete v části [Koncepty sestavení](/dotnet/framework/app-domains/assembly-contents).|  
|*Projname*.asmx|Textový soubor, který odkazuje na spravované třídy, které zapouzdřují funkce webové služby XML.|  
|*Projname*sada|Hlavní zdrojový soubor a vstupní bod aplikace sadou Visual Studio vytvoří. Identifikuje soubor .dll projektu a obor názvů projektu. Zadejte vlastní kód v tomto souboru.|  
|*Projname*.vsdisco|XML soubor nasazení obsahující odkazy na další zdroje, které popisují webové služby XML.|  
|*Projname*.h|Hlavní soubor projektu, který obsahuje deklarace, globální symboly, a `#include` pro ostatní soubory hlaviček.|  
|*Projname*.sln|Soubor řešení v rámci vývojového prostředí používají k uspořádání všechny elementy projektu v jediném řešení.|  
|*Projname*.suo|Soubor možností řešení používá ve vývojovém prostředí.|  
|*Projname*VCXPROJ|Soubor projektu použitý v rámci vývojového prostředí, která ukládá informace specifické pro tento projekt.|  
|ReadMe.txt|Soubor s popisem každý soubor ve vašem projektu pomocí skutečné názvy souborů vytvořených šablonou.|