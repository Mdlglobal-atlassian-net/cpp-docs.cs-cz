---
title: Casyncsocket – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAsyncSocket
- AFXSOCK/CAsyncSocket
- AFXSOCK/CAsyncSocket::CAsyncSocket
- AFXSOCK/CAsyncSocket::Accept
- AFXSOCK/CAsyncSocket::AsyncSelect
- AFXSOCK/CAsyncSocket::Attach
- AFXSOCK/CAsyncSocket::Bind
- AFXSOCK/CAsyncSocket::Close
- AFXSOCK/CAsyncSocket::Connect
- AFXSOCK/CAsyncSocket::Create
- AFXSOCK/CAsyncSocket::Detach
- AFXSOCK/CAsyncSocket::FromHandle
- AFXSOCK/CAsyncSocket::GetLastError
- AFXSOCK/CAsyncSocket::GetPeerName
- AFXSOCK/CAsyncSocket::GetPeerNameEx
- AFXSOCK/CAsyncSocket::GetSockName
- AFXSOCK/CAsyncSocket::GetSockNameEx
- AFXSOCK/CAsyncSocket::GetSockOpt
- AFXSOCK/CAsyncSocket::IOCtl
- AFXSOCK/CAsyncSocket::Listen
- AFXSOCK/CAsyncSocket::Receive
- AFXSOCK/CAsyncSocket::ReceiveFrom
- AFXSOCK/CAsyncSocket::ReceiveFromEx
- AFXSOCK/CAsyncSocket::Send
- AFXSOCK/CAsyncSocket::SendTo
- AFXSOCK/CAsyncSocket::SendToEx
- AFXSOCK/CAsyncSocket::SetSockOpt
- AFXSOCK/CAsyncSocket::ShutDown
- AFXSOCK/CASyncSocket::Socket
- AFXSOCK/CAsyncSocket::OnAccept
- AFXSOCK/CAsyncSocket::OnClose
- AFXSOCK/CAsyncSocket::OnConnect
- AFXSOCK/CAsyncSocket::OnOutOfBandData
- AFXSOCK/CAsyncSocket::OnReceive
- AFXSOCK/CAsyncSocket::OnSend
- AFXSOCK/CAsyncSocket::m_hSocket
dev_langs:
- C++
helpviewer_keywords:
- CAsyncSocket [MFC], CAsyncSocket
- CAsyncSocket [MFC], Accept
- CAsyncSocket [MFC], AsyncSelect
- CAsyncSocket [MFC], Attach
- CAsyncSocket [MFC], Bind
- CAsyncSocket [MFC], Close
- CAsyncSocket [MFC], Connect
- CAsyncSocket [MFC], Create
- CAsyncSocket [MFC], Detach
- CAsyncSocket [MFC], FromHandle
- CAsyncSocket [MFC], GetLastError
- CAsyncSocket [MFC], GetPeerName
- CAsyncSocket [MFC], GetPeerNameEx
- CAsyncSocket [MFC], GetSockName
- CAsyncSocket [MFC], GetSockNameEx
- CAsyncSocket [MFC], GetSockOpt
- CAsyncSocket [MFC], IOCtl
- CAsyncSocket [MFC], Listen
- CAsyncSocket [MFC], Receive
- CAsyncSocket [MFC], ReceiveFrom
- CAsyncSocket [MFC], ReceiveFromEx
- CAsyncSocket [MFC], Send
- CAsyncSocket [MFC], SendTo
- CAsyncSocket [MFC], SendToEx
- CAsyncSocket [MFC], SetSockOpt
- CAsyncSocket [MFC], ShutDown
- CASyncSocket [MFC], Socket
- CAsyncSocket [MFC], OnAccept
- CAsyncSocket [MFC], OnClose
- CAsyncSocket [MFC], OnConnect
- CAsyncSocket [MFC], OnOutOfBandData
- CAsyncSocket [MFC], OnReceive
- CAsyncSocket [MFC], OnSend
- CAsyncSocket [MFC], m_hSocket
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ffd2a8969b4cd0edb5845310300e3b42148f816
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337613"
---
# <a name="casyncsocket-class"></a>Casyncsocket – třída
Představuje Windows Socket – koncový bod komunikace v síti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAsyncSocket : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|Vytvoří `CAsyncSocket` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAsyncSocket::Accept](#accept)|Přijímá soketu připojení.|  
|[CAsyncSocket::AsyncSelect](#asyncselect)|Oznamování událostí žádostí pro soket.|  
|[CAsyncSocket::Attach](#attach)|Připojí popisovač soketu `CAsyncSocket` objektu.|  
|[CAsyncSocket::Bind](#bind)|Přidruží místních adres soketu.|  
|[CAsyncSocket::Close](#close)|Zavře soketu.|  
|[CAsyncSocket::Connect](#connect)|Naváže připojení k soketu partnera.|  
|[CAsyncSocket::Create](#create)|Vytvoří soket.|  
|[CAsyncSocket::Detach](#detach)|Odpojí popisovač soketu z `CAsyncSocket` objektu.|  
|[CAsyncSocket::FromHandle](#fromhandle)|Vrací ukazatel `CAsyncSocket` objekt daný popisovač soketu.|  
|[CAsyncSocket::GetLastError](#getlasterror)|Získá stav chyby pro poslední operace, která selhala.|  
|[CAsyncSocket::GetPeerName](#getpeername)|Získá adresu partnera soketu, ke kterému je připojený soket.|  
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Získá adresu peer soketu, ke kterému je soketu připojené (popisovače adresy IPv6).|  
|[CAsyncSocket::GetSockName](#getsockname)|Získá místní název pro soket.|  
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Získá název místního soketu (popisovače adresy IPv6).|  
|[CAsyncSocket::GetSockOpt](#getsockopt)|Získá možnost soketu.|  
|[CAsyncSocket::IOCtl](#ioctl)|Určuje režim soketu.|  
|[CAsyncSocket::Listen](#listen)|Vytvoří pro naslouchání pro příchozí požadavky na připojení soketu.|  
|[CAsyncSocket::Receive](#receive)|Přijímá data ze soketu.|  
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Získá datagram a uloží zdrojovou adresu.|  
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Přijímá datagram a ukládá zdrojové adresy (popisovače adresy IPv6).|  
|[CAsyncSocket::Send](#send)|Odešle data do připojený soket.|  
|[CAsyncSocket::SendTo](#sendto)|Odesílá data na určité cíle.|  
|[CAsyncSocket::SendToEx](#sendtoex)|Odesílá data na určité cíle (popisovače adresy IPv6).|  
|[CAsyncSocket::SetSockOpt](#setsockopt)|Nastaví možnost soketu.|  
|[CAsyncSocket::ShutDown](#shutdown)|Zakáže `Send` a/nebo `Receive` volá na soketu.|  
|[CASyncSocket::Socket](#socket)|Přidělí popisovač soketu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAsyncSocket::OnAccept](#onaccept)|Naslouchání soketu, který může přijmout čekající žádosti o připojení pomocí volání upozorní `Accept`.|  
|[CAsyncSocket::OnClose](#onclose)|Upozorní, že soketu, který k němu připojili soketu byl uzavřen.|  
|[CAsyncSocket::OnConnect](#onconnect)|Oznámí připojování soketu, pokus o připojení je dokončena, ať už úspěšně nebo s chybou.|  
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Upozorní příjmu soketu, že je out-of-band data ke čtení na soketu, obvykle naléhavé zprávy.|  
|[CAsyncSocket::OnReceive](#onreceive)|Upozorní naslouchání soketu, že se data mají být načtena voláním `Receive`.|  
|[CAsyncSocket::OnSend](#onsend)|Upozorní soketu, kterou může odesílat data voláním `Send`.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAsyncSocket::operator =](#operator_eq)|Přiřadí novou hodnotu `CAsyncSocket` objektu.|  
|[CAsyncSocket::operator SOKETU](#operator_socket)|Tento operátor umožňuje načíst popisovač SOKETU `CAsyncSocket` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAsyncSocket::m_hSocket](#m_hsocket)|Označuje popisovač SOKETU připojených k tomuto `CAsyncSocket` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Třída `CAsyncSocket` zapouzdřuje funkce API Windows Socket, poskytují objektově orientované abstrakce pro programátory, kteří chtějí používat ve spojení s knihovnou MFC rozhraní Windows Sockets.  
  
 Tato třída vychází z předpokladu, že rozumíte síťové komunikace. Je zodpovědná za zpracování blokování, pořadí bajtů rozdíly a převodů mezi kódování Unicode a vícebajtových znaků nastavte řetězce (znakové sady MBCS). Pokud chcete pohodlnější rozhraní, které spravuje za vás tyto problémy, naleznete v tématu třídy [csocket –](../../mfc/reference/csocket-class.md).  
  
 Použití `CAsyncSocket` objektu, volání konstruktoru, zavolejte [vytvořit](#create) funkci, která vytvoří základní popisovač soketu (typ `SOCKET`), s výjimkou přijaté sockets. Pro volání soketu serveru [naslouchání](#listen) členská funkce a pro volání soketu klienta [připojit](#connect) členskou funkci. Serverového soketu by měly volat [přijmout](#accept) funkce při přijetí požadavku na připojení. Pomocí zbývajících `CAsyncSocket` funkce provádět komunikace mezi sokety. Po dokončení zrušení `CAsyncSocket` objekt by byl vytvořen na haldě, destruktor automaticky volá [Zavřít](#close) funkce. Datový typ SOCKET je popsaný v článku [rozhraní Windows Sockets: pozadí](../../mfc/windows-sockets-background.md).  
  
> [!NOTE]
>  Při použití soketů knihovny MFC v sekundárních vláken aplikace staticky propojené knihovny MFC, je nutné volat `AfxSocketInit` v každém vlákně, který používá sockets k inicializaci soketu knihovny. Ve výchozím nastavení `AfxSocketInit` je volána pouze v primárním vlákně.  
  
 Další informace najdete v tématu [rozhraní Windows Sockets: použití třídy CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) a souvisejících článcích., stejně jako [rozhraní Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 `CAsyncSocket`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxsock.h  
  
##  <a name="accept"></a>  CAsyncSocket::Accept  
 Voláním této členské funkce tak, aby přijímal připojení pro soket.  
  
```  
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,  
    SOCKADDR* lpSockAddr = NULL,  
    int* lpSockAddrLen = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *rConnectedSocket*  
 Odkaz identifikaci nových soketu, která je dostupná pro připojení.  
  
 *lpSockAddr*  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura, která bude přijímat adresy připojení soketu, jako známé v síti. Přesný formát *lpSockAddr* argument je určeno rodina adres vytvořen, když soket byl vytvořen. Pokud *lpSockAddr* a/nebo *lpSockAddrLen* rovnají na hodnotu NULL, je vrácena žádná informace o vzdálených adres přijetí soketu.  
  
 *lpSockAddrLen*  
 Ukazatel na délky na adresu v *lpSockAddr* v bajtech. *LpSockAddrLen* je výsledkem hodnota parametru: nejprve musí obsahovat množství místa, na které odkazuje *lpSockAddr*; při návratu bude obsahovat skutečná délka (v bajtech) adresu vrácenou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEFAULT *lpSockAddrLen* argument je příliš malý (menší než velikost [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura).  
  
- Probíhá WSAEINPROGRESS A, které blokují rozhraní Windows Sockets volat.  
  
- WSAEINVAL `Listen` nebyla vyvolanou před přijmout.  
  
- WSAEMFILE fronta je prázdná při vstupu tak, aby přijímal a nejsou k dispozici žádné popisovače.  
  
- Ne WSAENOBUFS vyrovnávací paměť je k dispozici.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
- WSAEOPNOTSUPP odkazované soketu se nejedná o typ, který podporuje službu připojení objektově orientovaný.  
  
- WSAEWOULDBLOCK soketu je označen jako neblokový a přijmout nejsou žádná připojení.  
  
### <a name="remarks"></a>Poznámky  
 Tato rutina extrahuje první připojení ve frontě čekajících připojení, vytvoří nové soketu se stejnými vlastnostmi jako tento soket a připojí ho k *rConnectedSocket*. Pokud nejsou žádné čekající připojení ve frontě, `Accept` vrátí hodnotu 0 a `GetLastError` vrátí chybu. Přijetí soketu ( *rConnectedSocket)* nelze použít tak, aby přijímal další připojení. Původní soketu zůstane otevřený a naslouchá.  
  
 Argument *lpSockAddr* je výsledek parametr, který se vyplní adresu připojování soketu, protože ví, komunikační vrstvu. `Accept` se používá s typy založené na připojení soketu, jako jsou SOCK_STREAM.  
  
##  <a name="asyncselect"></a>  CAsyncSocket::AsyncSelect  
 Voláním této členské funkce pro vyžádání oznámení události pro soket.  
  
```  
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>Parametry  
 *lEvent*  
 Bitová maska, který určuje kombinaci událostech sítě, ve kterých je chcete aplikaci.  
  
- FD_READ chcete dostávat oznámení o připravenosti pro čtení.  
  
- FD_WRITE chcete obdržení oznámení při data jsou k dispozici pro čtení.  
  
- FD_OOB chcete dostávat oznámení o zásilce out-of-band data.  
  
- FD_ACCEPT chcete dostávat oznámení příchozí připojení.  
  
- FD_CONNECT chcete dostávat oznámení o výsledcích připojení.  
  
- FD_CLOSE chcete obdržení oznámení při soketu bylo ukončeno partnerského uzlu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEINVAL označuje, že jedna ze zadaných parametrů byl neplatný.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží k určení, které funkce zpětného volání oznámení knihovny MFC bude volána pro soket. `AsyncSelect` automaticky nastaví tento soket neblokový režimu. Další informace najdete v článku [rozhraní Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="attach"></a>  CAsyncSocket::Attach  
 Voláním této členské funkce se připojit *hSocket* popisovače `CAsyncSocket` objektu.  
  
```  
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>Parametry  
 *hSocket*  
 Obsahuje popisovač soketu.  
  
 *lEvent*  
 Bitová maska, který určuje kombinaci událostech sítě, ve kterých je chcete aplikaci.  
  
- FD_READ chcete dostávat oznámení o připravenosti pro čtení.  
  
- FD_WRITE chcete obdržení oznámení při data jsou k dispozici pro čtení.  
  
- FD_OOB chcete dostávat oznámení o zásilce out-of-band data.  
  
- FD_ACCEPT chcete dostávat oznámení příchozí připojení.  
  
- FD_CONNECT chcete dostávat oznámení o výsledcích připojení.  
  
- FD_CLOSE chcete obdržení oznámení při soketu bylo ukončeno partnerského uzlu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač SOKETU je uložena v objektu [m_hSocket](#m_hsocket) datový člen.  
  
##  <a name="bind"></a>  CAsyncSocket::Bind  
 Voláním této členské funkce přidružit místních adres soketu.  
  
```  
BOOL Bind(
    UINT nSocketPort,  
    LPCTSTR lpszSocketAddress = NULL);

 
BOOL Bind (
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>Parametry  
 *nSocketPort*  
 Port, který identifikuje aplikaci soketu.  
  
 *lpszSocketAddress*  
 Síťová adresa tečkovaná číslo, například "128.56.22.8". Předání NULL řetězec pro tento parametr určuje `CAsyncSocket` instance naslouchat požadavkům klientů na všech síťových rozhraních.  
  
 *lpSockAddr*  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) strukturu, která obsahuje adresu, kterou chcete přiřadit tento soket.  
  
 *nSockAddrLen*  
 Délka adresy v *lpSockAddr* v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEADDRINUSE zadaná adresa je již používán. (Viz možnost soketu SO_REUSEADDR pod [SetSockOpt](#setsockopt).)  
  
- WSAEFAULT *nSockAddrLen* argument je příliš malý (menší než velikost [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura).  
  
- Probíhá WSAEINPROGRESS A, které blokují rozhraní Windows Sockets volat.  
  
- WSAEAFNOSUPPORT řady zadaná adresa není podporován tímto portem.  
  
- WSAEINVAL soketu je již vázán na adresu.  
  
- Není WSAENOBUFS dostatečně ukládá do vyrovnávací paměti k dispozici příliš mnoho připojení.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
### <a name="remarks"></a>Poznámky  
 Tato rutina se používá na nepřipojené datagram nebo soketu datového proudu před následné `Connect` nebo `Listen` volání. Předtím, než mohl přijímat žádosti o připojení, naslouchání serverového soketu musí vyberte číslo portu a nastavte ji známá rozhraní Windows Sockets voláním `Bind`. `Bind` vytvoří místní přidružení (číslo adresa/port hostitele) soketu přiřazením místní název nepojmenované soketu.  
  
##  <a name="casyncsocket"></a>  CAsyncSocket::CAsyncSocket  
 Vytvoří prázdný objekt.  
  
```  
CAsyncSocket();
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytvoření objektu, je nutné volat jeho `Create` datová struktura SOKETU vytvářejí a vážou adresy členské funkce. (Na straně serveru Windows Sockets komunikace, při naslouchání soketu vytvoří soket pro použití v `Accept` volání není volána `Create` pro tento soket.)  
  
##  <a name="close"></a>  CAsyncSocket::Close  
 Zavře soketu.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce uvolní popisovač soketu tak, aby další se na ni odkazují nezdaří s chybou WSAENOTSOCK. Pokud je to poslední odkaz na základní soketu, související informace pro vytváření názvů a dat ve frontě se zahodí. Volání destruktoru objekt soketu `Close` za vás.  
  
 Pro `CAsyncSocket`, ale ne pro `CSocket`, sémantika `Close` ovlivníte soketů možnostmi SO_LINGER a SO_DONTLINGER. Další informace najdete v tématu členskou funkci `GetSockOpt`.  
  
##  <a name="connect"></a>  CAsyncSocket::Connect  
 Voláním této členské funkce k navázání připojení nepřipojené datového proudu nebo datagram soketu.  
  
```  
BOOL Connect(
    LPCTSTR lpszHostAddress,  
    UINT nHostPort);

 
BOOL Connect(
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszHostAddress*  
 Síťová adresa soketu, ke kterému je připojený tento objekt: název počítače, jako je například "ftp.microsoft.com" nebo tečkovaná číslo, například "128.56.22.8".  
  
 *nHostPort*  
 Port, který identifikuje aplikaci soketu.  
  
 *lpSockAddr*  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) strukturu, která obsahuje adresu připojený soket.  
  
 *nSockAddrLen*  
 Délka adresy v *lpSockAddr* v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Pokud se to označuje kód chyby WSAEWOULDBLOCK a vaše aplikace používá overridable zpětná volání, vaše aplikace dostanou `OnConnect` zprávu po dokončení operace připojení. Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEADDRINUSE zadaná adresa je již používán.  
  
- Probíhá WSAEINPROGRESS A, které blokují rozhraní Windows Sockets volat.  
  
- WSAEADDRNOTAVAIL zadaná adresa není k dispozici z místního počítače.  
  
- Adresy WSAEAFNOSUPPORT zadané řady nejde v tomto soketu.  
  
- WSAECONNREFUSED pokus o připojení byl odmítnut.  
  
- Vyžaduje se WSAEDESTADDRREQ A cílovou adresu.  
  
- WSAEFAULT *nSockAddrLen* argumentu je nesprávný.  
  
- WSAEINVAL neplatná adresa hostitele.  
  
- WSAEISCONN soketu je již připojen.  
  
- WSAEMFILE žádné další popisovače souborů, které jsou k dispozici.  
  
- WSAENETUNREACH sítě není dosažitelná z tohoto hostitele v tuto chvíli.  
  
- Ne WSAENOBUFS vyrovnávací paměť je k dispozici. Soketu nelze připojit.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
- Bez navázání připojení vypršel časový limit WSAETIMEDOUT pokus o připojení.  
  
- WSAEWOULDBLOCK soketu je označen jako neblokový a připojení nelze dokončit okamžitě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud soketu není vázaný, jedinečné hodnoty jsou přiřazeny k přidružení místní systém a soketu je označen jako vázán. Všimněte si, že pokud do pole adresy název struktury se všemi nulovými hodnotami, `Connect` vrátí nulu. Chcete-li získat rozšířené informace o chybě, zavolejte `GetLastError` členskou funkci.  
  
 Pro sokety datového proudu (typ SOCK_STREAM) je zahájeno aktivní připojení k hostiteli cizí. Po úspěšném dokončení volání soketu je připraven k posílání a přijímání dat soketu.  
  
 Pro soket datagram (typ SOCK_DGRAM) je nastavena výchozí cíl, který se použije při následných `Send` a `Receive` volání.  
  
##  <a name="create"></a>  CAsyncSocket::Create  
 Volání `Create` členskou funkci po vytváření objekt soketu soketu Windows vytvořit a připojit ji.  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nSocketPort*  
 Dobře známý port pro použití s soketu, nebo 0, pokud chcete rozhraní Windows Sockets vyberte port.  
  
 *nSocketType*  
 SOCK_STREAM nebo SOCK_DGRAM.  
  
 *lEvent*  
 Bitová maska, který určuje kombinaci událostech sítě, ve kterých je chcete aplikaci.  
  
- FD_READ chcete dostávat oznámení o připravenosti pro čtení.  
  
- FD_WRITE chcete dostávat oznámení o připravenosti pro zápis.  
  
- FD_OOB chcete dostávat oznámení o zásilce out-of-band data.  
  
- FD_ACCEPT chcete dostávat oznámení příchozí připojení.  
  
- FD_CONNECT chcete dostávat oznámení o dokončení připojení.  
  
- FD_CLOSE chcete dostávat oznámení o uzavření soketu.  
  
 *lpszSockAddress*  
 Ukazatel na řetězec obsahující síťová adresa připojený soket tečkovaná číslo, například "128.56.22.8". Předání NULL řetězec pro tento parametr určuje `CAsyncSocket` instance naslouchat požadavkům klientů na všech síťových rozhraních.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEAFNOSUPPORT řady zadaná adresa není podporována.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- WSAEMFILE žádné další popisovače souborů, které jsou k dispozici.  
  
- Ne WSAENOBUFS vyrovnávací paměť je k dispozici. Nelze vytvořit soketu.  
  
- WSAEPROTONOSUPPORT zadaný port není podporován.  
  
- WSAEPROTOTYPE zadaný port je nesprávného typu pro tento soket.  
  
- WSAESOCKTNOSUPPORT určený typ soketu se nepodporuje v této rodině adres.  
  
### <a name="remarks"></a>Poznámky  
 `Create` volání [soketu](#socket) a v případě úspěchu se volá [svázat](#bind) soketu vytvořit vazbu na zadané adrese. Jsou podporovány následující typy soketu:  
  
- SOCK_STREAM poskytuje sekvencování, spolehlivá, plně duplexní, na základě připojení bajtové datové proudy. Používá protokol TCP (Transmission Control) pro rodinu adres sítě Internet.  
  
- Datagramy SOCK_DGRAM podporuje, které jsou pakety bez připojení, nespolehlivé pevné (obvykle malý) maximální délky. Protokolu UDP (User Datagram) používá pro rodinu adres sítě Internet.  
  
    > [!NOTE]
    >  `Accept` Členská funkce používá odkaz na nový, prázdný `CSocket` objektu jako svůj parametr. Je nutné vytvořit tento objekt před voláním `Accept`. Mějte na paměti, která pokud je tento objekt soketu se odesílá z oboru, ukončí připojení. Nevolejte `Create` pro tento nový objekt soketu.  
  
> [!IMPORTANT]
> `Create` je **není** bezpečné pro vlákna.  Pokud voláte ho v prostředí s víc vlákny kde ji mohou být volány současně v různých vláknech, je nutné k ochraně každé volání s mutex nebo jiných zámek synchronizace.  
  
 Další informace o streamu a datagram sokety, najdete v článcích [rozhraní Windows Sockets: pozadí](../../mfc/windows-sockets-background.md) a [rozhraní Windows Sockets: porty a adresy soketů](../../mfc/windows-sockets-ports-and-socket-addresses.md) a [rozhraní Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="detach"></a>  CAsyncSocket::Detach  
 Voláním této členské funkce se odpojit popisovač SOKETU v *m_hSocket* datový člen z `CAsyncSocket` objektu a nastavte *m_hSocket* na hodnotu NULL.  
  
```  
SOCKET Detach();
```  
  
##  <a name="fromhandle"></a>  CAsyncSocket::FromHandle  
 Vrací ukazatel `CAsyncSocket` objektu.  
  
```  
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>Parametry  
 *hSocket*  
 Obsahuje popisovač soketu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CAsyncSocket` objektu, nebo hodnota NULL, pokud neexistuje žádný `CAsyncSocket` objekt připojen k *hSocket*.  
  
### <a name="remarks"></a>Poznámky  
 Když je zadaný popisovač SOKETU, pokud `CAsyncSocket` objekt není připojen ke popisovač, členská funkce vrátí hodnotu NULL.  
  
##  <a name="getlasterror"></a>  CAsyncSocket::GetLastError  
 Voláním této členské funkce se získat stav chyby pro poslední operace, která selhala.  
  
```  
static int PASCAL GetLastError();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota označuje kód chyby rozhraní Windows Sockets API rutiny poslední provedené tímto vláknem.  
  
### <a name="remarks"></a>Poznámky  
 Pokud nevkládal členské funkce naznačuje, že došlo k chybě, `GetLastError` by měla být volána k načtení příslušné chybový kód. V popisech jednotliví členové funkce pro seznam o příslušné chybové kódy.  
  
 Další informace o chybových kódech naleznete v tématu [rozhraní Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="getpeername"></a>  CAsyncSocket::GetPeerName  
 Voláním této členské funkce k získání adresy peer soketu, ke kterému je připojený tento soket.  
  
```  
BOOL GetPeerName(
    CString& rPeerAddress,  
    UINT& rPeerPort);

 
BOOL GetPeerName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>Parametry  
 *rPeerAddress*  
 Odkaz `CString` objekt, který přijme tečkovaná číslo IP adresu.  
  
 *rPeerPort*  
 Odkaz na UINT, která ukládá port.  
  
 *lpSockAddr*  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura, která přijímá název partnera soketu.  
  
 *lpSockAddrLen*  
 Ukazatel na délky na adresu v *lpSockAddr* v bajtech. Při návratu *lpSockAddrLen* argument obsahuje skutečnou velikost *lpSockAddr* vrátil v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEFAULT *lpSockAddrLen* argument není dostatečně velký.  
  
- Probíhá WSAEINPROGRESS A, které blokují rozhraní Windows Sockets volat.  
  
- WSAENOTCONN soketu není připojený.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zpracovat adresy IPv6, použijte [CAsyncSocket::GetPeerNameEx](#getpeernameex).  
  
##  <a name="getpeernameex"></a>  CAsyncSocket::GetPeerNameEx  
 Voláním této členské funkce k získání adresy peer soketu, ke kterému je tento soket připojené (popisovače adresy IPv6).  
  
```  
BOOL GetPeerNameEx(
    CString& rPeerAddress,  
    UINT& rPeerPort);
```  
  
### <a name="parameters"></a>Parametry  
 *rPeerAddress*  
 Odkaz `CString` objekt, který přijme tečkovaná číslo IP adresu.  
  
 *rPeerPort*  
 Odkaz na UINT, která ukládá port.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEFAULT *lpSockAddrLen* argument není dostatečně velký.  
  
- Probíhá WSAEINPROGRESS A, které blokují rozhraní Windows Sockets volat.  
  
- WSAENOTCONN soketu není připojený.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je stejná jako [CAsyncSocket::GetPeerName](#getpeername) s tím rozdílem, že zpracovává IPv6 adres i starší protokoly.  
  
##  <a name="getsockname"></a>  CAsyncSocket::GetSockName  
 Voláním této členské funkce se získat místní název pro soket.  
  
```  
BOOL GetSockName(
    CString& rSocketAddress,  
    UINT& rSocketPort);

 
BOOL GetSockName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>Parametry  
 *rSocketAddress*  
 Odkaz `CString` objekt, který přijme tečkovaná číslo IP adresu.  
  
 *rSocketPort*  
 Odkaz na UINT, která ukládá port.  
  
 *lpSockAddr*  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura, která přijímá adres soketu.  
  
 *lpSockAddrLen*  
 Ukazatel na délky na adresu v *lpSockAddr* v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEFAULT *lpSockAddrLen* argument není dostatečně velký.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
- WSAEINVAL soketu ještě vytvořenou vazbu na adresu s `Bind`.  
  
### <a name="remarks"></a>Poznámky  
 Toto volání je zvlášť užitečné, když `Connect` provedl volání bez tím `Bind` první; toto volání obsahuje pouze prostředky, pomocí kterého můžete určit místní přidružení, která byla nastavena systém.  
  
 Chcete-li zpracovat adresy IPv6, použijte [CAsyncSocket::GetSockNameEx](#getsocknameex)  
  
##  <a name="getsocknameex"></a>  CAsyncSocket::GetSockNameEx  
 Voláním této členské funkce se získat název místního soketu (popisovače adresy IPv6).  
  
```  
BOOL GetSockNameEx(
    CString& rSocketAddress,  
    UINT& rSocketPort);
```  
  
### <a name="parameters"></a>Parametry  
 *rSocketAddress*  
 Odkaz `CString` objekt, který přijme tečkovaná číslo IP adresu.  
  
 *rSocketPort*  
 Odkaz na UINT, která ukládá port.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEFAULT *lpSockAddrLen* argument není dostatečně velký.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
- WSAEINVAL soketu ještě vytvořenou vazbu na adresu s `Bind`.  
  
### <a name="remarks"></a>Poznámky  
 Toto volání je stejný jako [CAsyncSocket::GetSockName](#getsockname) s tím rozdílem, že zpracovává IPv6 adres i starší protokoly.  
  
 Toto volání je zvlášť užitečné, když `Connect` provedl volání bez tím `Bind` první; toto volání obsahuje pouze prostředky, pomocí kterého můžete určit místní přidružení, která byla nastavena systém.  
  
##  <a name="getsockopt"></a>  CAsyncSocket::GetSockOpt  
 Voláním této členské funkce k načtení možnost soketu.  
  
```  
BOOL GetSockOpt(
    int nOptionName,  
    void* lpOptionValue,  
    int* lpOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>Parametry  
 *nOptionName*  
 Možnost soketu, pro který má být načtena hodnota.  
  
 *lpOptionValue*  
 Ukazatel do vyrovnávací paměti, ve kterém má být vráceno hodnota pro požadovanou možnost. Hodnota přidružená k vybrané možnosti se vrátí ve vyrovnávací paměti *lpOptionValue*. Celé číslo odkazované *lpOptionLen* by měl obsahovat původně velikosti této vyrovnávací paměti v bajtech; a na vrátit, bude nastavena na velikost vrácená hodnota. U SO_LINGER, bude velikost `LINGER` struktury; u všech jiných možností bude velikost BOOL nebo **int**, v závislosti na možnosti. Zobrazit seznam možností a jejich velikosti v oddílu Poznámky.  
  
 *lpOptionLen*  
 Ukazatel na velikost *lpOptionValue* vyrovnávací paměti v bajtech.  
  
 *nLevel*  
 Úroveň, ve kterém je možnost definována; jsou pouze podporované úrovně SOL_SOCKET a IPPROTO_TCP.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Pokud možnost nastavila nikdy s `SetSockOpt`, pak `GetSockOpt` vrátí výchozí hodnotu pro možnost. Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEFAULT *lpOptionLen* argument byl neplatný.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- WSAENOPROTOOPT možnost je neznámý nebo nepodporovaný. Zejména SO_BROADCAST nepodporuje sockets SOCK_STREAM při SO_ACCEPTCONN SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER a SO_OOBINLINE nejsou podporovány na soketech typu SOCK_DGRAM typu.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
### <a name="remarks"></a>Poznámky  
 `GetSockOpt` načte aktuální hodnota pro možnost soketu přidružené k soketu libovolného typu, v libovolném stavu a uloží výsledek v *lpOptionValue*. Možnosti vliv na operace soketu, jako je například směrování paketů, přenos dat out-of-band a tak dále.  
  
 Tyto možnosti jsou podporovány pro `GetSockOpt`. Typ určuje typ dat řešený *lpOptionValue*. Možnost TCP_NODELAY používá úroveň IPPROTO_TCP; všechny ostatní možnosti použít úroveň SOL_SOCKET.  
  
|Hodnota|Typ|Význam|  
|-----------|----------|-------------|  
|SO_ACCEPTCONN|BOOL|Naslouchání soketu.|  
|SO_BROADCAST|BOOL|Soket je nakonfigurovaný pro předávání zpráv všesměrového vysílání.|  
|SO_DEBUG|BOOL|Je povoleno ladění.|  
|SO_DONTLINGER|BOOL|Při hodnotě true se SO_LINGER možnost je zakázaná.|  
|SO_DONTROUTE|BOOL|Směrování je zakázaná.|  
|SO_ERROR|**int**|Načíst stav chyby a zrušte zaškrtnutí.|  
|SO_KEEPALIVE|BOOL|Udržování otevřených připojení jsou odesílány.|  
|SO_LINGER|`struct LINGER`|Vrátí aktuální linger – možnosti.|  
|SO_OOBINLINE|BOOL|Se přijetí dat Out-of-band v normální datového proudu.|  
|ASYNCHRONNÍ|int|Velikost vyrovnávací paměti pro obdrží.|  
|SO_REUSEADDR|BOOL|Soket mohou být vázány na adresu, která se už používá.|  
|SO_SNDBUF|**int**|Velikost vyrovnávací paměti pro odešle.|  
|SO_TYPE|**int**|Typ soketu (například SOCK_STREAM).|  
|TCP_NODELAY|BOOL|Zakáže algoritmus Nagle pro odeslání, sloučení.|  
  
 Možnosti Berkeley Software Distribution (BSD) není podporována pro `GetSockOpt` jsou:  
  
|Hodnota|Typ|Význam|  
|-----------|----------|-------------|  
|SO_RCVLOWAT|**int**|Zobrazit dolní meze.|  
|SO_RCVTIMEO|**int**|Zobrazit časový limit.|  
|SO_SNDLOWAT|**int**|Odešlete dolní meze.|  
|SO_SNDTIMEO|**int**|Časový limit odeslání.|  
|IP_OPTIONS||Získejte možnosti v hlavičce protokolu IP.|  
|TCP_MAXSEG|**int**|Získejte TCP maximální velikost segmentu.|  
  
 Volání `GetSockOpt` pomocí nepodporované možnosti způsobí chybu WSAENOPROTOOPT vráceného z `GetLastError`.  
  
##  <a name="ioctl"></a>  CAsyncSocket::IOCtl  
 Voláním této členské funkce pro řízení režimu soketu.  
  
```  
BOOL IOCtl(
    long lCommand,  
    DWORD* lpArgument);
```  
  
### <a name="parameters"></a>Parametry  
 *lCommand*  
 Příkaz provést na soketu.  
  
 *lpArgument*  
 Ukazatel na parametr *lCommand*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEINVAL *lCommand* není platný příkaz, nebo *lpArgument* není přijatelný parametr pro *lCommand*, nebo příkaz neplatí pro typ zadaný soketu .  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
### <a name="remarks"></a>Poznámky  
 Tato rutina lze použít v jakékoli soketu v libovolném státu. Používá se k získání nebo načíst parametry přidružené k soketu, nezávisle na podsystému protokol a komunikace. Podporovány jsou následující příkazy:  
  
- FIONBIO povolit nebo zakázat režim neblokový na soketu. *LpArgument* parametr odkazuje na `DWORD`, což je nenulová, pokud neblokový režimu se má povolit a nula, pokud je zakázán. Pokud `AsyncSelect` byl vydán pro soket, pak žádný pokus o použití `IOCtl` nastavit soketu se zpět a režim blokování nezdaří s WSAEINVAL. K nastavení soketu zpátky do režimu blokování a WSAEINVAL chybě zabránit, musíte aplikace nejdřív zakázat `AsyncSelect` voláním `AsyncSelect` s *lEvent* parametr rovná 0, zavolejte `IOCtl`.  
  
- FIONREAD určit maximální počet bajtů, které může číst s jedním `Receive` volání z tento soket. *LpArgument* parametr odkazuje na `DWORD` ve kterém `IOCtl` výsledek je uložen. Pokud tento soket má typ SOCK_STREAM, FIONREAD vrátí celkové množství dat, který lze číst v jediném `Receive`; to je obvykle stejný jako celkové množství dat ve frontě na soketu. Pokud tento soket má typ SOCK_DGRAM, vrátí FIONREAD že velikost datagramu první ve frontě na soketu.  
  
- SIOCATMARK určit, zda byla načtena všechna data out-of-band. To platí pouze pro soket typu SOCK_STREAM, který byl nakonfigurován pro vložené příjem jakýchkoli dat out-of-band (SO_OOBINLINE). Pokud žádná data out-of-band čeká ke čtení, operace vrátí nenulovou hodnotu. V opačném případě vrátí 0 a dalších `Receive` nebo `ReceiveFrom` provedla soketu se načtou některé nebo všechny předchozí "znak" data, aplikace by měla pomocí SIOCATMARK operace můžete zjistit, zda všechna data zůstanou. Pokud není žádná normální data před "naléhavých" dat (out-of-band), nebudou přijímány v pořadí. (Všimněte si, že `Receive` nebo `ReceiveFrom` se nikdy Nekombinujte out-of-band běžné, že data ve stejném volání.) *LpArgument* parametr odkazuje na `DWORD` ve kterém `IOCtl` výsledek je uložen.  
  
 Tato funkce je podmnožinou `ioctl()` v Berkeley sokety. Především neexistuje žádný příkaz, který je ekvivalentní FIOASYNC, zatímco SIOCATMARK je pouze úrovni soketu příkaz, který není podporovaný.  
  
##  <a name="listen"></a>  CAsyncSocket::Listen  
 Voláním této členské funkce k naslouchání pro příchozí požadavky na připojení.  
  
```  
BOOL Listen(int nConnectionBacklog = 5);
```  
  
### <a name="parameters"></a>Parametry  
 *nConnectionBacklog*  
 Maximální délka, ke kterému můžou růst frontě čekajících připojení. Platný rozsah je od 1 do 5.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- Byl proveden WSAEADDRINUSE pokus o naslouchání adresy používá.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- WSAEINVAL nebyl dosud navázaný soketu `Bind` nebo je již připojen.  
  
- WSAEISCONN soketu je již připojen.  
  
- WSAEMFILE žádné další popisovače souborů, které jsou k dispozici.  
  
- Ne WSAENOBUFS vyrovnávací paměť je k dispozici.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
- WSAEOPNOTSUPP odkazované soketu není typu, který podporuje `Listen` operace.  
  
### <a name="remarks"></a>Poznámky  
 Tak, aby přijímal připojení soketu se nejprve vytvoří s `Create`, nevyřízených položek pro příchozí připojení není zadán s `Listen`, a pak se přijímají připojení s `Accept`. `Listen` platí jenom pro soketů, které podporují připojení, tedy typu SOCK_STREAM. Tento soket přejde do režimu "pasivní" kde příchozí připojení jsou potvrzeny a ve frontě čekajících přijetí procesem.  
  
 Tato funkce je obvykle používána servery (nebo jakékoli aplikace, která chce, aby se tak, aby přijímal připojení), který může mít více než jeden požadavek na připojení v čase: dorazí požadavek na připojení s frontou úplné klienta se zobrazí chyba s uvedením WSAECONNREFUSED.  
  
 `Listen` pokusí se i nadále fungovat racionální, když nejsou dostupné žádné porty (popisovače). Dokud vyprázdnění fronty bude akceptovat připojení. Pokud porty budou k dispozici, novější volání `Listen` nebo `Accept` doplnění fronty do aktuální nebo nejnovější "nevyřízených položek," Pokud je to možné a obnovit naslouchání pro příchozí připojení.  
  
##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket  
 Obsahuje popisovač SOKETU pro soket zapouzdřené situace `CAsyncSocket` objektu.  
  
```  
SOCKET m_hSocket;  
```  
  
##  <a name="onaccept"></a>  CAsyncSocket::OnAccept  
 Volá se rozhraním, aby se oznámilo soketu naslouchání, ve kterém lze přijmout čekající žádosti o připojení pomocí volání [přijmout](#accept) členskou funkci.  
  
```  
virtual void OnAccept(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 *nErrorCode*  
 Poslední chyba pro soket. Následující kódy chyb platí pro `OnAccept` členské funkce:  
  
- **0** funkce byla úspěšně provedena.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [rozhraní Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="onclose"></a>  CAsyncSocket::OnClose  
 Volá se rozhraním, aby tento soket upozornit, že jeho procesem se zavře připojený soket.  
  
```  
virtual void OnClose(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 *nErrorCode*  
 Poslední chyba pro soket. Následující kódy chyb platí pro `OnClose` členské funkce:  
  
- **0** funkce byla úspěšně provedena.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAECONNRESET připojení bylo resetováno na vzdálené straně.  
  
- WSAECONNABORTED připojení byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [rozhraní Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="onconnect"></a>  CAsyncSocket::OnConnect  
 Volá se rozhraním upozornit tento připojování soketu, že dokončení jeho pokus o připojení, ať už úspěšně nebo s chybou.  
  
```  
virtual void OnConnect(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 *nErrorCode*  
 Poslední chyba pro soket. Následující kódy chyb platí pro `OnConnect` členské funkce:  
  
- **0** funkce byla úspěšně provedena.  
  
- WSAEADDRINUSE zadaná adresa je již používán.  
  
- WSAEADDRNOTAVAIL zadaná adresa není k dispozici z místního počítače.  
  
- Adresy WSAEAFNOSUPPORT zadané řady nejde v tomto soketu.  
  
- WSAECONNREFUSED pokus o připojení vynuceně byla odmítnuta.  
  
- Vyžaduje se WSAEDESTADDRREQ A cílovou adresu.  
  
- WSAEFAULT *lpSockAddrLen* argumentu je nesprávný.  
  
- WSAEINVAL soketu je již vázán na adresu.  
  
- WSAEISCONN soketu je již připojen.  
  
- WSAEMFILE žádné další popisovače souborů, které jsou k dispozici.  
  
- WSAENETUNREACH sítě není dosažitelná z tohoto hostitele v tuto chvíli.  
  
- Ne WSAENOBUFS vyrovnávací paměť je k dispozici. Soketu nelze připojit.  
  
- WSAENOTCONN soketu není připojený.  
  
- WSAENOTSOCK popisovač je soubor, nikoli soketu.  
  
- Bez navázání připojení vypršel časový limit WSAETIMEDOUT pokus o připojení.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  V [csocket –](../../mfc/reference/csocket-class.md), `OnConnect` nebude nikdy volána funkce oznámení. Pro připojení, jednoduše zavoláte `Connect`, která vrátí po dokončení připojení (ať už úspěšně nebo s chybou). Zpracování oznámení připojení je podrobnosti implementace MFC.  
  
 Další informace najdete v tématu [rozhraní Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]  
  
##  <a name="onoutofbanddata"></a>  CAsyncSocket::OnOutOfBandData  
 Volá se rozhraním k oznámení příjmu soketu, který posílá soket má out-of-band data k odeslání.  
  
```  
virtual void OnOutOfBandData(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 *nErrorCode*  
 Poslední chyba pro soket. Následující kódy chyb platí pro `OnOutOfBandData` členské funkce:  
  
- **0** funkce byla úspěšně provedena.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
### <a name="remarks"></a>Poznámky  
 Out-of-band data jsou logicky nezávislý kanál, který je spojen s každou dvojici připojených sockets typu SOCK_STREAM. Kanálu se obvykle používá k odesílání naléhavá data.  
  
 MFC podporuje out-of-band data, ale uživatelé třídy `CAsyncSocket` se nedoporučuje používat. Vytvořit druhý soket pro předávání těchto dat je jednodušší způsob. Další informace o datech out-of-band najdete v tématu [rozhraní Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="onreceive"></a>  CAsyncSocket::OnReceive  
 Volá se rozhraním, aby upozornit tento soket, že se data ve vyrovnávací paměti, která může být načten voláním `Receive` členskou funkci.  
  
```  
virtual void OnReceive(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 *nErrorCode*  
 Poslední chyba pro soket. Následující kódy chyb platí pro `OnReceive` členské funkce:  
  
- **0** funkce byla úspěšně provedena.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [rozhraní Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]  
  
##  <a name="onsend"></a>  CAsyncSocket::OnSend  
 Volá se rozhraním, aby upozornění soketu, že ji teď odeslat data volání `Send` členskou funkci.  
  
```  
virtual void OnSend(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 *nErrorCode*  
 Poslední chyba pro soket. Následující kódy chyb platí pro `OnSend` členské funkce:  
  
- **0** funkce byla úspěšně provedena.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [rozhraní Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]  
  
##  <a name="operator_eq"></a>  CAsyncSocket::operator =  
 Přiřadí novou hodnotu `CAsyncSocket` objektu.  
  
```  
void operator=(const CAsyncSocket& rSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *rSrc*  
 Odkaz na existující `CAsyncSocket` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této funkce Kopírovat existující `CAsyncSocket` objektu na jiný `CAsyncSocket` objektu.  
  
##  <a name="operator_socket"></a>  CAsyncSocket::operator SOKETU  
 Tento operátor umožňuje načíst popisovač SOKETU `CAsyncSocket` objektu.  
  
```  
operator SOCKET() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu popisovač SOKETU objekt. v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač můžete použít pro volání rozhraní API Windows přímo.  
  
##  <a name="receive"></a>  CAsyncSocket::Receive  
 Voláním této členské funkce pro příjem dat ze soketu.  
  
```  
virtual int Receive(
    void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpBuf*  
 Vyrovnávací paměť pro příchozí data.  
  
 *nBufLen*  
 Délka *lpBuf* v bajtech.  
  
 *nFlags*  
 Určuje způsob, ve kterém se provádí volání. Sémantika této funkce jsou určeny soketů možnostmi a *nFlags* parametru. Je vytvořen kombinací libovolné z následujících hodnot C++ **nebo** operátor:  
  
- Zobrazení náhledu MSG_PEEK příchozí data. Data zkopírována do vyrovnávací paměti, ale neodebere se z do vstupní fronty.  
  
- Data out-of-band MSG_OOB procesu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenastane žádná chyba `Receive` vrátí počet bajtů přijatých. Pokud připojení bylo ukončeno, vrátí hodnotu 0. V opačném případě vrátí hodnotu SOCKET_ERROR a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAENOTCONN soketu není připojený.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
- WSAEOPNOTSUPP MSG_OOB byla zadána, ale není typu SOCK_STREAM soketu.  
  
- Byla ukončena WSAESHUTDOWN soketu; není možné volat `Receive` na soketu po `ShutDown` zavolání s *nHow* nastavena na hodnotu 0 nebo 2.  
  
- WSAEWOULDBLOCK soketu je označen jako neblokový a `Receive` by blokovaly operace.  
  
- WSAEMSGSIZE datagram byl příliš velký a nevejde se do zadané vyrovnávací paměti a byla zkrácena.  
  
- WSAEINVAL nebyl dosud navázaný soketu `Bind`.  
  
- WSAECONNABORTED virtuální okruh byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
- WSAECONNRESET virtuální okruh bylo resetováno na vzdálené straně.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se používá pro připojení datového proudu nebo sokety datagramu a slouží k načtení příchozí data.  
  
 Co nejvíce informací, jako je aktuálně k dispozici až do velikosti vyrovnávací paměť předaná sockets typu SOCK_STREAM, bude vrácena. Pokud soketu byl nakonfigurován pro příjem vložených dat out-of-band (možnost soketu SO_OOBINLINE) a out-of-band data nejsou, vrátí se pouze data out-of-band. Aplikace můžete použít `IOCtlSIOCATMARK` možnost nebo [OnOutOfBandData](#onoutofbanddata) k určení, zda všechna data více out-of-band zůstává pro čtení.  
  
 Sokety datagramu data extrahují z první datagram zařazených do fronty až do velikosti vyrovnávací paměť předaná. Pokud je větší než vyrovnávací paměť předaná datagram, vyrovnávací paměti, naplní se první část datagram, nadbytečná data řadit do dojde ke ztrátě, a `Receive` vrátí hodnotu SOCKET_ERROR s kódem chyby nastavena na WSAEMSGSIZE. Pokud žádné příchozí data jsou k dispozici na soket, vrátí se hodnota SOCKET_ERROR s kódem chyby nastavena na WSAEWOULDBLOCK. [Události OnReceive](#onreceive) funkce zpětného volání lze použít k určení, kdy další data přibývají.  
  
 Pokud soket má typ SOCK_STREAM a na vzdálené straně je řádně ukončit připojení, `Receive` se ihned dokončí s 0 bajtů. Pokud bylo připojení resetováno, `Receive` se nezdaří s chybou WSAECONNRESET.  
  
 `Receive` by měla být volána pouze jednou pro každý čas [CAsyncSocket::OnReceive](#onreceive) je volána.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAsyncSocket::OnReceive](#onreceive).  
  
##  <a name="receivefrom"></a>  CAsyncSocket::ReceiveFrom  
 Voláním této členské funkce přijímají datagram a ukládání adresy zdroje v [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktury nebo *rSocketAddress*.  
  
```  
int ReceiveFrom(
    void* lpBuf,  
    int nBufLen,  
    CString& rSocketAddress,  
    UINT& rSocketPort,  
    int nFlags = 0);

 
int ReceiveFrom(
    void* lpBuf,  
    int nBufLen,  
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpBuf*  
 Vyrovnávací paměť pro příchozí data.  
  
 *nBufLen*  
 Délka *lpBuf* v bajtech.  
  
 *rSocketAddress*  
 Odkaz `CString` objekt, který přijme tečkovaná číslo IP adresu.  
  
 *rSocketPort*  
 Odkaz na UINT, která ukládá port.  
  
 *lpSockAddr*  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura, která obsahuje po návratu zdrojovou adresu.  
  
 *lpSockAddrLen*  
 Ukazatel na délku zdrojová adresa v *lpSockAddr* v bajtech.  
  
 *nFlags*  
 Určuje způsob, ve kterém se provádí volání. Sémantika této funkce jsou určeny soketů možnostmi a *nFlags* parametru. Je vytvořen kombinací libovolné z následujících hodnot C++ **nebo** operátor:  
  
- Zobrazení náhledu MSG_PEEK příchozí data. Data zkopírována do vyrovnávací paměti, ale neodebere se z do vstupní fronty.  
  
- Data out-of-band MSG_OOB procesu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenastane žádná chyba `ReceiveFrom` vrátí počet bajtů přijatých. Pokud připojení bylo ukončeno, vrátí hodnotu 0. V opačném případě vrátí hodnotu SOCKET_ERROR a určitý kód chyby může být načten voláním `GetLastError`. Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEFAULT *lpSockAddrLen* argument byl neplatný: *lpSockAddr* vyrovnávací paměť je příliš malá, aby odpovídala adresy partnerského uzlu.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- WSAEINVAL nebyl dosud navázaný soketu `Bind`.  
  
- WSAENOTCONN soketu není připojen (pouze SOCK_STREAM).  
  
- Není WSAENOTSOCK popisovač soketu.  
  
- WSAEOPNOTSUPP MSG_OOB byla zadána, ale není typu SOCK_STREAM soketu.  
  
- Byla ukončena WSAESHUTDOWN soketu; není možné volat `ReceiveFrom` na soketu po `ShutDown` zavolání s *nHow* nastavena na hodnotu 0 nebo 2.  
  
- WSAEWOULDBLOCK soketu je označen jako neblokový a `ReceiveFrom` by blokovaly operace.  
  
- WSAEMSGSIZE datagram byl příliš velký a nevejde se do zadané vyrovnávací paměti a byla zkrácena.  
  
- WSAECONNABORTED virtuální okruh byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
- WSAECONNRESET virtuální okruh bylo resetováno na vzdálené straně.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží ke čtení povoluje data (může být připojený) soket a zachytit adresu, ze kterého se data odesílají.  
  
 Chcete-li zpracovat adresy IPv6, použijte [CAsyncSocket::ReceiveFromEx](#receivefromex).  
  
 Co nejvíce informací, jako je aktuálně k dispozici až do velikosti vyrovnávací paměť předaná sockets typu SOCK_STREAM, bude vrácena. Pokud soketu byl nakonfigurován pro příjem vložených dat out-of-band (možnost soketu SO_OOBINLINE) a out-of-band data nejsou, vrátí se pouze data out-of-band. Aplikace můžete použít `IOCtlSIOCATMARK` možnost nebo `OnOutOfBandData` k určení, zda všechna data více out-of-band zůstává pro čtení. *LpSockAddr* a *lpSockAddrLen* parametry budou ignorovány SOCK_STREAM soketů.  
  
 Sokety datagramu data extrahují z první datagram zařazených do fronty až do velikosti vyrovnávací paměť předaná. Pokud je větší než vyrovnávací paměť předaná datagram, vyrovnávací paměti, naplní se první část zprávy, nadbytečná data řadit do dojde ke ztrátě, a `ReceiveFrom` vrátí hodnotu SOCKET_ERROR s kódem chyby nastavena na WSAEMSGSIZE.  
  
 Pokud *lpSockAddr* nenulové a soket má typ SOCK_DGRAM, síťovou adresu soketu, která odesílá data zkopírována do odpovídajícího [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktury. Hodnota odkazované *lpSockAddrLen* je inicializován na velikost struktury a je upraveno vrátit se k určení skutečné velikosti adresu v ní uloženy. Pokud žádné příchozí data jsou k dispozici na soket, `ReceiveFrom` volání čeká dat není-li soketu neblokový. V takovém případě vrátí hodnotu SOCKET_ERROR s kódem chyby nastavena na WSAEWOULDBLOCK. `OnReceive` Zpětného volání lze použít k určení, kdy další data přibývají.  
  
 Pokud soket má typ SOCK_STREAM a na vzdálené straně je řádně ukončit připojení, `ReceiveFrom` se ihned dokončí s 0 bajtů.  
  
##  <a name="receivefromex"></a>  CAsyncSocket::ReceiveFromEx  
 Voláním této členské funkce přijímají datagram a ukládání adresy zdroje v [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktury nebo *rSocketAddress* (zpracovává adresy IPv6).  
  
```  
int ReceiveFromEx(
    void* lpBuf,  
    int nBufLen,  
    CString& rSocketAddress,  
    UINT& rSocketPort,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpBuf*  
 Vyrovnávací paměť pro příchozí data.  
  
 *nBufLen*  
 Délka *lpBuf* v bajtech.  
  
 *rSocketAddress*  
 Odkaz `CString` objekt, který přijme tečkovaná číslo IP adresu.  
  
 *rSocketPort*  
 Odkaz na UINT, která ukládá port.  
  
 *nFlags*  
 Určuje způsob, ve kterém se provádí volání. Sémantika této funkce jsou určeny soketů možnostmi a *nFlags* parametru. Je vytvořen kombinací libovolné z následujících hodnot C++ **nebo** operátor:  
  
- Zobrazení náhledu MSG_PEEK příchozí data. Data zkopírována do vyrovnávací paměti, ale neodebere se z do vstupní fronty.  
  
- Data out-of-band MSG_OOB procesu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenastane žádná chyba `ReceiveFromEx` vrátí počet bajtů přijatých. Pokud připojení bylo ukončeno, vrátí hodnotu 0. V opačném případě vrátí hodnotu SOCKET_ERROR a určitý kód chyby může být načten voláním `GetLastError`. Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEFAULT *lpSockAddrLen* argument byl neplatný: *lpSockAddr* vyrovnávací paměť je příliš malá, aby odpovídala adresy partnerského uzlu.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- WSAEINVAL nebyl dosud navázaný soketu `Bind`.  
  
- WSAENOTCONN soketu není připojen (pouze SOCK_STREAM).  
  
- Není WSAENOTSOCK popisovač soketu.  
  
- WSAEOPNOTSUPP MSG_OOB byla zadána, ale není typu SOCK_STREAM soketu.  
  
- Byla ukončena WSAESHUTDOWN soketu; není možné volat `ReceiveFromEx` na soketu po `ShutDown` zavolání s *nHow* nastavena na hodnotu 0 nebo 2.  
  
- WSAEWOULDBLOCK soketu je označen jako neblokový a `ReceiveFromEx` by blokovaly operace.  
  
- WSAEMSGSIZE datagram byl příliš velký a nevejde se do zadané vyrovnávací paměti a byla zkrácena.  
  
- WSAECONNABORTED virtuální okruh byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
- WSAECONNRESET virtuální okruh bylo resetováno na vzdálené straně.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží ke čtení povoluje data (může být připojený) soket a zachytit adresu, ze kterého se data odesílají.  
  
 Tato funkce je stejná jako [CAsyncSocket::ReceiveFrom](#receivefrom) s tím rozdílem, že zpracovává IPv6 adres i starší protokoly.  
  
 Co nejvíce informací, jako je aktuálně k dispozici až do velikosti vyrovnávací paměť předaná sockets typu SOCK_STREAM, bude vrácena. Pokud soketu byl nakonfigurován pro příjem vložených dat out-of-band (možnost soketu SO_OOBINLINE) a out-of-band data nejsou, vrátí se pouze data out-of-band. Aplikace můžete použít `IOCtlSIOCATMARK` možnost nebo `OnOutOfBandData` k určení, zda všechna data více out-of-band zůstává pro čtení. *LpSockAddr* a *lpSockAddrLen* parametry budou ignorovány SOCK_STREAM soketů.  
  
 Sokety datagramu data extrahují z první datagram zařazených do fronty až do velikosti vyrovnávací paměť předaná. Pokud je větší než vyrovnávací paměť předaná datagram, vyrovnávací paměti, naplní se první část zprávy, nadbytečná data řadit do dojde ke ztrátě, a `ReceiveFromEx` vrátí hodnotu SOCKET_ERROR s kódem chyby nastavena na WSAEMSGSIZE.  
  
 Pokud *lpSockAddr* nenulové a soket má typ SOCK_DGRAM, síťovou adresu soketu, která odesílá data zkopírována do odpovídajícího [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktury. Hodnota odkazované *lpSockAddrLen* je inicializován na velikost struktury a je upraveno vrátit se k určení skutečné velikosti adresu v ní uloženy. Pokud žádné příchozí data jsou k dispozici na soket, `ReceiveFromEx` volání čeká dat není-li soketu neblokový. V takovém případě vrátí hodnotu SOCKET_ERROR s kódem chyby nastavena na WSAEWOULDBLOCK. `OnReceive` Zpětného volání lze použít k určení, kdy další data přibývají.  
  
 Pokud soket má typ SOCK_STREAM a na vzdálené straně je řádně ukončit připojení, `ReceiveFromEx` se ihned dokončí s 0 bajtů.  
  
##  <a name="send"></a>  CAsyncSocket::Send  
 Voláním této členské funkce k odesílání dat na připojený soket.  
  
```  
virtual int Send(
    const void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpBuf*  
 Vyrovnávací paměť obsahující data předávají.  
  
 *nBufLen*  
 Délka dat v *lpBuf* v bajtech.  
  
 *nFlags*  
 Určuje způsob, ve kterém se provádí volání. Sémantika této funkce jsou určeny soketů možnostmi a *nFlags* parametru. Je vytvořen kombinací libovolné z následujících hodnot C++ **nebo** operátor:  
  
- MSG_DONTROUTE Určuje, že data by neměly být v souladu s směrování. Windows Sockets dodavatele můžete rozhodnout Ignorovat tento příznak.  
  
- Odeslat MSG_OOB out-of-band dat (pouze SOCK_STREAM).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenastane žádná chyba `Send` vrátí celkový počet znaků, které jsou odeslány. (Všimněte si, že to může být menší než počet indikován *nBufLen*.) V opačném případě vrátí hodnotu SOCKET_ERROR a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEACCES požadovaná adresa je adresa všesměrového vysílání, ale odpovídající příznak nebyla nastavena.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- WSAEFAULT *lpBuf* argument není platný součástí adresního prostoru uživatele.  
  
- WSAENETRESET připojení musí resetovat, protože implementace rozhraní Windows Sockets ho vyřadit.  
  
- Implementace Windows Sockets WSAENOBUFS sestavy zablokování vyrovnávací paměti.  
  
- WSAENOTCONN soketu není připojený.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
- WSAEOPNOTSUPP MSG_OOB byla zadána, ale není typu SOCK_STREAM soketu.  
  
- Byla ukončena WSAESHUTDOWN soketu; není možné volat `Send` na soketu po `ShutDown` zavolání s *nHow* nastavena na 1 nebo 2.  
  
- WSAEWOULDBLOCK soketu je označen jako neblokový a by blokovaly požadovanou operaci.  
  
- WSAEMSGSIZE soket má typ SOCK_DGRAM a datagram je větší než maximální podporovaná implementací rozhraní Windows Sockets.  
  
- WSAEINVAL nebyl dosud navázaný soketu `Bind`.  
  
- WSAECONNABORTED virtuální okruh byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
- WSAECONNRESET virtuální okruh bylo resetováno na vzdálené straně.  
  
### <a name="remarks"></a>Poznámky  
 `Send` slouží k zápisu odchozí data na připojených datový proud nebo sokety datagramu. Pro sokety datagramu, musí věnovat pozornost nechcete být delší než maximální velikost paketu IP základní podsítí, které je dán `iMaxUdpDg` prvek [wsadata –](../../mfc/reference/wsadata-structure.md) vrácené struktury `AfxSocketInit`. Pokud jsou data příliš dlouhý předávání atomicky na základním protokolu, WSAEMSGSIZE se vrátila prostřednictvím `GetLastError`, a přenášena žádná data.  
  
 Všimněte si, že pro datagram soketu úspěšné dokončení `Send` neznamená, že data byla úspěšně doručit.  
  
 Na `CAsyncSocket` objekty typu SOCK_STREAM počet zapsaných bajtů může být v rozmezí 1 a požadovaná délka, v závislosti na dostupnosti vyrovnávací paměti na místní i cizí hostitelích.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAsyncSocket::OnSend](#onsend).  
  
##  <a name="sendto"></a>  CAsyncSocket::SendTo  
 Voláním této členské funkce k odesílání dat na určité cíle.  
  
```  
int SendTo(
    const void* lpBuf,  
    int nBufLen,  
    UINT nHostPort,  
    LPCTSTR lpszHostAddress = NULL,  
    int nFlags = 0);

 
int SendTo(
    const void* lpBuf,  
    int nBufLen,  
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpBuf*  
 Vyrovnávací paměť obsahující data předávají.  
  
 *nBufLen*  
 Délka dat v *lpBuf* v bajtech.  
  
 *nHostPort*  
 Port, který identifikuje aplikaci soketu.  
  
 *lpszHostAddress*  
 Síťová adresa soketu, ke kterému je připojený tento objekt: název počítače, jako je například "ftp.microsoft.com" nebo tečkovaná číslo, například "128.56.22.8".  
  
 *nFlags*  
 Určuje způsob, ve kterém se provádí volání. Sémantika této funkce jsou určeny soketů možnostmi a *nFlags* parametru. Je vytvořen kombinací libovolné z následujících hodnot C++ **nebo** operátor:  
  
- MSG_DONTROUTE Určuje, že data by neměly být v souladu s směrování. Windows Sockets dodavatele můžete rozhodnout Ignorovat tento příznak.  
  
- Odeslat MSG_OOB out-of-band dat (pouze SOCK_STREAM).  
  
 *lpSockAddr*  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) strukturu, která obsahuje adresu cílové soketu.  
  
 *nSockAddrLen*  
 Délka adresy v *lpSockAddr* v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenastane žádná chyba `SendTo` vrátí celkový počet znaků, které jsou odeslány. (Všimněte si, že to může být menší než počet indikován *nBufLen*.) V opačném případě vrátí hodnotu SOCKET_ERROR a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEACCES požadovaná adresa je adresa všesměrového vysílání, ale odpovídající příznak nebyla nastavena.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- WSAEFAULT *lpBuf* nebo *lpSockAddr* parametry, které nejsou součástí adresního prostoru uživatele nebo *lpSockAddr* argument je příliš malý (menší než velikost [Sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura).  
  
- WSAEINVAL název hostitele je neplatný.  
  
- WSAENETRESET připojení musí resetovat, protože implementace rozhraní Windows Sockets ho vyřadit.  
  
- Implementace Windows Sockets WSAENOBUFS sestavy zablokování vyrovnávací paměti.  
  
- WSAENOTCONN soketu není připojen (pouze SOCK_STREAM).  
  
- Není WSAENOTSOCK popisovač soketu.  
  
- WSAEOPNOTSUPP MSG_OOB byla zadána, ale není typu SOCK_STREAM soketu.  
  
- Byla ukončena WSAESHUTDOWN soketu; není možné volat `SendTo` na soketu po `ShutDown` zavolání s *nHow* nastavena na 1 nebo 2.  
  
- WSAEWOULDBLOCK soketu je označen jako neblokový a by blokovaly požadovanou operaci.  
  
- WSAEMSGSIZE soket má typ SOCK_DGRAM a datagram je větší než maximální podporovaná implementací rozhraní Windows Sockets.  
  
- WSAECONNABORTED virtuální okruh byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
- WSAECONNRESET virtuální okruh bylo resetováno na vzdálené straně.  
  
- WSAEADDRNOTAVAIL zadaná adresa není k dispozici z místního počítače.  
  
- Adresy WSAEAFNOSUPPORT zadané řady nejde v tomto soketu.  
  
- Vyžaduje se WSAEDESTADDRREQ A cílovou adresu.  
  
- WSAENETUNREACH sítě není dosažitelná z tohoto hostitele v tuto chvíli.  
  
### <a name="remarks"></a>Poznámky  
 `SendTo` se používá pro sokety datagramu nebo datového proudu a slouží k zápisu odchozích dat pro soket. Pro sokety datagramu, musí věnovat pozornost nechcete být delší než maximální velikost paketu IP základní podsítí, které je dán `iMaxUdpDg` prvek [wsadata –](../../mfc/reference/wsadata-structure.md) struktura vyplňuje [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit). Pokud jsou data příliš dlouhý předávání atomicky na základním protokolu, chyba je vrácena WSAEMSGSIZE a přenášena žádná data.  
  
 Všimněte si, že úspěšné dokončení `SendTo` neznamená, že data byla úspěšně doručit.  
  
 `SendTo` se používá pouze pro soket SOCK_DGRAM k odesílání datagram na konkrétní soket identifikován *lpSockAddr* parametru.  
  
 Odeslat vysílání (na SOCK_DGRAM pouze), adresu v *lpSockAddr* parametr by měl vytvořený pomocí speciální IP adresy INADDR_BROADCAST (definované v souboru hlaviček rozhraní Windows Sockets rozhraní WINSOCK. H) společně s použitím čísla portu určené. Nebo, pokud *lpszHostAddress* parametr hodnotu NULL, soketu je nakonfigurovaný pro všesměrové vysílání. Je obecně není vhodné pro vysílání datagram překročení velikosti, jakou může dojít k fragmentaci, což naznačuje, že datovou část datagram (s výjimkou záhlaví) by neměl být delší než 512 bajtů.  
  
 Chcete-li zpracovat adresy IPv6, použijte [CAsyncSocket::SendToEx](#sendtoex).  
  
##  <a name="sendtoex"></a>  CAsyncSocket::SendToEx  
 Voláním této členské funkce k odesílání dat na určité cíle (popisovače adresy IPv6).  
  
```  
int SendToEx(
    const void* lpBuf,  
    int nBufLen,  
    UINT nHostPort,  
    LPCTSTR lpszHostAddress = NULL,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpBuf*  
 Vyrovnávací paměť obsahující data předávají.  
  
 *nBufLen*  
 Délka dat v *lpBuf* v bajtech.  
  
 *nHostPort*  
 Port, který identifikuje aplikaci soketu.  
  
 *lpszHostAddress*  
 Síťová adresa soketu, ke kterému je připojený tento objekt: název počítače, jako je například "ftp.microsoft.com" nebo tečkovaná číslo, například "128.56.22.8".  
  
 *nFlags*  
 Určuje způsob, ve kterém se provádí volání. Sémantika této funkce jsou určeny soketů možnostmi a *nFlags* parametru. Je vytvořen kombinací libovolné z následujících hodnot C++ **nebo** operátor:  
  
- MSG_DONTROUTE Určuje, že data by neměly být v souladu s směrování. Windows Sockets dodavatele můžete rozhodnout Ignorovat tento příznak.  
  
- Odeslat MSG_OOB out-of-band dat (pouze SOCK_STREAM).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenastane žádná chyba `SendToEx` vrátí celkový počet znaků, které jsou odeslány. (Všimněte si, že to může být menší než počet indikován *nBufLen*.) V opačném případě vrátí hodnotu SOCKET_ERROR a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEACCES požadovaná adresa je adresa všesměrového vysílání, ale odpovídající příznak nebyla nastavena.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- WSAEFAULT *lpBuf* nebo *lpSockAddr* parametry, které nejsou součástí adresního prostoru uživatele nebo *lpSockAddr* argument je příliš malý (menší než velikost [Sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura).  
  
- WSAEINVAL název hostitele je neplatný.  
  
- WSAENETRESET připojení musí resetovat, protože implementace rozhraní Windows Sockets ho vyřadit.  
  
- Implementace Windows Sockets WSAENOBUFS sestavy zablokování vyrovnávací paměti.  
  
- WSAENOTCONN soketu není připojen (pouze SOCK_STREAM).  
  
- Není WSAENOTSOCK popisovač soketu.  
  
- WSAEOPNOTSUPP MSG_OOB byla zadána, ale není typu SOCK_STREAM soketu.  
  
- Byla ukončena WSAESHUTDOWN soketu; není možné volat `SendToEx` na soketu po `ShutDown` zavolání s *nHow* nastavena na 1 nebo 2.  
  
- WSAEWOULDBLOCK soketu je označen jako neblokový a by blokovaly požadovanou operaci.  
  
- WSAEMSGSIZE soket má typ SOCK_DGRAM a datagram je větší než maximální podporovaná implementací rozhraní Windows Sockets.  
  
- WSAECONNABORTED virtuální okruh byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
- WSAECONNRESET virtuální okruh bylo resetováno na vzdálené straně.  
  
- WSAEADDRNOTAVAIL zadaná adresa není k dispozici z místního počítače.  
  
- Adresy WSAEAFNOSUPPORT zadané řady nejde v tomto soketu.  
  
- Vyžaduje se WSAEDESTADDRREQ A cílovou adresu.  
  
- WSAENETUNREACH sítě není dosažitelná z tohoto hostitele v tuto chvíli.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je stejný jako [CAsyncSocket::SendTo](#sendto) s tím rozdílem, že zpracovává IPv6 adres i starší protokoly.  
  
 `SendToEx` se používá pro sokety datagramu nebo datového proudu a slouží k zápisu odchozích dat pro soket. Pro sokety datagramu, musí věnovat pozornost nechcete být delší než maximální velikost paketu IP základní podsítí, které je dán `iMaxUdpDg` prvek [wsadata –](../../mfc/reference/wsadata-structure.md) struktura vyplňuje [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit). Pokud jsou data příliš dlouhý předávání atomicky na základním protokolu, chyba je vrácena WSAEMSGSIZE a přenášena žádná data.  
  
 Všimněte si, že úspěšné dokončení `SendToEx` neznamená, že data byla úspěšně doručit.  
  
 `SendToEx` se používá pouze pro soket SOCK_DGRAM k odesílání datagram na konkrétní soket identifikován *lpSockAddr* parametru.  
  
 Odeslat vysílání (na SOCK_DGRAM pouze), adresu v *lpSockAddr* parametr by měl vytvořený pomocí speciální IP adresy INADDR_BROADCAST (definované v souboru hlaviček rozhraní Windows Sockets rozhraní WINSOCK. H) společně s použitím čísla portu určené. Nebo, pokud *lpszHostAddress* parametr hodnotu NULL, soketu je nakonfigurovaný pro všesměrové vysílání. Je obecně není vhodné pro vysílání datagram překročení velikosti, jakou může dojít k fragmentaci, což naznačuje, že datovou část datagram (s výjimkou záhlaví) by neměl být delší než 512 bajtů.  
  
##  <a name="setsockopt"></a>  CAsyncSocket::SetSockOpt  
 Voláním této členské funkce, chcete-li nastavit možnost soketu.  
  
```  
BOOL SetSockOpt(
    int nOptionName,  
    const void* lpOptionValue,  
    int nOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>Parametry  
 *nOptionName*  
 Možnost soketu, pro který má být nastavena hodnotu.  
  
 *lpOptionValue*  
 Ukazatel do vyrovnávací paměti, ve které je zadána hodnota pro požadovanou možnost.  
  
 *nOptionLen*  
 Velikost *lpOptionValue* vyrovnávací paměti v bajtech.  
  
 *nLevel*  
 Úroveň, ve kterém je možnost definována; jsou pouze podporované úrovně SOL_SOCKET a IPPROTO_TCP.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEFAULT *lpOptionValue* není platnou součástí adresního prostoru procesu.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- WSAEINVAL *nLevel* není platný, nebo informace v *lpOptionValue* není platný.  
  
- Pokud je nastavena SO_KEEPALIVE WSAENETRESET připojení vypršel.  
  
- WSAENOPROTOOPT možnost je neznámý nebo nepodporovaný. Zejména SO_BROADCAST nepodporuje sockets SOCK_STREAM při SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER a SO_OOBINLINE nejsou podporovány na soketech typu SOCK_DGRAM typu.  
  
- Pokud je nastavena SO_KEEPALIVE byla obnovena WSAENOTCONN připojení.  
  
- Není WSAENOTSOCK popisovač soketu.  
  
### <a name="remarks"></a>Poznámky  
 `SetSockOpt` Nastaví aktuální hodnotu pro možnost soketu přidružené k soketu libovolného typu, v libovolném státu. I když možnosti může existovat více úrovní protokolu, tato specifikace definuje pouze možnosti, které existují na úrovni nejvyšší "soket". Možnosti vliv na operace soketu, například zda urychlené přijetí dat v normální datový proud, zda lze odesílat na soketu zprávy všesměrového vysílání a tak dále.  
  
 Existují dva typy soketu: logická možnosti, které povolí nebo zakáže funkci nebo chování a možnosti, které vyžadují celočíselnou hodnotou nebo strukturu. Logická možnost Povolit *lpOptionValue* odkazuje na nenulovou hodnotu celého čísla. Chcete-li tuto možnost zakažte *lpOptionValue* odkazuje na celé číslo rovna hodnotě nula. *nOptionLen* by měl být roven `sizeof(BOOL)` logická možnosti. Další možnosti *lpOptionValue* odkazuje na celé číslo nebo struktura, která obsahuje požadovanou hodnotu pro možnost a *nOptionLen* je délka celé číslo nebo struktury.  
  
 SO_LINGER řídí akce provedená v případě unsent dat je ve frontě na soket a `Close` funkce je volána zavřete soketu.  
  
 Ve výchozím nastavení, nemůže být vázaný soketu (naleznete v tématu [svázat](#bind)) na místní adresu, která se už používá. V některých případech ale může být žádoucí "opakovaně používat" adresu tímto způsobem. Vzhledem k tomu, že všechna připojení je jedinečně identifikovaný kombinací místních a vzdálených adres, neexistuje žádný problém s s dvěma sokety vázán na stejnou místní adresou jako vzdálené adresy se liší.  
  
 Implementace rozhraní Windows Sockets informovat, který `Bind` volání na soket nesmí zakázané, protože požadovaná adresa je již používán jinou soketu, aplikace by měl nastavit možnost soketu SO_REUSEADDR soketu před vydáním `Bind` volání. Všimněte si, že je možnost interpretován pouze v době `Bind` volání: je proto zbytečné (ale neškodné) nastavení možnosti pro soket, která nemá být vázaný na existující adresu, a nebo obnovení nastavení možnost po `Bind` má volání žádný vliv na to nebo jiných soketu.  
  
 Může aplikace vyžadovat, aby implementace rozhraní Windows Sockets povolit použití "zachování" paketů na připojení protokolu TCP (Transmission Control) když zapnete možnost soketu SO_KEEPALIVE. Implementace rozhraní Windows Sockets nemusí podporovat používání udržování otevřených připojení: Pokud ano, přesně sémantiku jsou specifický pro implementaci, ale by měl odpovídat část 4.2.3.6 RFC 1122: "požadavky na internetoví hostitelé – komunikačními vrstvami." Ztracené připojení jako výsledek z "udržování otevřených připojení" vrácený kód chyby WSAENETRESET je pro všechna volání probíhá v soketu a následných volání selže s WSAENOTCONN.  
  
 Možnost TCP_NODELAY zakáže Nagle algoritmus. Nagle algoritmus se používá k omezení počtu malé paketů odesílaných hostitel nepotvrzených odeslat data do vyrovnávací paměti dokud reklamy paket, který je možné odeslat. Však pro některé aplikace pro tento algoritmus může bránit ve výkonu a TCP_NODELAY je možné ho vypnout. Uživatelé vytvářející obsah aplikace by neměl TCP_NODELAY nastavit, pokud to uděláte tak se odůvodněné a požadované, protože nastavení TCP_NODELAY může mít významný negativní dopad na výkon sítě. Je jediná TCP_NODELAY nepodporuje možnost soketu, která používá úroveň IPPROTO_TCP; všechny ostatní možnosti použít úroveň SOL_SOCKET.  
  
 Některé implementace rozhraní Windows Sockets dodání výstupní informace o ladění při nastavení možnosti SO_DEBUG aplikací.  
  
 Tyto možnosti jsou podporovány pro `SetSockOpt`. Typ určuje typ dat řešený *lpOptionValue*.  
  
|Hodnota|Typ|Význam|  
|-----------|----------|-------------|  
|SO_BROADCAST|BOOL|Povolte přenos zpráv všesměrového vysílání v soketu.|  
|SO_DEBUG|BOOL|Záznam informací o ladění.|  
|SO_DONTLINGER|BOOL|Nedošlo k blokování `Close` čekání unsent dat k odeslání. Nastavení této možnosti je ekvivalentní nastavení SO_LINGER s `l_onoff` nastaven na hodnotu nula.|  
|SO_DONTROUTE|BOOL|Není směrování: odeslat přímo do rozhraní.|  
|SO_KEEPALIVE|BOOL|Odešlete udržování otevřených připojení.|  
|SO_LINGER|`struct LINGER`|Linger – `Close` Pokud unsent data jsou k dispozici.|  
|SO_OOBINLINE|BOOL|Příjem dat out-of-band v normální datového proudu.|  
|ASYNCHRONNÍ|**int**|Zadejte velikost vyrovnávací paměti pro obdrží.|  
|SO_REUSEADDR|BOOL|Povolte soketu bylo vázané na adresu, která se už používá. (Viz [svázat](#bind).)|  
|SO_SNDBUF|**int**|Zadejte velikost vyrovnávací paměti pro odesílání.|  
|TCP_NODELAY|BOOL|Zakáže algoritmus Nagle pro odeslání, sloučení.|  
  
 Možnosti Berkeley Software Distribution (BSD) není podporována pro `SetSockOpt` jsou:  
  
|Hodnota|Typ|Význam|  
|-----------|----------|-------------|  
|SO_ACCEPTCONN|BOOL|Naslouchání soketu|  
|SO_ERROR|**int**|Získat stav chyby a zrušte zaškrtnutí.|  
|SO_RCVLOWAT|**int**|Zobrazit dolní meze.|  
|SO_RCVTIMEO|**int**|Zobrazit časový limit|  
|SO_SNDLOWAT|**int**|Odešlete dolní meze.|  
|SO_SNDTIMEO|**int**|Časový limit odeslání.|  
|SO_TYPE|**int**|Typ soketu.|  
|IP_OPTIONS||Nastavit možnosti pole v hlavičce protokolu IP.|  
  
##  <a name="shutdown"></a>  CAsyncSocket::ShutDown  
 Přijímá volání odešle tato členská funkce, zakážete, nebo na soketu.  
  
```  
BOOL ShutDown(int nHow = sends);
```  
  
### <a name="parameters"></a>Parametry  
 *nHow*  
 Příznak, který popisuje, jaké typy operací se už nebude mít, pomocí následujících hodnot výčtu:  
  
- **přijímá = 0**  
  
- **Odešle = 1**  
  
- **jak = 2**  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Tyto chyby se vztahují na tuto funkci člena:  
  
- Úspěšné A WSANOTINITIALISED [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) se musí vyskytovat před použitím tohoto rozhraní API.  
  
- Implementace Windows Sockets WSAENETDOWN zjistil, že se nepodařilo síťového podsystému.  
  
- WSAEINVAL *nHow* není platný.  
  
- Probíhá WSAEINPROGRESS A blokující operace rozhraní Windows Sockets.  
  
- WSAENOTCONN soketu není připojen (pouze SOCK_STREAM).  
  
- Není WSAENOTSOCK popisovač soketu.  
  
### <a name="remarks"></a>Poznámky  
 `ShutDown` se používá na všech typech sockets zakázat příjem nebo přenos. Pokud *nHow* je 0, obdrží dalších na soketu. bude zakázáno. Tato akce nemá vliv na nižších vrstvách protokolu.  
  
 V okně TCP pro protokol TCP (Transmission Control), se nezmění a budou příchozí data přijato (ale ne potvrzené) až do vyčerpání okna. Pro protokol UDP (User Datagram), příchozí datagramů přijaty a zařazeny do fronty. V žádném případě se vygeneruje chyba paketu ICMP. Pokud *nHow* 1, následné odešle nejsou povoleny. Pro TCP sockety se odešlou dokončení. Nastavení *nHow* 2 zakáže obou odešle a přijme, jak je popsáno výše.  
  
 Všimněte si, že `ShutDown` nemá zavřete soketu a prostředkům připojeným k soketu se není být uvolněna až do `Close` je volána. Aplikace, neměli byste tedy spoléhat na schopnost znovu použít soketu poté, co byl vypnut. Zejména implementaci rozhraní Windows Sockets nemusí podporovat používání `Connect` takové pro soket.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAsyncSocket::OnReceive](#onreceive).  
  
##  <a name="socket"></a>  CASyncSocket::Socket  
 Přidělí popisovač soketu.  
  
```  
BOOL Socket(
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    int nProtocolType = 0,  
    int nAddressFormat = PF_INET);
```  
  
### <a name="parameters"></a>Parametry  
 *nSocketType*  
 Určuje `SOCK_STREAM` nebo `SOCK_DGRAM`.  
  
 *lEvent*  
 Bitová maska, která určuje kombinaci událostech sítě, ve kterých aplikace interested.  
  
- `FD_READ`: Chcete dostávat oznámení o připravenosti pro čtení.  
  
- `FD_WRITE`: Chcete dostávat oznámení o připravenosti pro zápis.  
  
- `FD_OOB`: Chcete dostávat oznámení o zásilce out-of-band data.  
  
- `FD_ACCEPT`: Chcete dostávat oznámení příchozí připojení.  
  
- `FD_CONNECT`: Chcete dostávat oznámení o dokončení připojení.  
  
- `FD_CLOSE`: Chcete dostávat oznámení o uzavření soketu.  
  
 *nProtocolType*  
 Protokol pro použití s soket, který je specifický pro řady uvedena adresa.  
  
 *nAddressFormat*  
 Specifikace rodiny adres.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` v případě úspěchu, `FALSE` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidělí popisovač soketu. Nevolá [CAsyncSocket::Bind](#bind) svázat soketu k zadané adrese, proto musíte volat `Bind` později na připojení soketu k zadané adrese. Můžete použít [CAsyncSocket::SetSockOpt](#setsockopt) nastavit možnost soketu předtím, než je vázán.  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Csocket – třída](../../mfc/reference/csocket-class.md)   
 [CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
