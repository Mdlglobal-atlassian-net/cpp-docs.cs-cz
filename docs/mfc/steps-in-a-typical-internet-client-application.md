---
title: Postup v typické internetové klientské aplikaci
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
ms.openlocfilehash: 9762e762680e2ac530b87baeac7afdea77ef6f14
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265740"
---
# <a name="steps-in-a-typical-internet-client-application"></a>Postup v typické internetové klientské aplikaci

Následující tabulka uvádí kroky, že které může provádět v typické internetové klientské aplikaci.

|Vaším cílem|Akce, které můžete provést|Účinek|
|---------------|----------------------|-------------|
|Zahájit relaci k Internetu.|Vytvoření [cinternetsession –](../mfc/reference/cinternetsession-class.md) objektu.|Inicializuje WinInet a připojí k serveru.|
|Nastavte dotaz možnost Internet (časový limit nebo počet opakovaných pokusů u příkladu).|Použití [CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption).|Vrátí hodnotu FALSE, pokud byla operace neúspěšná.|
|Vytvoření funkce zpětného volání k monitorování stavu relace.|Použití [CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback).|Vytvoří zpětné volání, aby [CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback). Přepsat `OnStatusCallback` k vytvoření vlastní rutina zpětného volání.|
|Připojení k serveru Internet, intranetový server nebo místní soubor.|Použití [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl).|Analyzuje adresu URL a otevře připojení k zadanému serveru. Vrátí [cstdiofile –](../mfc/reference/cstdiofile-class.md) (Pokud předáte `OpenURL` název místního souboru). Jedná se o objekt, přes který přistupujete data načtená ze serveru nebo souboru.|
|Čtení ze souboru.|Použití [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|Přečte zadaný počet bajtů pomocí vyrovnávací paměti, které zadáte.|
|Zpracování výjimek.|Použití [cinternetexception –](../mfc/reference/cinternetexception-class.md) třídy.|Zpracovává všechny typy výjimek common Internet.|
|Ukončení relace Internet.|Vyřazení [cinternetsession –](../mfc/reference/cinternetsession-class.md) objektu.|Automaticky vyčistí otevřené popisovače souborů a připojení.|

## <a name="see-also"></a>Viz také:

[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
