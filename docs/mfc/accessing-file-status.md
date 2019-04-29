---
title: Přístup ke stavu souboru
ms.date: 11/04/2016
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
ms.openlocfilehash: 26c263b2d7e4e0243444925cb9416cb337dcd79d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392957"
---
# <a name="accessing-file-status"></a>Přístup ke stavu souboru

`CFile` také podporuje získávání stav souboru, včetně toho, jestli soubor existuje, vytváření a úpravu dat a časů, logická velikost a cestu.

### <a name="to-get-file-status"></a>Chcete-li získat stav souboru

1. Použití [cfile –](../mfc/reference/cfile-class.md) třídy k získání a nastavení informací o souboru. Užitečné jednu aplikaci, je použít `CFile` statickou členskou funkci **GetStatus** k určení, zda soubor existuje. **GetStatus** vrátí hodnotu 0, pokud zadaný soubor neexistuje.

Proto můžete použít výsledek **GetStatus** k určení, jestli se má použít **CFile::modeCreate** příznak při otevírání souboru, jak je znázorněno v následujícím příkladu:

[!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]

Související informace naleznete v tématu [serializace](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Viz také:

[Soubory](../mfc/files-in-mfc.md)
