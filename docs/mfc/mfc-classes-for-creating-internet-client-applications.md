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
ms.openlocfilehash: 7e05bfdc8af680ae8fc7412d20b57151b8581af8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554346"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>MFC – třídy pro tvorbu internetových klientských aplikací

Knihovna MFC poskytuje následující třídy a globální funkce pro psaní internetových klientských aplikací. Odsazení označuje, že třída je odvozena od třídy neodsazeného nad ním. `CGopherFile` a `CHttpFile` odvozovat `CInternetFile`, např. Tyto třídy a globální funkce jsou deklarovány v AFXINET. H, s výjimkou `CFileFind`, který je deklarován v afx –. H.

## <a name="classes"></a>Třídy

- [Cinternetsession –](../mfc/reference/cinternetsession-class.md)

- [Cinternetconnection –](../mfc/reference/cinternetconnection-class.md)

   - [Cftpconnection –](../mfc/reference/cftpconnection-class.md)

   - [Cgopherconnection –](../mfc/reference/cgopherconnection-class.md)

   - [Chttpconnection –](../mfc/reference/chttpconnection-class.md)

- [Cinternetfile –](../mfc/reference/cinternetfile-class.md)

   - [Cgopherfile –](../mfc/reference/cgopherfile-class.md)

   - [Chttpfile –](../mfc/reference/chttpfile-class.md)

- [Cfilefind –](../mfc/reference/cfilefind-class.md)

   - [Cftpfilefind –](../mfc/reference/cftpfilefind-class.md)

   - [Cgopherfilefind –](../mfc/reference/cgopherfilefind-class.md)

- [Cgopherlocator –](../mfc/reference/cgopherlocator-class.md)

- [Cinternetexception –](../mfc/reference/cinternetexception-class.md)

## <a name="global-functions"></a>Globální funkce

- [Afxparseurl –](reference/internet-url-parsing-globals.md#afxparseurl)

- [Afxgetinternethandletype –](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [Afxthrowinternetexception –](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>Viz také

[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
