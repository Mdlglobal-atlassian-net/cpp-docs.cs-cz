---
title: "Kroky typické aplikaci klienta FTP | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a092c79bcd2f64793d43990cb6ee2900a8c4734a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="steps-in-a-typical-ftp-client-application"></a>Postup v typické aplikaci klienta FTP
Vytvoří typické aplikaci klienta FTP [CInternetSession](../mfc/reference/cinternetsession-class.md) a [CFtpConnection](../mfc/reference/cftpconnection-class.md) objektu. Všimněte si, že těchto tříd WinInet knihovny MFC ve skutečnosti nebudete řídit typ nastavení proxy serveru; Služba IIS neodpovídá.  
  
 Také naleznete v článcích znalostní báze Knowledge Base:  
  
-   POSTUPY: FTP s Proxy na základě CERN pomocí WinInet rozhraní API (ID článku: Q166961)  
  
-   Ukázka: FTP na základě CERN heslem chráněné Proxy (ID článku: Q216214)  
  
-   Internetové služby nepodaří Manager zobrazit nainstalované Proxy služby (ID článku: Q216802)  
  
 Následující tabulka uvádí kroky, že které může provádět v typické aplikaci klienta FTP.  
  
|Vaším cílem|Akce, které můžete provést|Účinek|  
|---------------|----------------------|-------------|  
|Zahájení relace FTP.|Vytvoření [CInternetSession](../mfc/reference/cinternetsession-class.md) objektu.|Inicializuje WinInet a připojí k serveru.|  
|Připojte k serveru FTP.|Použití [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Vrátí [CFtpConnection](../mfc/reference/cftpconnection-class.md) objektu.|  
|Změnit na nový adresář serveru FTP na serveru.|Použití [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Změní na adresář, který jste aktuálně připojeni k na serveru.|  
|Najít první soubor v adresáři serveru FTP.|Použití [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Vyhledá první soubor. Vrátí hodnotu FALSE, pokud nejsou nalezeny žádné soubory.|  
|Najít další soubor v adresáři serveru FTP.|Použití [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Vyhledá další soubor. Vrátí hodnotu FALSE, pokud soubor nebyl nalezen.|  
|Otevřete soubor nalezena **FindFile** nebo `FindNextFile` pro čtení nebo zápis.|Použití [CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile), pomocí názvu souboru vrácený [FindFile](../mfc/reference/cftpfilefind-class.md#findfile) nebo [FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Otevře se soubor na serveru pro čtení nebo zápis. Vrátí [CInternetFile](../mfc/reference/cinternetfile-class.md) objektu.|  
|Čtení z a zapisovat do souboru.|Použití [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read) nebo [CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write).|Čtení nebo zápisu zadaný počet bajtů, pomocí vyrovnávací paměti, které zadáte.|  
|Zpracování výjimek.|Použití [CInternetException](../mfc/reference/cinternetexception-class.md) třídy.|Zpracovává všechny běžné typy výjimek Internetu.|  
|Ukončení relace FTP.|Odstranění [CInternetSession](../mfc/reference/cinternetsession-class.md) objektu.|Automaticky vyčistí otevřených popisovačů souborů a připojení.|  
  
## <a name="see-also"></a>Viz také  
 [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)   
 [Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
