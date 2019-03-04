---
title: Požadavky na třídy internetových klientů
ms.date: 11/04/2016
helpviewer_keywords:
- Internet files [MFC], writing to
- Internet [MFC], connections
- FTP (File Transfer Protocol), MFC classes
- Gopher prerequisites [MFC]
- files [MFC], writing to
- classes [MFC], connections
- HTTP [MFC], prerequisites for Internet clients
- connections [MFC], classes for
- Internet client class prerequisites [MFC]
- files [MFC], reading
- URLs [MFC], Internet client applications
- prerequisites, Internet client classes [MFC]
- Gopher client applications [MFC]
ms.assetid: c51d1dfe-260c-4228-8100-e4efd90e9599
ms.openlocfilehash: 6246db7dfb2837f5d94fa51f8433b46722c43663
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267742"
---
# <a name="prerequisites-for-internet-client-classes"></a>Požadavky na třídy internetových klientů

Některé akce internetovým klientem (čtení souboru, třeba) nejsou požadované akce (v tomto případě navazování připojení k Internetu). Následující tabulky uvádí požadavky pro některé akce klienta.

### <a name="general-internet-url-ftp-gopher-or-http"></a>Obecné Internet URL (FTP, Gopher nebo HTTP)

|Akce|Předpoklad|
|------------|------------------|
|Navázat připojení.|Vytvoření [cinternetsession –](../mfc/reference/cinternetsession-class.md) položit základ internetových klientských aplikací.|
|Otevřete adresu URL.|Navázat připojení. Volání [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl). `OpenURL` Funkce vrátí objekt prostředků jen pro čtení.|
|Data adresy URL pro čtení.|Otevřete adresu URL. Volání [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|
|Nastavte možnosti Internetu.|Navázat připojení. Volání [CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption).|
|Nastavení funkce, která se volá s informací o stavu.|Navázat připojení. Volání [CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback). Přepsat [CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) ke zpracování volání.|

### <a name="ftp"></a>FTP

|Akce|Předpoklad|
|------------|------------------|
|Navázání připojení k serveru FTP.|Vytvoření [cinternetsession –](../mfc/reference/cinternetsession-class.md) jako základ pro toto internetových klientských aplikací. Volání [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection) k vytvoření [cftpconnection –](../mfc/reference/cftpconnection-class.md) objektu.|
|Najdete první prostředek.|Navázání připojení k serveru FTP. Vytvoření [cftpfilefind –](../mfc/reference/cftpfilefind-class.md) objektu. Volání [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|
|Zobrazení výčtu všechny dostupné prostředky.|Najdete první soubor. Volání [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile) dokud vrátí hodnotu FALSE.|
|Otevřete soubor protokolu FTP.|Navázání připojení k serveru FTP. Volání [CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile) k vytváření a otevírání [cinternetfile –](../mfc/reference/cinternetfile-class.md) objektu.|
|Čtení souboru protokolu FTP.|Otevřete soubor protokolu FTP s přístupem pro čtení. Volání [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|
|Zápis do souboru protokolu FTP.|Otevřete soubor protokolu FTP s oprávněním k zápisu. Volání [CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write).|
|Změňte adresář klienta na serveru.|Navázání připojení k serveru FTP. Volání [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|
|Načte aktuální adresář klienta na serveru.|Navázání připojení k serveru FTP. Volání [CFtpConnection::GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory).|

### <a name="http"></a>HTTP

|Akce|Předpoklad|
|------------|------------------|
|Navázání připojení k protokolu HTTP.|Vytvoření [cinternetsession –](../mfc/reference/cinternetsession-class.md) jako základ pro toto internetových klientských aplikací. Volání [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection) k vytvoření [chttpconnection –](../mfc/reference/chttpconnection-class.md) objektu.|
|Otevřete soubor protokolu HTTP.|Navázání připojení k protokolu HTTP. Volání [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest) k vytvoření [chttpfile –](../mfc/reference/chttpfile-class.md) objektu. Volání [CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders). Volání [CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest).|
|Čtení souboru HTTP.|Otevřete soubor protokolu HTTP. Volání [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|
|Získejte informace o požadavku HTTP.|Navázání připojení k protokolu HTTP. Volání [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest) k vytvoření [chttpfile –](../mfc/reference/chttpfile-class.md) objektu. Call [CHttpFile::QueryInfo](../mfc/reference/chttpfile-class.md#queryinfo).|

### <a name="gopher"></a>Gopher

|Akce|Předpoklad|
|------------|------------------|
|Navázání připojení gopher.|Vytvoření [cinternetsession –](../mfc/reference/cinternetsession-class.md) jako základ pro toto internetových klientských aplikací. Volání [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection) k vytvoření [cgopherconnection –](../mfc/reference/cgopherconnection-class.md).|
|Najdete první soubor v aktuálním adresáři.|Navázání připojení gopher. Vytvoření [cgopherfilefind –](../mfc/reference/cgopherfilefind-class.md) objektu. Volání [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator) k vytvoření [cgopherlocator –](../mfc/reference/cgopherlocator-class.md) objektu. Lokátor k předání [CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile). Volání [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator) získat Lokátor souboru, pokud ji budete potřebovat později.|
|Vytvoření výčtu všech dostupných souborů.|Najdete první soubor. Volání [CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile) dokud vrátí hodnotu FALSE.|
|Otevřete soubor gopher.|Navázání připojení gopher. Vytvoření lokátoru gopher s [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator) nebo najít Lokátor s [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Volání [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|
|Čtení souboru gopher.|Otevřete soubor gopher. Použití [cgopherfile –](../mfc/reference/cgopherfile-class.md).|

## <a name="see-also"></a>Viz také:

[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[MFC – třídy pro tvorbu internetových klientských aplikací](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
