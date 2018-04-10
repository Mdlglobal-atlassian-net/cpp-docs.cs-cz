---
title: Jak MFC usnadňuje tvorbu internetových klientských aplikací | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6270cdd3e64d24f1c2000acb9e8466f8c85edba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>Jak prostředí MFC usnadňuje tvorbu internetových klientských aplikací
Třídy Microsoft Foundation zapouzdřují funkce Win32 internetová rozšíření (WinInet) způsobem, který poskytuje pro programátory v jazyce MFC Známé kontext. Knihovna MFC poskytuje tři třídy souborů Internetu ([CInternetFile](../mfc/reference/cinternetfile-class.md), [CHttpFile](../mfc/reference/chttpfile-class.md), a [CGopherFile](../mfc/reference/cgopherfile-class.md)) odvozené z [CStdioFile](../mfc/reference/cstdiofile-class.md) – třída . Ne jenom tyto třídy, Nedělejte načítání a manipulace s daty Internetu pro programátory, kteří použili `CStdioFile` pro místní soubory, ale tyto třídy můžete řešit místní soubory a soubory Internet konzistentní, transparentním způsobem.  
  
 Třídy MFC WinInet poskytovat stejné funkce jako `CStdioFile` pro data, která se přenáší přes Internet. Tyto třídy abstraktní Internetové protokoly pro protokol HTTP, FTP a gopher na vysoké úrovni aplikaci programovací rozhraní, poskytuje rychlý a snadný cestu k vytvoření aplikace podporující rozhraní Internet. Například připojení k serveru FTP, stále vyžaduje několik kroků na nízké úrovni, ale jako vývojář MFC potřebujete jenom jednu hovor `CInternetSession::GetFTPConnection` k vytvoření připojení.  
  
 Kromě toho tříd WinInet knihovny MFC poskytuje následující výhody:  
  
-   Vstupně-výstupních operací ve vyrovnávací paměti  
  
-   Typově bezpečný zpracovává pro data  
  
-   Výchozí parametry pro mnoho funkcí  
  
-   Zpracování výjimek pro běžné chyby Internetu  
  
-   Automatické čištění připojení a otevřených popisovačů  
  
## <a name="see-also"></a>Viz také  
 [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Jak rozhraní WinInet usnadňuje tvorbu internetových klientských aplikací](../mfc/how-wininet-makes-it-easier-to-create-internet-client-applications.md)

