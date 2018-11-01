---
title: Přetahování souborů v okně s rámečkem
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
ms.openlocfilehash: 34fb6ec6d57bcf8bc1cf51a3ac0c0db5203b3ffa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498826"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Přetahování souborů v okně s rámečkem

Okno rámce spravuje relace pomocí Průzkumníka souborů nebo Správce souborů.

Podle přidává několik inicializace v přepsání metody volá `CWinApp` členskou funkci `InitInstance`, jak je popsáno v [CWinApp: třída aplikace](../mfc/cwinapp-the-application-class.md), můžete použít okno rámce nepřímo otevřít soubory, které jsou kvůli usnadnění použití vypsány ze souboru Průzkumníka nebo Správce souborů a vyřadit v okně rámce. Zobrazit [Správce souborů přetažení](../mfc/special-cwinapp-services.md).

## <a name="see-also"></a>Viz také

[Použití oken s rámečkem](../mfc/using-frame-windows.md)

