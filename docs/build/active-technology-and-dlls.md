---
title: Technologie Active a knihovny DLL | Dokumentace Microsoftu
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
ms.openlocfilehash: efa9a5cf17a4578fc7be9cbadc51605ee32c1650
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706248"
---
# <a name="active-technology-and-dlls"></a>Technologie Active a knihovny DLL

Technologie Active umožňuje objektových serverů uvnitř knihovny DLL úplnou implementaci. Tento typ serveru je volána v procesový server. MFC nepodporuje zcela vnitroprocesové servery pro úpravy s náhledem, všechny funkce hlavně, protože technologie Active neposkytuje způsob, jak integrovat do kontejneru hlavní smyčka zpráv serveru. MFC vyžaduje přístup k smyčky zpráv aplikace typu kontejner pro zpracování přístupové klávesy a doby nečinnosti zpracování.

Pokud píšete automatizační server a server nemá žádné uživatelské rozhraní, můžete nastavit váš server v procesový server a kompletně umístit do knihovny DLL.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Automatizační servery](../mfc/automation-servers.md)

## <a name="see-also"></a>Viz také

[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)