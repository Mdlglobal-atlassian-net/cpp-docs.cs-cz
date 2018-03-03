---
title: "Kroky v aplikaci klienta Gopher typické | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5108e997336e53434ad33030c0e79be027aa4a98
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-gopher-client-application"></a>Postup v typické aplikaci klienta Gopher
Následující tabulka uvádí kroky, že které může provádět v aplikaci klienta gopher typické.  
  
|Vaším cílem|Akce, které můžete provést|Účinek|  
|---------------|----------------------|-------------|  
|Zahájit relaci gopher.|Vytvoření [CInternetSession](../mfc/reference/cinternetsession-class.md) objektu.|Inicializuje WinInet a připojí k serveru.|  
|Připojení k serveru gopher.|Použití [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection).|Vrátí [CGopherConnection](../mfc/reference/cgopherconnection-class.md) objektu.|  
|Najít první prostředek v gopher.|Použití [CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile).|Vyhledá první soubor. Vrátí hodnotu FALSE, pokud nejsou nalezeny žádné soubory.|  
|Najít další prostředek v gopher.|Použití [CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile).|Vyhledá další soubor. Vrátí hodnotu FALSE, pokud soubor nebyl nalezen.|  
|Otevřete soubor nalezena **FindFile** nebo `FindNextFile` pro čtení.|Získat gopher lokátoru pomocí [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Použití [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Otevře se soubor určený touto Lokátor. `OpenFile`Vrátí [CGopherFile](../mfc/reference/cgopherfile-class.md) objektu.|  
|Otevřete soubor pomocí lokátoru gopher, které zadáte.|Vytvořit lokátor gopher pomocí [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator). Použití [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Otevře se soubor určený touto Lokátor. `OpenFile`Vrátí [CGopherFile](../mfc/reference/cgopherfile-class.md) objektu.|  
|Čtení ze souboru.|Použití [CGopherFile](../mfc/reference/cgopherfile-class.md).|Přečte zadaný počet bajtů, pomocí vyrovnávací paměti, které zadáte.|  
|Zpracování výjimek.|Použití [CInternetException](../mfc/reference/cinternetexception-class.md) třídy.|Zpracovává všechny běžné typy výjimek Internetu.|  
|Ukončení relace gopher.|Odstranění [CInternetSession](../mfc/reference/cinternetsession-class.md) objektu.|Automaticky vyčistí otevřených popisovačů souborů a připojení.|  
  
## <a name="see-also"></a>Viz také  
 [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)   
 [Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
