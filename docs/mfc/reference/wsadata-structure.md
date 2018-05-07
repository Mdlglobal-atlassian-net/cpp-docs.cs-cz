---
title: Wsadata – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WSADATA
dev_langs:
- C++
helpviewer_keywords:
- WSADATA structure [MFC]
ms.assetid: 80cc60e5-f9ae-4290-8ed5-07003136627d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93c98f792e1d72d3e6d4a8e15b8347c653b32f46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wsadata-structure"></a>WSADATA – struktura
`WSADATA` Struktura se používá k ukládání vrácené voláním rozhraní Windows Sockets inicializace informace `AfxSocketInit` globální funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct WSAData {  
    WORD wVersion;  
    WORD wHighVersion;  
    char szDescription[WSADESCRIPTION_LEN+1];  
    char szSystemStatus[WSASYSSTATUS_LEN+1];  
    unsigned short iMaxSockets;  
    unsigned short iMaxUdpDg;  
    char FAR* lpVendorInfo;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 *wVersion*  
 Verze specifikace rozhraní Windows Sockets že Knihovnu Windows Sockets očekává, že volající používat.  
  
 *wHighVersion*  
 Nejvyšší verze Windows Sockets specifikace, který podporuje tuto knihovnu DLL (také kódovaný jako výše). Za normálních okolností je to stejné jako **wVersion**.  
  
 *szDescription*  
 Ukončené hodnotou null ASCII řetězec, do kterého Knihovnu Windows Sockets zkopíruje popis implementace rozhraní Windows Sockets, včetně identifikace dodavatele. Text (až 256 znaků) může obsahovat libovolné znaky, ale jsou dodavatelé cautioned proti včetně ovládacího prvku a formátování znaků: pravděpodobně používání, která aplikace to uvedli do se zobrazte jej (pravděpodobně zkrácen) v stavovou zprávu.  
  
 *szSystemStatus*  
 Ukončené hodnotou null ASCII řetězec, do kterého Knihovnu Windows Sockets zkopíruje relevantní informace o stavu nebo konfigurace. Knihovnu Windows Sockets má toto pole použít pouze v případě, že informace může být užitečná pro uživatele nebo pracovníci; nemělo by se používat jako rozšíření nástroje **szDescription** pole.  
  
 *iMaxSockets*  
 Maximální počet soketů, které mohou potenciálně otevřít jeden proces. Implementace rozhraní Windows Sockets může poskytnout globální fond soketů pro přidělení jakýkoli proces; případně ho můžete přidělit prostředky podle procesu pro sokety. Číslo můžete projeví i způsob, ve kterém byla nakonfigurována Knihovnu Windows Sockets nebo síťový software. Zapisovače aplikace můžete použít tento počet jako hrubý ukazatel toho, zda je implementace rozhraní Windows Sockets použitelná pro aplikace. Například může zkontrolovat serveru X Windows **iMaxSockets** při prvním spuštění: Pokud je menší než 8, aplikace se zobrazí se chybová zpráva informuje uživatele o překonfigurovat síťový software. (Toto je situace, ve kterém **szSystemStatus** text může být používán.) Samozřejmě není zaručeno, konkrétní aplikace ve skutečnosti můžete přidělit **iMaxSockets** soketů, protože může být jiné aplikace rozhraní Windows Sockets používán.  
  
 *iMaxUdpDg*  
 Velikost v bajtech největšího datagramu protokolu UDP (User Datagram), který může odesílat nebo přijímat Windows Sockets aplikace. Pokud implementace ukládá žádný limit, **iMaxUdpDg** je nulová. V mnoha implementacích Berkeley soketů existuje implicitní maximální 8192 bajtů na datagramy UDP (které jsou fragmentovaná. v případě potřeby). Implementace rozhraní Windows Sockets použít omezení, například na základě přidělení vyrovnávací paměti fragment nového sestavení. Minimální hodnota **iMaxUdpDg** pro kompatibilní s Windows Sockets implementace je 512. Všimněte si, že bez ohledu na hodnotu **iMaxUdpDg**, není vhodné pokus o odeslání datagram všesměrového vysílání, která je větší než maximální přenosové jednotky (MTU) pro síť. (Rozhraní API systému Windows Sockets neposkytuje mechanismus pro zjištění MTU, ale musí být menší než 512 bajtů.)  
  
 *lpVendorInfo*  
 Úplně ukazatel na strukturu dat specifické pro dodavatele. Definice této struktury (Pokud je zadaný) je nad rámec specifikace rozhraní Windows Sockets.  
  
> [!NOTE]
>  V prostředí MFC `WSADATA` struktura je vrácený `AfxSocketInit` funkce, která se volá v vaší `InitInstance` funkce. Můžete načíst strukturu a uložit v programu, pokud budete muset použít informace z něj později.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winsock2.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit)

