---
title: "Požadavky na třídy internetových klientů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d079edd919d54149b527330a7a3cb49fa496f676
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="prerequisites-for-internet-client-classes"></a>Požadavky na třídy internetových klientů
Některé akce provedenou internetového klienta (čtení souboru, třeba) (v tomto případě navazování připojení k Internetu) je nutné požadované akce. Následující tabulka uvádí požadavky pro některé akce klienta.  
  
### <a name="general-internet-url-ftp-gopher-or-http"></a>Adresa URL pro obecné Internet (FTP, Gopher nebo HTTP)  
  
|Akce|Předpoklad|  
|------------|------------------|  
|Navažte připojení.|Vytvoření [CInternetSession](../mfc/reference/cinternetsession-class.md) stanovení základu internetových klientských aplikací.|  
|Otevřete adresu URL.|Navažte připojení. Volání [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl). `OpenURL` Funkce vrátí objekt prostředků jen pro čtení.|  
|Data adresy URL pro čtení.|Otevřete adresu URL. Volání [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|  
|Nastavte možnosti Internetu.|Navažte připojení. Volání [CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption).|  
|Nastavení funkce, která se má volat s informace o stavu.|Navažte připojení. Volání [CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback). Přepsání [CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) pro zpracování volání.|  
  
### <a name="ftp"></a>FTP  
  
|Akce|Předpoklad|  
|------------|------------------|  
|Vytvořte připojení FTP.|Vytvoření [CInternetSession](../mfc/reference/cinternetsession-class.md) jako základ pro toto internetových klientských aplikací. Volání [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection) k vytvoření [CFtpConnection](../mfc/reference/cftpconnection-class.md) objektu.|  
|Najít první prostředek.|Vytvořte připojení FTP. Vytvoření [CFtpFileFind](../mfc/reference/cftpfilefind-class.md) objektu. Volání [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|  
|Výčet všechny dostupné prostředky.|Najít první soubor. Volání [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile) dokud vrátí hodnotu FALSE.|  
|Otevřete soubor FTP.|Vytvořte připojení FTP. Volání [CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile) k vytváření a otevírání [CInternetFile](../mfc/reference/cinternetfile-class.md) objektu.|  
|Soubor pro čtení k serveru FTP.|Otevřete soubor FTP s přístupem pro čtení. Volání [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|  
|Zápis do souboru FTP.|Otevřete soubor FTP přístup pro zápis. Volání [CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write).|  
|Změňte adresář klienta na serveru.|Vytvořte připojení FTP. Volání [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|  
|Načtěte aktuální adresář klienta na serveru.|Vytvořte připojení FTP. Volání [CFtpConnection::GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory).|  
  
### <a name="http"></a>HTTP  
  
|Akce|Předpoklad|  
|------------|------------------|  
|Navázání připojení HTTP.|Vytvoření [CInternetSession](../mfc/reference/cinternetsession-class.md) jako základ pro toto internetových klientských aplikací. Volání [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection) k vytvoření [CHttpConnection](../mfc/reference/chttpconnection-class.md) objektu.|  
|Otevřete soubor protokolu HTTP.|Navázání připojení HTTP. Volání [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest) k vytvoření [CHttpFile](../mfc/reference/chttpfile-class.md) objektu. Volání [CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders). Volání [CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest).|  
|Přečtěte si soubor protokolu HTTP.|Otevřete soubor protokolu HTTP. Volání [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|  
|Získáte informace o požadavku HTTP.|Navázání připojení HTTP. Volání [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest) k vytvoření [CHttpFile](../mfc/reference/chttpfile-class.md) objektu. Volání [CHttpFile::QueryInfo](../mfc/reference/chttpfile-class.md#queryinfo).|  
  
### <a name="gopher"></a>Gopher  
  
|Akce|Předpoklad|  
|------------|------------------|  
|Gopher připojení.|Vytvoření [CInternetSession](../mfc/reference/cinternetsession-class.md) jako základ pro toto internetových klientských aplikací. Volání [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection) k vytvoření [CGopherConnection](../mfc/reference/cgopherconnection-class.md).|  
|Najít první soubor v aktuálním adresáři.|Gopher připojení. Vytvoření [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md) objektu. Volání [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator) k vytvoření [CGopherLocator](../mfc/reference/cgopherlocator-class.md) objektu. Předat Lokátor k [CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile). Volání [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator) získat Lokátor souboru, pokud ji budete potřebovat později.|  
|Výčet všech dostupných souborů.|Najít první soubor. Volání [CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile) dokud vrátí hodnotu FALSE.|  
|Otevřete soubor gopher.|Gopher připojení. Vytvořit lokátor gopher s [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator) nebo najít lokátoru s [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Volání [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|  
|Čtení z gopher souboru.|Otevřete soubor gopher. Použití [CGopherFile](../mfc/reference/cgopherfile-class.md).|  
  
## <a name="see-also"></a>Viz také  
 [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [MFC – třídy pro tvorbu internetových klientských aplikací](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
