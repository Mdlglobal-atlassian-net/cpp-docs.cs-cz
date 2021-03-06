---
title: Postup v typické aplikaci klienta HTTP
ms.date: 11/04/2016
helpviewer_keywords:
- HTTP client applications [MFC]
- client applications [MFC], HTTP
- Internet applications [MFC], HTTP client applications
- applications [MFC], HTTP client
- Internet client applications [MFC], HTTP table
- WinInet classes [MFC], HTTP
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
ms.openlocfilehash: 59b585d3e6b8c9f13c585f5a712d33abd6123f67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306961"
---
# <a name="steps-in-a-typical-http-client-application"></a>Postup v typické aplikaci klienta HTTP

Následující tabulka uvádí kroky, že které může provádět v typické aplikaci klienta HTTP:

|Vaším cílem|Akce, které můžete provést|Účinek|
|---------------|----------------------|-------------|
|Zahájit relaci protokolu HTTP.|Vytvoření [cinternetsession –](../mfc/reference/cinternetsession-class.md) objektu.|Inicializuje WinInet a připojí k serveru.|
|Připojte se k serveru HTTP.|Použití [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection).|Vrátí [chttpconnection –](../mfc/reference/chttpconnection-class.md) objektu.|
|Otevřete požadavek HTTP.|Použití [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest).|Vrátí [chttpfile –](../mfc/reference/chttpfile-class.md) objektu.|
|Odeslání požadavku HTTP.|Použití [CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders) a [CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest).|Vyhledá soubor. Pokud soubor není nalezen, vrátí hodnotu FALSE.|
|Čtení ze souboru.|Použití [chttpfile –](../mfc/reference/chttpfile-class.md).|Přečte zadaný počet bajtů pomocí vyrovnávací paměti, které zadáte.|
|Zpracování výjimek.|Použití [cinternetexception –](../mfc/reference/cinternetexception-class.md) třídy.|Zpracovává všechny typy výjimek common Internet.|
|Ukončit relaci protokolu HTTP.|Vyřazení [cinternetsession –](../mfc/reference/cinternetsession-class.md) objektu.|Automaticky vyčistí otevřené popisovače souborů a připojení.|

## <a name="see-also"></a>Viz také:

[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
