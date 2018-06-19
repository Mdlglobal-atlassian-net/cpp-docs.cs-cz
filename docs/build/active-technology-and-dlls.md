---
title: Technologie Active a knihovny DLL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5e0296b994f7944d5b26e98ba1b0545a03ec55b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360110"
---
# <a name="active-technology-and-dlls"></a>Technologie Active a knihovny DLL
Technologie Active umožňuje serverům objektu k implementaci zcela uvnitř knihovny DLL. Tento typ serveru se říká server v procesu. MFC nepodporuje zcela v procesu servery pro úpravy s náhledem, všechny funkce především, protože technologie Active neposkytuje způsob, jak se server připojí do kontejneru hlavní zpráva smyčky. MFC vyžaduje přístup ke smyčce zpráv aplikace typu kontejner pro zpracování klávesy akcelerátoru a zpracování doby nečinnosti.  
  
 Pokud píšete serveru automatizace a váš server nemá žádné uživatelské rozhraní, můžete nastavit váš server v rámci procesu a umístí jej zcela do knihovny DLL.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Automatizační servery](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)