---
title: Win32 – internetové třídy
ms.date: 09/12/2018
f1_keywords:
- vc.classes.win32
helpviewer_keywords:
- Internet classes [MFC]
- WinInet classes [MFC], classes
- Win32 [MFC], Internet classes
- Windows API [MFC], Internet classes
ms.assetid: b49601d5-3025-4068-9408-316b54ee4375
ms.openlocfilehash: c067d0c0067ee13b0e6ce6d84fd97135274c88b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326726"
---
# <a name="win32-internet-classes"></a>Win32 – internetové třídy

MFC zabaluje internetové Win32 (WinInet) a technologii ActiveX pro usnadnění programování na Internetu.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

[CInternetSession](../mfc/reference/cinternetsession-class.md)<br/>
Vytvoří a inicializuje jednu relaci Internet nebo několik souběžných relací Internetu a v případě potřeby popisuje připojení k proxy serveru.

[CInternetConnection](../mfc/reference/cinternetconnection-class.md)<br/>
Spravuje připojení k internetovému serveru.

[CInternetFile](../mfc/reference/cinternetfile-class.md)<br/>
Tato třída a odvozené třídy povolit přístup k souborům ve vzdálených systémech, které používají protokoly sítě Internet.

[CHttpConnection](../mfc/reference/chttpconnection-class.md)<br/>
Spravuje připojení k serveru HTTP.

[CHttpFile](../mfc/reference/chttpfile-class.md)<br/>
Poskytuje funkce pro hledání a čtení souborů na HTTP server.

[CGopherFile](../mfc/reference/cgopherfile-class.md)<br/>
Poskytuje funkce pro hledání a čtení souborů na gopher serveru.

[CFtpConnection](../mfc/reference/cftpconnection-class.md)<br/>
Spravuje připojení k serveru FTP.

[CGopherConnection](../mfc/reference/cgopherconnection-class.md)<br/>
Spravuje připojení ke gopher serveru.

[CFileFind](../mfc/reference/cfilefind-class.md)<br/>
Provádí místní a hledání internetových souborů.

[CFtpFileFind](../mfc/reference/cftpfilefind-class.md)<br/>
Pomáhá při hledání internetových souborů na serverech FTP.

[CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)<br/>
Pomáhá při hledání internetových souborů na serverech gopher.

[CGopherLocator](../mfc/reference/cgopherlocator-class.md)<br/>
Získá gopher "Lokátor" ze serveru gopher, určí typ lokátoru a zpřístupní Lokátor `CGopherFileFind`.

[CInternetException](../mfc/reference/cinternetexception-class.md)<br/>
Představuje podmínku výjimky vztahující se k Internetu operaci.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
