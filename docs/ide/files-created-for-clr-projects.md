---
title: Soubory vytvořené pro projekty CLR | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bd76a978c1c85969883b8222097f29f501fd960
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385349"
---
# <a name="files-created-for-clr-projects"></a>Soubory vytvořené pro projekty CLR

Použijete-li vytvořit projekty Visual C++ šablony, se vytvoří několik souborů, závisti na šabloně, použijete. Následující tabulka uvádí všechny soubory, které jsou vytvořeny pomocí šablony projektů pro projekty .NET Framework.

|Název souboru|Popis souboru|
|---------------|----------------------|
|AssemblyInfo.cpp|Soubor, který obsahuje informace (to znamená, atributy, soubory, prostředky, typy, informace o verzi, podpisové informace a tak dále) k úpravě metadat sestavení projektu. Další informace najdete v části [Koncepty sestavení](/dotnet/framework/app-domains/assembly-contents).|
|*název_projektu*asmx|Textový soubor, který odkazuje na spravované třídy, které zapouzdřují funkce webové služby XML.|
|*Název_projektu*.cpp|Hlavní zdrojový soubor a vstupní bod do aplikace sady Visual Studio vytvoří za vás. Identifikuje soubor .dll projektu a obor názvů projektu. Zadejte vlastní kód v tomto souboru.|
|*název_projektu*.vsdisco|Nasazení souboru XML obsahující odkazy na další prostředky, které popisují webové služby XML.|
|*Název_projektu*.h|Zahrnout hlavní soubor projektu, který obsahuje všechny deklarace, globální symboly, a `#include` direktivy pro další hlavičkové soubory.|
|*název_projektu*.sln|Soubor řešení používaný v rámci vývojového prostředí uspořádat všechny prvky vašeho projektu v rámci jednoho řešení.|
|*Název_projektu*.suo|Soubor možností řešení použít v rámci vývojového prostředí.|
|*Název_projektu*.vcxproj|Soubor projektu používá v rámci vývojového prostředí, který obsahuje informace specifické pro tento projekt.|
|ReadMe.txt|Soubor s popisem každý soubor v projektu pomocí skutečné názvy souborů vytvořených šablonou.|