---
title: Kroky v aplikaci klienta Gopher typické | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a85e178f59eab88844b1990922870f52463f54a8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955619"
---
# <a name="steps-in-a-typical-gopher-client-application"></a>Postup v typické aplikaci klienta Gopher
Následující tabulka uvádí kroky, že které může provádět v aplikaci klienta gopher typické.  
  
|Vaším cílem|Akce, které můžete provést|Účinek|  
|---------------|----------------------|-------------|  
|Zahájit relaci gopher.|Vytvoření [CInternetSession](../mfc/reference/cinternetsession-class.md) objektu.|Inicializuje WinInet a připojí k serveru.|  
|Připojení k serveru gopher.|Použití [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection).|Vrátí [CGopherConnection](../mfc/reference/cgopherconnection-class.md) objektu.|  
|Najít první prostředek v gopher.|Použití [CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile).|Vyhledá první soubor. Vrátí hodnotu FALSE, pokud nejsou nalezeny žádné soubory.|  
|Najít další prostředek v gopher.|Použití [CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile).|Vyhledá další soubor. Vrátí hodnotu FALSE, pokud soubor nebyl nalezen.|  
|Otevřete soubor nalezena `FindFile` nebo `FindNextFile` pro čtení.|Získat gopher lokátoru pomocí [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Použití [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Otevře se soubor určený touto Lokátor. `OpenFile` Vrátí [CGopherFile](../mfc/reference/cgopherfile-class.md) objektu.|  
|Otevřete soubor pomocí lokátoru gopher, které zadáte.|Vytvořit lokátor gopher pomocí [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator). Použití [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Otevře se soubor určený touto Lokátor. `OpenFile` Vrátí [CGopherFile](../mfc/reference/cgopherfile-class.md) objektu.|  
|Čtení ze souboru.|Použití [CGopherFile](../mfc/reference/cgopherfile-class.md).|Přečte zadaný počet bajtů, pomocí vyrovnávací paměti, které zadáte.|  
|Zpracování výjimek.|Použití [CInternetException](../mfc/reference/cinternetexception-class.md) třídy.|Zpracovává všechny běžné typy výjimek Internetu.|  
|Ukončení relace gopher.|Odstranění [CInternetSession](../mfc/reference/cinternetsession-class.md) objektu.|Automaticky vyčistí otevřených popisovačů souborů a připojení.|  
  
## <a name="see-also"></a>Viz také  
 [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)   
 [Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
