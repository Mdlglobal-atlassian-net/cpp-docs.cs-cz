---
title: Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC]
- WinInet classes [MFC], programming
- Internet client applications [MFC], writing
- Internet applications [MFC], WinInet
- Internet applications [MFC], client applications
- MFC, Internet applications
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
ms.openlocfilehash: 6e32210217321e4eb59d7d3e666a4f5494eb3642
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399470"
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC

Základem každé internetových klientských aplikací je relace Internet. Implementuje relací Internetu jako objekty třídy knihovny MFC [cinternetsession –](../mfc/reference/cinternetsession-class.md). Pomocí této třídy, můžete vytvořit jednu relaci Internet nebo několik souběžných relací.

Ke komunikaci se serverem, je nutné [cinternetconnection –](../mfc/reference/cinternetconnection-class.md) objektu a také `CInternetSession`. Můžete vytvořit `CInternetConnection` pomocí [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection), [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection), nebo [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection). Každá z těchto volání je specifické pro daný typ protokolu. Tato volání otevřít soubor na serveru pro čtení nebo zápis. Pokud chcete číst ani zapisovat data, je nutné otevřít soubor jako samostatný krok.

U většiny relací Internetu `CInternetSession` objekt funguje ručně spolupráce s [cinternetfile –](../mfc/reference/cinternetfile-class.md) objektu:

- Pro relaci Internet, musíte vytvořit instanci [cinternetsession –](../mfc/reference/cinternetsession-class.md).

- Pokud vaše relace Internet čtení nebo zápis dat, musíte vytvořit instanci `CInternetFile` (nebo jejích podtříd [chttpfile –](../mfc/reference/chttpfile-class.md) nebo [cgopherfile –](../mfc/reference/cgopherfile-class.md)). Nejjednodušší způsob, jak číst data je volání [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl). Tato funkce analyzuje Universal Resource Locator (URL) vámi zadané, otevře připojení k serveru zadanému v poli Adresa URL a vrátí pouze pro čtení `CInternetFile` objektu. `CInternetSession::OpenURL` není specifická pro jeden protokol typu – stejné volání se dá použít pro libovolnou adresu URL protokolu FTP, HTTP nebo gopher. `CInternetSession::OpenURL` funguje i s místními soubory (vrácení `CStdioFile` místo `CInternetFile`).

- Pokud vaše připojení k Internetu relace číst nebo zapisovat data, ale provádí úkoly, jako je například odstranění souboru v adresáři služby FTP, nemusí je potřeba vytvořit instanci `CInternetFile`.

Existují dva způsoby, jak vytvořit `CInternetFile` objektu:

- Pokud používáte `CInternetSession::OpenURL` k navázání připojení k serveru, volání `OpenURL` vrátí `CStdioFile`.

- Pokud pomocí `CInternetSession::GetFtpConnection`, `GetGopherConnection`, nebo `GetHttpConnection` k navázání připojení k serveru, musí volat `CFtpConnection::OpenFile`, `CGopherConnection::OpenFile`, nebo `CHttpConnection::OpenRequest`, se vraťte `CInternetFile`, `CGopherFile`, nebo `CHttpFile`, v uvedeném pořadí.

Kroky při implementaci internetových klientských aplikací se liší v závislosti na tom, zda vytvoříte obecný internetový klient na základě `OpenURL` specifické pro protokol klienta pomocí jedné z nebo `GetConnection` funkce.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Jak se píše internetových klientských aplikací, které obecně funguje s FTP, HTTP a gopher](../mfc/steps-in-a-typical-internet-client-application.md)

- [Jak se píše aplikaci klienta FTP, který otevře soubor](../mfc/steps-in-a-typical-ftp-client-application.md)

- [Jak se píše aplikaci klienta FTP nelze otevřít soubor, který provádí operace adresáře, jako je například odstranění souboru](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)

- [Jak se píše aplikaci klienta gopher](../mfc/steps-in-a-typical-gopher-client-application.md)

- [Jak se píše aplikaci klienta HTTP](../mfc/steps-in-a-typical-http-client-application.md)

## <a name="see-also"></a>Viz také:

[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[MFC – třídy pro tvorbu internetových klientských aplikací](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)
