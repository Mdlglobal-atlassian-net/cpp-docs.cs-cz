---
title: Kroky v typické aplikaci klienta Gopher | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c547d5b2a0bc9755fdf968fc1c42643e96e6fa6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392408"
---
# <a name="steps-in-a-typical-gopher-client-application"></a>Postup v typické aplikaci klienta Gopher

Následující tabulka uvádí kroky, že které může provádět v aplikaci klienta gopher typické.

|Vaším cílem|Akce, které můžete provést|Účinek|
|---------------|----------------------|-------------|
|Zahájit relaci gopher.|Vytvoření [cinternetsession –](../mfc/reference/cinternetsession-class.md) objektu.|Inicializuje WinInet a připojí k serveru.|
|Připojení ke gopher serveru.|Použití [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection).|Vrátí [cgopherconnection –](../mfc/reference/cgopherconnection-class.md) objektu.|
|Na první prostředek hledání gopher.|Použití [CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile).|Vyhledá první soubor. Vrátí hodnotu FALSE, pokud se nenajdou žádné soubory.|
|Najdete další zdroje v gopher.|Použití [CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile).|Vyhledá další soubor. Pokud soubor není nalezen, vrátí hodnotu FALSE.|
|Otevřete soubor objevila `FindFile` nebo `FindNextFile` pro čtení.|Získat gopher lokátoru pomocí [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Použití [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Otevře se soubor určený parametrem Lokátor. `OpenFile` Vrátí [cgopherfile –](../mfc/reference/cgopherfile-class.md) objektu.|
|Otevřete soubor pomocí lokátoru gopher, které zadáte.|Vytvoření lokátoru gopher pomocí [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator). Použití [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Otevře se soubor určený parametrem Lokátor. `OpenFile` Vrátí [cgopherfile –](../mfc/reference/cgopherfile-class.md) objektu.|
|Čtení ze souboru.|Použití [cgopherfile –](../mfc/reference/cgopherfile-class.md).|Přečte zadaný počet bajtů, použilo vyrovnávací paměti, které zadáte.|
|Zpracování výjimek.|Použití [cinternetexception –](../mfc/reference/cinternetexception-class.md) třídy.|Zpracovává všechny typy výjimek common Internet.|
|Ukončení relace gopher.|Vyřazení [cinternetsession –](../mfc/reference/cinternetsession-class.md) objektu.|Automaticky vyčistí otevřené popisovače souborů a připojení.|

## <a name="see-also"></a>Viz také

[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
