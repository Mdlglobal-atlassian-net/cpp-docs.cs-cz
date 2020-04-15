---
title: MFC – třídy pro tvorbu internetových klientských aplikací
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
ms.openlocfilehash: 578fd5b72e6c04610aa862f1a6631895a32a9bfe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358222"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>MFC – třídy pro tvorbu internetových klientských aplikací

Knihovna MFC poskytuje následující třídy a globální funkce pro psaní klientských aplikací Internetu. Odsazení označuje, že třída je odvozena od třídy bez odsazení nad ní. `CGopherFile`a `CHttpFile` odvozují `CInternetFile`například . Tyto třídy a globální funkce jsou deklarovány v AFXINET. H, `CFileFind`s výjimkou , který je deklarován v AFX. H.

## <a name="classes"></a>Třídy

- [CInternetSession](../mfc/reference/cinternetsession-class.md)

- [CInternetConnection](../mfc/reference/cinternetconnection-class.md)

  - [CFtpConnection](../mfc/reference/cftpconnection-class.md)

  - [CGopherPřipojení](../mfc/reference/cgopherconnection-class.md)

  - [Připojení CHttp](../mfc/reference/chttpconnection-class.md)

- [Soubor CInternetFile](../mfc/reference/cinternetfile-class.md)

  - [Soubor CGopher](../mfc/reference/cgopherfile-class.md)

  - [Soubor CHttp](../mfc/reference/chttpfile-class.md)

- [CFileFind](../mfc/reference/cfilefind-class.md)

  - [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)

  - [CGopherFileNajít](../mfc/reference/cgopherfilefind-class.md)

- [CGopherLocator](../mfc/reference/cgopherlocator-class.md)

- [Výjimka CInternet](../mfc/reference/cinternetexception-class.md)

## <a name="global-functions"></a>Globální funkce

- [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleTyp](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>Viz také

[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
