---
title: "Kroky v typické internetové klientské aplikace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c435a4100189d8561be9217a970bfb4a5917908e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="steps-in-a-typical-internet-client-application"></a>Postup v typické internetové klientské aplikaci
Následující tabulka uvádí kroky, že které může provádět v typické internetové klientské aplikaci.  
  
|Vaším cílem|Akce, které můžete provést|Účinek|  
|---------------|----------------------|-------------|  
|Zahájit relaci Internet.|Vytvoření [CInternetSession](../mfc/reference/cinternetsession-class.md) objektu.|Inicializuje WinInet a připojí k serveru.|  
|Nastavte možnost dotazu Internet (časový limit nebo počet opakování, např.).|Použití [CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption).|Vrátí hodnotu FALSE, pokud byla operace neúspěšná.|  
|Vytvořte funkci zpětného volání k monitorování stavu relace.|Použití [CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback).|Zpětné volání pro zakládá [CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback). Přepsání `OnStatusCallback` vytvořit vlastní rutina zpětného volání.|  
|Připojte k serveru Internet, intranetový server nebo místního souboru.|Použití [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl).|Analyzuje adresu URL a otevře připojení k zadanému serveru. Vrátí [CStdioFile](../mfc/reference/cstdiofile-class.md) (Pokud předáte `OpenURL` názvu místního souboru). Toto je objekt, pomocí kterého můžete přistupovat k datům načíst ze serveru nebo souboru.|  
|Čtení ze souboru.|Použití [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|Přečte zadaný počet bajtů pomocí vyrovnávací paměti, které zadáte.|  
|Zpracování výjimek.|Použití [CInternetException](../mfc/reference/cinternetexception-class.md) třídy.|Zpracovává všechny běžné typy výjimek Internetu.|  
|Ukončení relace Internetu.|Odstranění [CInternetSession](../mfc/reference/cinternetsession-class.md) objektu.|Automaticky vyčistí otevřených popisovačů souborů a připojení.|  
  
## <a name="see-also"></a>Viz také  
 [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Požadavky na třídy internetových klientů](../mfc/prerequisites-for-internet-client-classes.md)   
 [Psaní internetových klientských aplikací pomocí tříd WinInet knihovny MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
