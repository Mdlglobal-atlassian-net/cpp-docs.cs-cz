---
title: Přístup ke stavu souboru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d424502e991ea355a6e31bba8fedccb6d5ad2fcf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334292"
---
# <a name="accessing-file-status"></a>Přístup ke stavu souboru
`CFile` také podporuje získání stavu souboru, včetně toho, jestli soubor existuje, vytváření a úpravy data a časy, logické velikosti a cestu.  
  
### <a name="to-get-file-status"></a>Chcete-li získat stav souboru  
  
1.  Použití [cfile –](../mfc/reference/cfile-class.md) třída k získání a nastavení informací o souboru. Jedna užitečné aplikace, je použít `CFile` funkce statický člen **GetStatus** k určení, zda soubor existuje. **GetStatus –** vrátí hodnotu 0, pokud zadaný soubor neexistuje.  
  
 Proto můžete použít výsledek **GetStatus** k určení, zda se má použít **CFile::modeCreate** příznak při otevírání souboru, jak je znázorněno v následujícím příkladu:  
  
 [!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]  
  
 Související informace najdete v tématu [serializace](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Soubory](../mfc/files-in-mfc.md)

