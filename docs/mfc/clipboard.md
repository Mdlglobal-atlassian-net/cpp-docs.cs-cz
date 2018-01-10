---
title: "Schránky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 304f20f94880b0bd8cb671788c5c06b69d25d377
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard"></a>Schránka
Tato řada článků vysvětluje, jak implementovat podporu pro schránky systému Windows v aplikacích MFC. Schránky systému Windows se používá dvěma způsoby:  
  
-   Implementace standardní příkazy nabídky upravit, jako je vyjmutí, kopírování a vložení.  
  
-   Implementace jednotné data přenos s přetažení a drop (OLE).  
  
 Schránka je standardní Windows metoda přenosu dat mezi zdrojem a cílem. Může být taky hodně užitečný v operacích OLE. S nástupem OLE existují dva mechanismy schránky v systému Windows. Standardní API schránky systému Windows je stále k dispozici, ale byla doplněná mechanismu přenosu dat OLE. OLE jednotný přenos dat (UDT) podporuje vyjmutí, kopírování a vložení s schránky a přetažení.  
  
 Schránka je systémová služba sdíleny celé relace systému Windows, takže nemá popisovač nebo vlastní třídu. Spravovat schránky prostřednictvím funkce člena třídy [CWnd](../mfc/reference/cwnd-class.md).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Kdy používat jednotlivé mechanismy schránky](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)  
  
-   [Pomocí rozhraní API služby tradiční schránky systému Windows](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [Použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
-   [Kopírování a vkládání dat](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Přidání dalších formátů](../mfc/clipboard-adding-other-formats.md)  
  
-   [Schránky systému Windows](https://msdn.microsoft.com/library/ms648709)  
  
-   [Implementace přetažení (OLE)](../mfc/drag-and-drop-ole.md)  
  
## <a name="see-also"></a>Viz také  
 [Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
