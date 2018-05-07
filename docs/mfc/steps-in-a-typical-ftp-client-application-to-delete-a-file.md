---
title: Kroky typické aplikaci klienta FTP chcete odstranit soubor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], FTP delete
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb595dfdc1a73ecd068e251cec5df99d4daaab30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="steps-in-a-typical-ftp-client-application-to-delete-a-file"></a>Postup odstranění souboru v typické aplikaci klienta FTP
Následující tabulka uvádí kroky, které můžete provést v typické aplikaci klienta FTP, který odstraní soubor.  
  
|Vaším cílem|Akce, které můžete provést|Účinek|  
|---------------|----------------------|-------------|  
|Zahájení relace FTP.|Vytvoření [CInternetSession](../mfc/reference/cinternetsession-class.md) objektu.|Inicializuje WinInet a připojí k serveru.|  
|Připojte k serveru FTP.|Použití [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Vrátí [CFtpConnection](../mfc/reference/cftpconnection-class.md) objektu.|  
|Zkontrolujte, ujistěte se, že jste v pravém adresáři na serveru FTP.|Použití [CFtpConnection::GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory) nebo [CFtpConnection::GetCurrentDirectoryAsURL](../mfc/reference/cftpconnection-class.md#getcurrentdirectoryasurl).|Vrátí název nebo adresa URL adresáře, který jste aktuálně připojeni k na serveru, v závislosti na vybrané členské funkce.|  
|Změnit na nový adresář serveru FTP na serveru.|Použití [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Změní na adresář, který jste aktuálně připojeni k na serveru.|  
|Najít první soubor v adresáři serveru FTP.|Použití [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Vyhledá první soubor. Vrátí hodnotu FALSE, pokud nejsou nalezeny žádné soubory.|  
|Najít další soubor v adresáři serveru FTP.|Použití [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Vyhledá další soubor. Vrátí hodnotu FALSE, pokud soubor nebyl nalezen.|  
|Odstraňte soubor nalezena **FindFile** nebo `FindNextFile`.|Použití [CFtpConnection::Remove](../mfc/reference/cftpconnection-class.md#remove), pomocí názvu souboru vrácený **FindFile** nebo `FindNextFile`.|Odstraní soubor na serveru pro čtení nebo zápis.|  
|Zpracování výjimek.|Použití [CInternetException](../mfc/reference/cinternetexception-class.md) třídy.|Zpracovává všechny běžné typy výjimek Internetu.|  
|Ukončení relace FTP.|Odstranění [CInternetSession](../mfc/reference/cinternetsession-class.md) objektu.|Automaticky vyčistí otevřených popisovačů souborů a připojení.|  
  
## <a name="see-also"></a>Viz také  
 [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)   
 [Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
