---
title: "Kroky typické aplikaci klienta HTTP | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTTP client applications [MFC]
- client applications [MFC], HTTP
- Internet applications [MFC], HTTP client applications
- applications [MFC], HTTP client
- Internet client applications [MFC], HTTP table
- WinInet classes [MFC], HTTP
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 936914a816f109736d38259908608b42b7bdcb00
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-http-client-application"></a>Postup v typické aplikaci klienta HTTP
Následující tabulka uvádí kroky, že které může provádět v typické aplikaci klienta HTTP:  
  
|Vaším cílem|Akce, které můžete provést|Účinek|  
|---------------|----------------------|-------------|  
|Zahájit relaci protokolu HTTP.|Vytvoření [CInternetSession](../mfc/reference/cinternetsession-class.md) objektu.|Inicializuje WinInet a připojí k serveru.|  
|Připojte k serveru HTTP.|Použití [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection).|Vrátí [CHttpConnection](../mfc/reference/chttpconnection-class.md) objektu.|  
|Otevřete požadavek HTTP.|Použití [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest).|Vrátí [CHttpFile](../mfc/reference/chttpfile-class.md) objektu.|  
|Odeslání požadavku HTTP.|Použití [CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders) a [CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest).|Vyhledá soubor. Vrátí hodnotu FALSE, pokud soubor nebyl nalezen.|  
|Čtení ze souboru.|Použití [CHttpFile](../mfc/reference/chttpfile-class.md).|Přečte zadaný počet bajtů pomocí vyrovnávací paměti, které zadáte.|  
|Zpracování výjimek.|Použití [CInternetException](../mfc/reference/cinternetexception-class.md) třídy.|Zpracovává všechny běžné typy výjimek Internetu.|  
|Ukončení relace HTTP.|Odstranění [CInternetSession](../mfc/reference/cinternetsession-class.md) objektu.|Automaticky vyčistí otevřených popisovačů souborů a připojení.|  
  
## <a name="see-also"></a>Viz také  
 [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)   
 [Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
