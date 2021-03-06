---
title: Postup v typické aplikaci klienta FTP
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
ms.openlocfilehash: d08edf704e748767f3b566252ad328baf40b55ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307013"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>Postup v typické aplikaci klienta FTP

Vytvoří v typické aplikaci klienta FTP [cinternetsession –](../mfc/reference/cinternetsession-class.md) a [cftpconnection –](../mfc/reference/cftpconnection-class.md) objektu. Všimněte si, že těchto tříd WinInet knihovny MFC ve skutečnosti neovládají typ nastavení proxy serveru; Služba IIS neodpovídá.

Následující tabulka uvádí kroky, že které může provádět v typické aplikaci klienta FTP.

|Vaším cílem|Akce, které můžete provést|Účinek|
|---------------|----------------------|-------------|
|Proces relace FTP.|Vytvoření [cinternetsession –](../mfc/reference/cinternetsession-class.md) objektu.|Inicializuje WinInet a připojí k serveru.|
|Připojte se k serveru FTP.|Použití [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Vrátí [cftpconnection –](../mfc/reference/cftpconnection-class.md) objektu.|
|Přejděte do nového adresáře FTP na serveru.|Použití [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Změní na adresář, který jste aktuálně připojeni k serveru.|
|Najdete první soubor v adresáři serveru FTP.|Použití [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Vyhledá první soubor. Vrátí hodnotu FALSE, pokud se nenajdou žádné soubory.|
|Najdete další soubor v adresáři serveru FTP.|Použití [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Vyhledá další soubor. Pokud soubor není nalezen, vrátí hodnotu FALSE.|
|Otevřete soubor objevila `FindFile` nebo `FindNextFile` pro čtení nebo zápis.|Použití [CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile), pomocí názvu souboru vrácený [FindFile](../mfc/reference/cftpfilefind-class.md#findfile) nebo [FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Otevře soubor na serveru pro čtení nebo zápis. Vrátí [cinternetfile –](../mfc/reference/cinternetfile-class.md) objektu.|
|Čtení nebo zápis do souboru.|Použití [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read) nebo [CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write).|Čtení nebo zápis zadaný počet bajtů, použilo vyrovnávací paměti, které zadáte.|
|Zpracování výjimek.|Použití [cinternetexception –](../mfc/reference/cinternetexception-class.md) třídy.|Zpracovává všechny typy výjimek common Internet.|
|Ukončení relace FTP.|Vyřazení [cinternetsession –](../mfc/reference/cinternetsession-class.md) objektu.|Automaticky vyčistí otevřené popisovače souborů a připojení.|

## <a name="see-also"></a>Viz také:

[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
