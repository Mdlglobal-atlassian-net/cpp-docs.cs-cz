---
title: WSADATA – struktura
ms.date: 11/04/2016
f1_keywords:
- WSADATA
helpviewer_keywords:
- WSADATA structure [MFC]
ms.assetid: 80cc60e5-f9ae-4290-8ed5-07003136627d
ms.openlocfilehash: 06e8423a00ecfe5179dbfe3e03f61dbf1ef870b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474019"
---
# <a name="wsadata-structure"></a>WSADATA – struktura

`WSADATA` Struktura se používá k ukládání informací o inicializaci rozhraní Windows Sockets vrácený voláním `AfxSocketInit` globální funkce.

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

*wVersion*<br/>
Verze specifikace rozhraní Windows Sockets, knihovny DLL Windows Sockets očekává, že volající použít.

*wHighVersion*<br/>
Nejvyšší verze specifikace rozhraní Windows Sockets, který podporuje tuto knihovnu DLL (také kódovaný jak je uvedeno výše). Za normálních okolností je to stejné jako *wVersion*.

*szDescription*<br/>
Řetězec zakončený hodnotou null ASCII do kterého kopíruje Windows Sockets DLL popis implementaci rozhraní Windows Sockets, včetně identifikace dodavatele. Text (až 256 znaků) může obsahovat libovolné znaky, ale dodavatelé se zobrazí se upozornění před včetně ovládacího prvku a formátování znaků: pravděpodobně použití, která tato aplikace bude zařazení do je zobrazíte (pravděpodobně zkrácen) v stavovou zprávu.

*szSystemStatus*<br/>
Řetězec zakončený hodnotou null ASCII do kterého kopíruje Windows Sockets DLL relevantní informace o stavu nebo konfigurace. Knihovna DLL Windows Sockets by toto pole použít pouze v případě, že informace může být užitečné pro uživatele nebo pracovníci; podpory by neměly být zahrnuté jako rozšíření *szDescription* pole.

*iMaxSockets*<br/>
Maximální počet soketů, které mohou potenciálně otevřít jeden proces. Implementace rozhraní Windows Sockets můžete zadat globální fond soketů pro přidělení k libovolnému procesu; případně ho můžete přidělit prostředky na úrovni jednotlivého procesu soketů. Číslo můžete také sledovat způsob, ve kterém byl nakonfigurován Windows Sockets DLL nebo síťovým softwarem. Uživatelé vytvářející obsah aplikace můžete tohle číslo použít jako hrubých označení, zda je použitelný pro aplikaci implementace rozhraní Windows Sockets. Například může zkontrolovat serveru Windows X *iMaxSockets* při prvním spuštění: Pokud je menší než 8, aplikace zobrazí chybová zpráva informuje uživatele o překonfigurovat síťový software. (To je naopak situace, ve kterém *szSystemStatus* text může být používán.) Samozřejmě neexistuje žádná záruka, že ve skutečnosti můžete přiřadit konkrétní aplikace *iMaxSockets* soketů, protože můžou existovat jiné aplikace rozhraní Windows Sockets používá.

*iMaxUdpDg*<br/>
Velikost v bajtech největšího datagramu protokolu UDP (User Datagram), která můžete odesílat nebo přijímat aplikace rozhraní Windows Sockets. Pokud implementace ukládá bez omezení *iMaxUdpDg* je nula. Mnoho implementací Berkeley soketů je omezený na implicitní 8192 bajtů na datagramů UDP (které jsou fragmentovaná. v případě potřeby). Implementace rozhraní Windows Sockets můžete omezit, například na základě přidělení vyrovnávací paměti fragment nového sestavení. Minimální hodnota *iMaxUdpDg* pro kompatibilní rozhraní Windows Sockets implementace je 512. Všimněte si, že bez ohledu na hodnotu *iMaxUdpDg*, není vhodné pokusilo odeslat všesměrového vysílání datagramu, který je větší než maximální přenosové jednotky (MTU) pro síť. (Rozhraní Windows Sockets API neposkytuje mechanismus pro zjišťování MTU, ale musí být menší než 512 bajtů.)

*lpVendorInfo*<br/>
Vzdálenější ukazatel na strukturu dat pro konkrétní dodavatele. Definice této struktury (je-li zadán) je nad rámec specifikace rozhraní Windows Sockets.

> [!NOTE]
>  V knihovně MFC `WSADATA` struktura je vrácený `AfxSocketInit` funkci, kterou voláte v vaše `InitInstance` funkce. Můžete načíst strukturu a ukládat ve svém programu, pokud je třeba použít informace z něj později.

## <a name="requirements"></a>Požadavky

**Záhlaví:** winsock2.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit)

