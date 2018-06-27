---
title: Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC]
- WinInet classes [MFC], programming
- Internet client applications [MFC], writing
- Internet applications [MFC], WinInet
- Internet applications [MFC], client applications
- MFC, Internet applications
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00ace36eef483d8385d718e14e1fc4c5f4e9ea1e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956470"
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC
Základ pro každý internetových klientských aplikací je relace Internetu. MFC implementuje relací Internetu jako objekty třídy [CInternetSession](../mfc/reference/cinternetsession-class.md). Pomocí této třídy, můžete vytvořit jednu relaci Internet nebo několik souběžných relací.  
  
 Ke komunikaci se serverem, je nutné [CInternetConnection](../mfc/reference/cinternetconnection-class.md) objektu a také `CInternetSession`. Můžete vytvořit `CInternetConnection` pomocí [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection), [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection), nebo [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection). Každá z těchto volání je specifické pro daný typ protokolu. Tyto volání otevřít soubor na serveru pro čtení nebo zápis. Pokud máte v úmyslu číst nebo zapisovat data, musíte otevřít soubor jako samostatný krok.  
  
 Pro většinu relace Internet `CInternetSession` objekt funguje ruční v dolním s [CInternetFile](../mfc/reference/cinternetfile-class.md) objektu:  
  
-   Pro relaci Internet, musíte vytvořit instanci [CInternetSession](../mfc/reference/cinternetsession-class.md).  
  
-   Pokud vaše relace Internet čtení nebo zápisu dat, musíte vytvořit instanci `CInternetFile` (nebo její podtřídy [CHttpFile](../mfc/reference/chttpfile-class.md) nebo [CGopherFile](../mfc/reference/cgopherfile-class.md)). Nejjednodušší způsob, jak číst data je volat [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl). Tato funkce analyzuje univerzální URL (Resource Locator) vám poskytl, otevře připojení k serveru zadanému v poli Adresa URL a vrátí pouze ke čtení `CInternetFile` objektu. `CInternetSession::OpenURL` není specifické pro typ jeden protokol – stejné volání funguje pro všechny adresy URL FTP, HTTP nebo gopher. `CInternetSession::OpenURL` funguje i s místní soubory (vrácení `CStdioFile` místo `CInternetFile`).  
  
-   Pokud vaše připojení k Internetu relace číst nebo zapisovat data, ale provádí další úlohy, jako je například odstranění souboru v adresáři služby FTP nemusí budete muset vytvořit instanci `CInternetFile`.  
  
 Existují dva způsoby, jak vytvořit `CInternetFile` objektu:  
  
-   Pokud používáte `CInternetSession::OpenURL` k navázání připojení k serveru, volání `OpenURL` vrátí `CStdioFile`.  
  
-   Pokud pomocí `CInternetSession::GetFtpConnection`, `GetGopherConnection`, nebo `GetHttpConnection` k navázání připojení k serveru, musí volat `CFtpConnection::OpenFile`, `CGopherConnection::OpenFile`, nebo `CHttpConnection::OpenRequest`, vrátit `CInternetFile`, `CGopherFile`, nebo `CHttpFile`, v uvedeném pořadí.  
  
 Postup při provádění internetových klientských aplikací lišit v závislosti na tom, jestli vytvoříte obecné Internet klienta na základě `OpenURL` nebo specifické pro protokol klienta pomocí jedné z `GetConnection` funkce.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Jak lze napsat internetových klientských aplikací, který obecně funguje s FTP, HTTP a gopher](../mfc/steps-in-a-typical-internet-client-application.md)  
  
-   [Jak lze napsat aplikaci klienta FTP, který otevře soubor](../mfc/steps-in-a-typical-ftp-client-application.md)  
  
-   [Jak lze napsat aplikaci klienta FTP, která nelze otevřít soubor, ale provádí operaci adresář, jako je například odstraněním souboru](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)  
  
-   [Jak lze napsat aplikaci klienta gopher](../mfc/steps-in-a-typical-gopher-client-application.md)  
  
-   [Jak lze napsat aplikaci klienta HTTP](../mfc/steps-in-a-typical-http-client-application.md)  
  
## <a name="see-also"></a>Viz také  
 [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [MFC – třídy pro tvorbu internetových klientských aplikací](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)
