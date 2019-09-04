---
title: CAsyncSocket – třída
ms.date: 09/03/2019
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
ms.openlocfilehash: 4e14052d400268a8852298113ba9b51fda713dc8
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273794"
---
# <a name="casyncsocket-class"></a>CAsyncSocket – třída

Představuje soket Windows – koncový bod síťové komunikace.

## <a name="syntax"></a>Syntaxe

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAsyncSocket:: CAsyncSocket](#casyncsocket)|`CAsyncSocket` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAsyncSocket:: Accept](#accept)|Přijme připojení na soketu.|
|[CAsyncSocket::AsyncSelect](#asyncselect)|Vyžádá oznámení události pro soket.|
|[CAsyncSocket:: Attach](#attach)|Připojí popisovač soketu k `CAsyncSocket` objektu.|
|[CAsyncSocket:: bind](#bind)|Přidruží k soketu místní adresu.|
|[CAsyncSocket::Close](#close)|Zavře soket.|
|[CAsyncSocket:: Connect](#connect)|Naváže připojení k soketu typu peer.|
|[CAsyncSocket::Create](#create)|Vytvoří soket.|
|[CAsyncSocket::Detach](#detach)|Odpojí popisovač soketu od `CAsyncSocket` objektu.|
|[CAsyncSocket:: FromHandle](#fromhandle)|Vrátí ukazatel na `CAsyncSocket` objekt s předaným popisovačem soketu.|
|[CAsyncSocket:: GetLastError](#getlasterror)|Získá chybový stav poslední operace, která se nezdařila.|
|[CAsyncSocket:: getpeere](#getpeername)|Získá adresu soketu partnerského zařízení, ke kterému je soket připojen.|
|[CAsyncSocket:: GetPeerNameEx](#getpeernameex)|Načte adresu soketu partnerského zařízení, ke kterému je soket připojen (zpracovává adresy IPv6).|
|[CAsyncSocket::GetSockName](#getsockname)|Získá místní název soketu.|
|[CAsyncSocket:: GetSockNameEx](#getsocknameex)|Získá místní název soketu (zpracovává adresy IPv6).|
|[CAsyncSocket::GetSockOpt](#getsockopt)|Načte možnost soketu.|
|[CAsyncSocket:: IOCtl](#ioctl)|Řídí režim soketu.|
|[CAsyncSocket::Listen](#listen)|Vytvoří soket, který bude naslouchat příchozím žádostem o připojení.|
|[CAsyncSocket:: Receive](#receive)|Přijímá data ze soketu.|
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Přijme datagram a uloží zdrojovou adresu.|
|[CAsyncSocket:: ReceiveFromEx](#receivefromex)|Přijímá datagram a ukládá zdrojovou adresu (zpracovává adresy IPv6).|
|[CAsyncSocket:: Send](#send)|Odesílá data do připojeného soketu.|
|[CAsyncSocket:: SendTo](#sendto)|Odesílá data do konkrétního cíle.|
|[CAsyncSocket:: SendToEx](#sendtoex)|Odesílá data do konkrétního cíle (zpracovává adresy IPv6).|
|[CAsyncSocket::SetSockOpt](#setsockopt)|Nastaví možnost soketu.|
|[CAsyncSocket::ShutDown](#shutdown)|Zakáže `Send` a/nebo `Receive` volá na soketu.|
|[CASyncSocket:: Socket](#socket)|Přidělí popisovač soketu.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CAsyncSocket:: Souhlasím](#onaccept)|Oznamuje naslouchajícímu soketu, že může přijmout žádosti o připojení nedokončené voláním `Accept`.|
|[CAsyncSocket::OnClose](#onclose)|Oznamuje soketu, že se ukončila zásuvka připojená k němu.|
|[CAsyncSocket:: Connect](#onconnect)|Oznamuje připojujícím se soketu, že je pokus o připojení dokončený, ať už úspěšně, nebo v omyl.|
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Upozorní přijímací soket na to, že data, která jsou mimo IP síť, se mají na soketu přečíst, zpravidla naléhavá zpráva.|
|[CAsyncSocket:: inreceive](#onreceive)|Oznamuje naslouchacímu soketu, že jsou k dispozici data, která `Receive`mají být načtena voláním.|
|[CAsyncSocket:: Send – odeslání](#onsend)|Upozorňuje na soket, který může odesílat data voláním `Send`.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CAsyncSocket:: operator =](#operator_eq)|Přiřadí novou hodnotu `CAsyncSocket` objektu.|
|[CAsyncSocket:: operator – SOKET](#operator_socket)|Tento operátor použijte k načtení popisovače `CAsyncSocket` soketu objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CAsyncSocket::m_hSocket](#m_hsocket)|Určuje popisovač soketu připojený k tomuto `CAsyncSocket` objektu.|

## <a name="remarks"></a>Poznámky

Třída `CAsyncSocket` zapouzdřuje rozhraní API služby Windows Socket Functions, které poskytuje abstrakci zaměřenou na objekt pro programátory, kteří chtějí používat rozhraní Windows Sockets ve spojení s knihovnou MFC.

Tato třída je založena na předpokladu, který rozumíte síťové komunikaci. Zodpovídáte za zpracování blokování, rozdílů v pořadí bytů a převodů mezi řetězci Unicode a vícebajtové znakové sady (MBCS). Pokud chcete pohodlnější rozhraní, které tyto problémy spravuje, přečtěte si téma třída [CSocket –](../../mfc/reference/csocket-class.md).

Chcete-li `CAsyncSocket` použít objekt, zavolejte svůj konstruktor a pak zavolejte funkci [Create](#create) k vytvoření základního soketového popisovače (typu `SOCKET`), s výjimkou povolených soketů. U soketu serveru zavolejte členskou funkci [Listen](#listen) a pro volání klientského objektu volejte členskou funkci [Connect](#connect) . Soket serveru by měl zavolat funkci [Accept](#accept) při přijetí žádosti o připojení. Pomocí zbývajících `CAsyncSocket` funkcí můžete provést komunikaci mezi sokety. Po dokončení zničí `CAsyncSocket` objekt, pokud byl vytvořen na haldě; destruktor automaticky zavolá funkci [Close](#close) . Datový typ soketu je popsaný v článku [Windows Sockets: Pozadí](../../mfc/windows-sockets-background.md).

> [!NOTE]
>  Při použití soketů MFC v sekundárních vláknech v staticky propojené aplikaci MFC je nutné zavolat `AfxSocketInit` do každého vlákna, které používá sokety k inicializaci knihoven soketu. Ve výchozím nastavení `AfxSocketInit` je volána pouze v primárním vlákně.

Další informace najdete v tématu [Windows Sockets: Použití třídy CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) a souvisejících článků, stejně jako [rozhraní Windows Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AfxSock. h

##  <a name="accept"></a>CAsyncSocket:: Accept

Voláním této členské funkce přijměte připojení na soketu.

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>Parametry

*rConnectedSocket*<br/>
Odkaz identifikující nový soket, který je k dispozici pro připojení.

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR –](/windows/win32/winsock/sockaddr-2) , která přijímá adresu připojovacího soketu, jak je známo v síti. Přesný formát argumentu *lpSockAddr* určuje rodina adres, která se vytvořila při vytvoření soketu. Pokud jsou *lpSockAddr* a/nebo *lpSockAddrLen* rovny hodnotě null, nebudou vráceny žádné informace o vzdálené adrese přijatého soketu.

*lpSockAddrLen*<br/>
Ukazatel na délku adresy v *lpSockAddr* v bajtech. *LpSockAddrLen* je parametr výsledku hodnoty: zpočátku by měl obsahovat množství místa, na které ukazuje *lpSockAddr*; Po návratu bude obsahovat skutečnou délku (v bajtech) vrácené adresy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEFAULT argument *lpSockAddrLen* je příliš malý (menší než velikost struktury [SOCKADDR –](/windows/win32/winsock/sockaddr-2) ).

- WSAEINPROGRESS, že probíhá zablokování volání Windows Sockets.

- WSAEINVAL `Listen` nebyl vyvolán před přijetím.

- WSAEMFILE fronta je po vstupu k přijetí prázdná a nejsou k dispozici žádné popisovače.

- WSAENOBUFS není k dispozici žádný prostor vyrovnávací paměti.

- WSAENOTSOCK popisovač není soket.

- WSAEOPNOTSUPP odkazovaný soket není typ, který podporuje službu orientovanou na připojení.

- WSAEWOULDBLOCK je soket označený jako neblokované a není k dispozici žádné připojení, které by bylo možné přijmout.

### <a name="remarks"></a>Poznámky

Tato rutina extrahuje první připojení ve frontě nedokončených připojení, vytvoří nový soket se stejnými vlastnostmi, jako je tento soket, a připojí ho k *rConnectedSocket*. Pokud fronta neobsahuje žádná nevyřízená připojení, `Accept` vrátí hodnotu nula a `GetLastError` vrátí chybu. Přijatý soket ( *rConnectedSocket)* nelze použít k přijetí dalších připojení. Původní soket zůstane otevřený a naslouchat.

Argument *lpSockAddr* je parametr výsledku, který se vyplní adresou připojovacího soketu, jak je známo v komunikační vrstvě. `Accept`se používá s typy soketů založenými na připojení, jako je SOCK_STREAM.

##  <a name="asyncselect"></a>CAsyncSocket:: AsyncSelect

Volejte tuto členskou funkci pro vyžádání oznámení události pro soket.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parametry

*lEvent*<br/>
Bitová maska, která určuje kombinaci událostí sítě, ve kterých se aplikace zajímá.

- FD_READ chtít dostávat oznámení o připravenosti na čtení.

- FD_WRITE chtít dostávat oznámení, když budou data čitelná k dispozici.

- FD_OOB chtít dostávat oznámení o doručení dat mimo pásmo.

- FD_ACCEPT chtít dostávat oznámení o příchozích připojeních.

- FD_CONNECT chtít dostávat oznámení o výsledcích připojení.

- FD_CLOSE chtít dostávat oznámení, když je soket uzavřený partnerským uzlem.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEINVAL značí, že jeden ze zadaných parametrů byl neplatný.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k určení, které funkce oznámení o zpětném volání knihovny MFC budou pro soketu volány. `AsyncSelect`automaticky nastaví tento soket na režim neblokování. Další informace najdete v článku [rozhraní Windows Sockets: Oznámení](../../mfc/windows-sockets-socket-notifications.md)soketu.

##  <a name="attach"></a>CAsyncSocket:: Attach

Chcete-li připojit popisovač *hSocket* k `CAsyncSocket` objektu, zavolejte tuto členskou funkci.

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Obsahuje popisovač pro soket.

*lEvent*<br/>
Bitová maska, která určuje kombinaci událostí sítě, ve kterých se aplikace zajímá.

- FD_READ chtít dostávat oznámení o připravenosti na čtení.

- FD_WRITE chtít dostávat oznámení, když budou data čitelná k dispozici.

- FD_OOB chtít dostávat oznámení o doručení dat mimo pásmo.

- FD_ACCEPT chtít dostávat oznámení o příchozích připojeních.

- FD_CONNECT chtít dostávat oznámení o výsledcích připojení.

- FD_CLOSE chtít dostávat oznámení, když je soket uzavřený partnerským uzlem.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná.

### <a name="remarks"></a>Poznámky

Popisovač SOKETu je uložený v datovém členu [m_hSocket](#m_hsocket) objektu.

##  <a name="bind"></a>CAsyncSocket:: bind

Tuto členskou funkci volejte pro přidružení místní adresy ke soketu.

```
BOOL Bind(
    UINT nSocketPort,
    LPCTSTR lpszSocketAddress = NULL);

BOOL Bind (
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Port identifikující aplikaci soketu.

*lpszSocketAddress*<br/>
Síťová adresa, tečkovaná číslo, například "128.56.22.8". Předání řetězce s hodnotou null pro tento parametr znamená `CAsyncSocket` , že instance má naslouchat aktivitě klienta na všech síťových rozhraních.

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR –](/windows/win32/winsock/sockaddr-2) , která obsahuje adresu, která se má přiřadit k tomuto soketu.

*nSockAddrLen*<br/>
Délka adresy v *lpSockAddr* v bajtech

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Následující seznam obsahuje několik chyb, které mohou být vráceny. Úplný seznam najdete v tématu [kódy chyb Windows Sockets](/windows/win32/winsock/windows-sockets-error-codes-2).

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEADDRINUSE zadaná adresa se už používá. (Viz možnost soketu SO_REUSEADDR v části [setsockopt](#setsockopt).)

- WSAEFAULT argument *nSockAddrLen* je příliš malý (menší než velikost struktury [SOCKADDR –](/windows/win32/winsock/sockaddr-2) ).

- WSAEINPROGRESS, že probíhá zablokování volání Windows Sockets.

- WSAEAFNOSUPPORT zadaná rodina adres není tímto portem podporována.

- WSAEINVAL soket již je svázán s adresou.

- WSAENOBUFS není k dispozici dostatek vyrovnávací paměti, příliš mnoho připojení.

- WSAENOTSOCK popisovač není soket.

### <a name="remarks"></a>Poznámky

Tato rutina se používá na nepřipojeném datagramu nebo soketu datového `Connect` proudu `Listen` před dalším voláním nebo voláními. Předtím, než může přijímat žádosti o připojení, musí soket naslouchajícího serveru vybrat číslo portu a volat ho pro Windows Sockets voláním `Bind`. `Bind`Vytvoří místní přidružení (adresu hostitele/číslo portu) soketu přiřazením místního názvu k nenázvovému soketu.

##  <a name="casyncsocket"></a>CAsyncSocket:: CAsyncSocket

Vytvoří prázdný objekt soketu.

```
CAsyncSocket();
```

### <a name="remarks"></a>Poznámky

Po sestavení objektu je nutné zavolat jeho `Create` členskou funkci pro vytvoření datové struktury soketu a vytvořit vazby její adresy. (Na straně serveru komunikace rozhraní Windows Sockets, když naslouchající soket vytvoří soket pro použití ve `Accept` volání, nebudete volat `Create` tento soket.)

##  <a name="close"></a>CAsyncSocket:: Close

Zavře soket.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Tato funkce uvolní popisovač soketu, takže další odkazy na něj selžou s chybou WSAENOTSOCK. Pokud se jedná o poslední odkaz na základní soket, budou přidružené informace o pojmenování a data ve frontě zahozena. Destruktor objektu soketu pro vás `Close` zavolá.

Pro `CAsyncSocket`, ale ne pro `CSocket` `Close` , sémantika je ovlivněna možnostmi soketu SO_LINGER a SO_DONTLINGER. Další informace naleznete v tématu členská `GetSockOpt`funkce.

##  <a name="connect"></a>CAsyncSocket:: Connect

Zavolejte tuto členskou funkci, aby se navázalo připojení k nepřipojenému datovému proudu nebo soketu datagramu.

```
BOOL Connect(
    LPCTSTR lpszHostAddress,
    UINT nHostPort);

BOOL Connect(
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>Parametry

*lpszHostAddress*<br/>
Síťová adresa soketu, ke kterému je tento objekt připojen: název počítače, například "ftp.microsoft.com" nebo číslo s tečkami, například "128.56.22.8".

*nHostPort*<br/>
Port identifikující aplikaci soketu.

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR –](/windows/win32/winsock/sockaddr-2) , která obsahuje adresu připojeného soketu.

*nSockAddrLen*<br/>
Délka adresy v *lpSockAddr* v bajtech

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Pokud to znamená chybový kód WSAEWOULDBLOCK a vaše aplikace používá přepisovatelný zpětná volání, vaše aplikace po dokončení operace připojení obdrží `OnConnect` zprávu. Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEADDRINUSE zadaná adresa se už používá.

- WSAEINPROGRESS, že probíhá zablokování volání Windows Sockets.

- WSAEADDRNOTAVAIL zadaná adresa není k dispozici z místního počítače.

- V rámci tohoto soketu nelze používat WSAEAFNOSUPPORT adresy v zadané rodině.

- WSAECONNREFUSED pokus o připojení byl odmítnut.

- WSAEDESTADDRREQ je vyžadována cílová adresa.

- WSAEFAULT argument *nSockAddrLen* není správný.

- WSAEINVAL neplatná adresa hostitele.

- WSAEISCONN soket je již připojen.

- WSAEMFILE nejsou k dispozici žádné další popisovače souboru.

- V tuto chvíli není možné WSAENETUNREACH síť kontaktovat z tohoto hostitele.

- WSAENOBUFS není k dispozici žádný prostor vyrovnávací paměti. Soket nelze připojit.

- WSAENOTSOCK popisovač není soket.

- WSAETIMEDOUT pokus o připojení vypršel bez navázání připojení.

- WSAEWOULDBLOCK je soket označený jako neblokované a připojení se nedá dokončit hned.

### <a name="remarks"></a>Poznámky

Pokud soket není vázaný, přiřadí se k místnímu přidružení jedinečné hodnoty a soket bude označen jako vázaný. Všimněte si, že pokud je pole Adresa struktury názvů všechny nula, `Connect` vrátí se nula. Chcete-li získat rozšířené informace o chybě `GetLastError` , zavolejte členskou funkci.

Pro sokety streamu (typ SOCK_STREAM) se iniciuje aktivní připojení k cizímu hostiteli. Po úspěšném dokončení volání soketu bude soket připraven k odeslání nebo přijetí dat.

U soketu datagramu (typ SOCK_DGRAM) je nastaven výchozí cíl, který bude použit při dalších `Send` voláních a `Receive` voláních.

##  <a name="create"></a>CAsyncSocket:: Create

Po vytvoření objektu soketu pro vytvoření soketu Windows a jeho připojení volejte členskoufunkci.`Create`

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Dobře známý port, který se má použít s soketem, nebo 0, pokud chcete, aby sokety Windows vybraly port.

*nSocketType*<br/>
SOCK_STREAM nebo SOCK_DGRAM.

*lEvent*<br/>
Bitová maska, která určuje kombinaci událostí sítě, ve kterých se aplikace zajímá.

- FD_READ chtít dostávat oznámení o připravenosti na čtení.

- FD_WRITE chtít dostávat oznámení o připravenosti na zápis.

- FD_OOB chtít dostávat oznámení o doručení dat mimo pásmo.

- FD_ACCEPT chtít dostávat oznámení o příchozích připojeních.

- FD_CONNECT chtít dostávat oznámení o dokončeném připojení.

- FD_CLOSE chtít dostávat oznámení o uzavření soketu.

*lpszSockAddress*<br/>
Ukazatel na řetězec, který obsahuje síťovou adresu připojeného soketu, číslo s tečkami, například "128.56.22.8". Předání řetězce s hodnotou null pro tento parametr znamená `CAsyncSocket` , že instance má naslouchat aktivitě klienta na všech síťových rozhraních.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEAFNOSUPPORT zadaná rodina adres není podporována.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAEMFILE nejsou k dispozici žádné další popisovače souboru.

- WSAENOBUFS není k dispozici žádný prostor vyrovnávací paměti. Soket nelze vytvořit.

- WSAEPROTONOSUPPORT zadaný port se nepodporuje.

- WSAEPROTOTYPE zadaný port je nesprávného typu pro tento soket.

- WSAESOCKTNOSUPPORT zadaný typ soketu není v této rodině adres podporován.

### <a name="remarks"></a>Poznámky

`Create`volání [a v případě úspěchu volá metodu](#socket) [BIND](#bind) , aby vytvořila vazby soketu se zadanou adresou. Podporovány jsou následující typy soketů:

- SOCK_STREAM poskytuje sekvenční, spolehlivé a plně duplexní datové proudy bajtů založené na připojení. Používá protokol TCP (Transmission Control Protocol) pro rodinu internetových adres.

- SOCK_DGRAM podporuje datagramy, které jsou bez připojení, což jsou nespolehlivé pakety s pevnou (obvykle malou) maximální délkou. Používá protokol UDP (User Datagram Protocol) pro rodinu internetových adres.

    > [!NOTE]
    >  Členská funkce přebírá odkaz na nový prázdný `CSocket` objekt jako svůj parametr. `Accept` Tento objekt je nutné vytvořit před voláním `Accept`. Mějte na paměti, že pokud se tento objekt soketu dostane mimo rozsah, připojení se zavře. Nevolejte `Create` pro tento nový objekt soketu.

> [!IMPORTANT]
> `Create`není bezpečná pro přístup **z více vláken** .  Pokud ji voláte v prostředí s více vlákny, kde by mohla být vyvolána současně různými vlákny, nezapomeňte chránit jednotlivá volání pomocí mutexu nebo jiného zámku synchronizace.

Další informace o streamování a soketech datagram najdete v článcích [Windows Sockets: Pozadí](../../mfc/windows-sockets-background.md) a[sokety Windows: Porty a adresy](../../mfc/windows-sockets-ports-and-socket-addresses.md) soketu a [rozhraní API pro Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

##  <a name="detach"></a>CAsyncSocket::D etach

Zavolejte tuto členskou funkci pro odpojení popisovače soketu v datovém členu *m_hSocket* z `CAsyncSocket` objektu a nastavte *m_hSocket* na hodnotu null.

```
SOCKET Detach();
```

##  <a name="fromhandle"></a>CAsyncSocket:: FromHandle

Vrátí ukazatel na `CAsyncSocket` objekt.

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Obsahuje popisovač pro soket.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CAsyncSocket` objekt nebo hodnotu null, pokud není k *hSocket*připojen `CAsyncSocket` žádný objekt.

### <a name="remarks"></a>Poznámky

Pokud je předána obslužná rutina soketu, pokud `CAsyncSocket` objekt není připojen k popisovači, vrátí členská funkce hodnotu null.

##  <a name="getlasterror"></a>CAsyncSocket:: GetLastError

Voláním této členské funkce získáte chybový stav poslední operace, která se nezdařila.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota označuje kód chyby poslední rutiny rozhraní Windows Sockets API prováděné tímto vláknem.

### <a name="remarks"></a>Poznámky

Pokud konkrétní členská funkce indikuje, že došlo k chybě, `GetLastError` měla by být volána pro načtení příslušného kódu chyby. Seznam platných kódů chyb naleznete v popisu jednotlivých členských funkcí.

Další informace o kódech chyb najdete v tématu [rozhraní API pro Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

##  <a name="getpeername"></a>CAsyncSocket:: getpeere

Zavolejte tuto členskou funkci, aby se získala adresa soketu partnerského zařízení, ke kterému je tento soket připojený.

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);

BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Parametry

*rPeerAddress*<br/>
Odkaz na `CString` objekt, který obdrží IP adresu s tečkovaným číslem.

*rPeerPort*<br/>
Odkaz na objekt UINT, který ukládá port.

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR –](/windows/win32/winsock/sockaddr-2) , která přijímá název soketu partnera.

*lpSockAddrLen*<br/>
Ukazatel na délku adresy v *lpSockAddr* v bajtech. Při návratu argument *lpSockAddrLen* obsahuje skutečnou velikost *lpSockAddr* vrácených v bajtech.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEFAULT argument *lpSockAddrLen* není dostatečně velký.

- WSAEINPROGRESS, že probíhá zablokování volání Windows Sockets.

- WSAENOTCONN soket není připojen.

- WSAENOTSOCK popisovač není soket.

### <a name="remarks"></a>Poznámky

Pro zpracování IPv6 adres použijte [CAsyncSocket:: GetPeerNameEx](#getpeernameex).

##  <a name="getpeernameex"></a>CAsyncSocket:: GetPeerNameEx

Voláním této členské funkce získáte adresu soketu partnerského zařízení, ke kterému je tento soket připojen (zpracovává adresy IPv6).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>Parametry

*rPeerAddress*<br/>
Odkaz na `CString` objekt, který obdrží IP adresu s tečkovaným číslem.

*rPeerPort*<br/>
Odkaz na objekt UINT, který ukládá port.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEFAULT argument *lpSockAddrLen* není dostatečně velký.

- WSAEINPROGRESS, že probíhá zablokování volání Windows Sockets.

- WSAENOTCONN soket není připojen.

- WSAENOTSOCK popisovač není soket.

### <a name="remarks"></a>Poznámky

Tato funkce je stejná jako [CAsyncSocket:: getpeer](#getpeername) , s tím rozdílem, že zpracovává adresy IPv6 i starší protokoly.

##  <a name="getsockname"></a>CAsyncSocket:: GetSockName

Voláním této členské funkce získáte místní název soketu.

```
BOOL GetSockName(
    CString& rSocketAddress,
    UINT& rSocketPort);

BOOL GetSockName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Parametry

*rSocketAddress*<br/>
Odkaz na `CString` objekt, který obdrží IP adresu s tečkovaným číslem.

*rSocketPort*<br/>
Odkaz na objekt UINT, který ukládá port.

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR –](/windows/win32/winsock/sockaddr-2) , která přijímá adresu soketu.

*lpSockAddrLen*<br/>
Ukazatel na délku adresy v *lpSockAddr* v bajtech.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEFAULT argument *lpSockAddrLen* není dostatečně velký.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAENOTSOCK popisovač není soket.

- WSAEINVAL soket nebyl vázán na adresu s `Bind`adresou.

### <a name="remarks"></a>Poznámky

Toto volání je užitečné hlavně v případě `Connect` , že bylo provedeno volání bez `Bind` prvotního provedení; toto volání poskytuje pouze to, jak lze určit místní přidružení, které bylo nastaveno systémem.

Pro zpracování IPv6 adres použijte [CAsyncSocket:: GetSockNameEx](#getsocknameex)

##  <a name="getsocknameex"></a>CAsyncSocket:: GetSockNameEx

Voláním této členské funkce získáte místní název soketu (zpracovává adresy IPv6).

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>Parametry

*rSocketAddress*<br/>
Odkaz na `CString` objekt, který obdrží IP adresu s tečkovaným číslem.

*rSocketPort*<br/>
Odkaz na objekt UINT, který ukládá port.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEFAULT argument *lpSockAddrLen* není dostatečně velký.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAENOTSOCK popisovač není soket.

- WSAEINVAL soket nebyl vázán na adresu s `Bind`adresou.

### <a name="remarks"></a>Poznámky

Toto volání je stejné jako [CAsyncSocket:: getsockname](#getsockname) s tím rozdílem, že zpracovává adresy IPv6 i starší protokoly.

Toto volání je užitečné hlavně v případě `Connect` , že bylo provedeno volání bez `Bind` prvotního provedení; toto volání poskytuje pouze to, jak lze určit místní přidružení, které bylo nastaveno systémem.

##  <a name="getsockopt"></a>CAsyncSocket:: GetSockOpt

Voláním této členské funkce načtěte možnost soketu.

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Parametry

*nOptionName*<br/>
Možnost soketu, pro kterou má být načtena hodnota.

*lpOptionValue*<br/>
Ukazatel na vyrovnávací paměť, ve které má být vrácena hodnota požadované možnosti. Hodnota přidružená k vybrané možnosti se vrátí ve vyrovnávací paměti *lpOptionValue*. Celé číslo, na které odkazuje *lpOptionLen* , by mělo původně obsahovat velikost této vyrovnávací paměti v bajtech. a při návratu bude nastaveno na velikost vrácené hodnoty. Pro SO_LINGER se jedná o velikost `LINGER` struktury. u všech ostatních možností bude velikost bool nebo **int**, a to v závislosti na možnosti. Podívejte se na seznam možností a jejich velikosti v oddílu poznámky.

*lpOptionLen*<br/>
Ukazatel na velikost vyrovnávací paměti *lpOptionValue* v bajtech.

*nLevel*<br/>
Úroveň, na které je možnost definována; Jediné podporované úrovně jsou SOL_SOCKET a IPPROTO_TCP.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Pokud možnost nebyla nikdy nastavena s `SetSockOpt` `GetSockOpt` , vrátí výchozí hodnotu pro možnost. Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEFAULT argument *lpOptionLen* byl neplatný.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAENOPROTOOPT možnost je neznámá nebo nepodporovaná. Konkrétně SO_BROADCAST není podporován na soketech typu SOCK_STREAM, zatímco SO_ACCEPTCONN, SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER a SO_OOBINLINE nejsou podporovány na soketech typu SOCK_DGRAM.

- WSAENOTSOCK popisovač není soket.

### <a name="remarks"></a>Poznámky

`GetSockOpt`Načte aktuální hodnotu pro možnost soketu přidruženou ke soketu libovolného typu v jakémkoli stavu a uloží výsledek do *lpOptionValue*. Možnosti ovlivňují operace soketu, například směrování paketů, přenos dat mimo pásmo a tak dále.

Pro můžete `GetSockOpt`použít následující možnosti. Typ identifikuje typ dat řešených *lpOptionValue*. Možnost TCP_NODELAY používá úroveň IPPROTO_TCP; všechny ostatní možnosti používají úroveň SOL_SOCKET.

|Value|type|Význam|
|-----------|----------|-------------|
|SO_ACCEPTCONN|LOGICK|Soket naslouchá.|
|SO_BROADCAST|LOGICK|Soket je nakonfigurován pro přenos zpráv všesměrového vysílání.|
|SO_DEBUG|LOGICK|Ladění je povoleno.|
|SO_DONTLINGER|LOGICK|Pokud je nastaveno na true, možnost SO_LINGER je zakázaná.|
|SO_DONTROUTE|LOGICK|Směrování je zakázané.|
|SO_ERROR|**int**|Načtěte stav chyby a zrušte zaškrtnutí.|
|SO_KEEPALIVE|LOGICK|Jsou odesílány udržování připojení.|
|SO_LINGER|`struct LINGER`|Vrátí aktuální možnosti pro hodnotu permanentní.|
|SO_OOBINLINE|LOGICK|Data mimo pásmo jsou přijímána v normálním datovém proudu.|
|SO_RCVBUF|int|Velikost vyrovnávací paměti pro příjem.|
|SO_REUSEADDR|LOGICK|Soket může být svázán s adresou, která je již používána.|
|SO_SNDBUF|**int**|Velikost vyrovnávací paměti pro odeslání.|
|SO_TYPE|**int**|Typ soketu (například SOCK_STREAM).|
|TCP_NODELAY|LOGICK|Zakáže Nagle algoritmus pro odesílání slučovacích.|

Možnosti služby Berkeley Software Distribution (BSD) nejsou podporované `GetSockOpt` pro:

|Value|type|Význam|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|Příjem značky s nízkou vodou.|
|SO_RCVTIMEO|**int**|Časový limit příjmu|
|SO_SNDLOWAT|**int**|Poslat nízkou značku na vodu|
|SO_SNDTIMEO|**int**|Časový limit odeslání|
|IP_OPTIONS||Načte možnosti v hlavičce protokolu IP.|
|TCP_MAXSEG|**int**|Získá maximální velikost segmentu TCP.|

Volání `GetSockOpt` s nepodporovanou možností způsobí, že se vrátí chybový kód WSAENOPROTOOPT z `GetLastError`.

##  <a name="ioctl"></a>CAsyncSocket:: IOCtl

Zavolejte tuto členskou funkci pro řízení režimu soketu.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>Parametry

*lCommand*<br/>
Příkaz, který má být proveden na soketu.

*lpArgument*<br/>
Ukazatel na parametr pro *lCommand*.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEINVAL *lCommand* není platný příkaz, nebo *lpArgument* není přijatelný parametr pro *lCommand*, nebo příkaz nelze použít na zadaný typ soketu.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAENOTSOCK popisovač není soket.

### <a name="remarks"></a>Poznámky

Tato rutina se dá použít na jakémkoli soketu v jakémkoli stavu. Slouží k získání nebo načtení provozních parametrů přidružených ke soketu nezávisle na protokolu a komunikačním subsystému. Podporovány jsou následující příkazy:

- FIONBIO povolit nebo zakázat režim neblokování na soketu. Parametr *lpArgument* odkazuje na `DWORD`, což je nenulové, pokud má být režim neblokování povolený a nulový, pokud má být zakázán. Pokud `AsyncSelect` byla na soketu vystavena, pak všechny pokusy o `IOCtl` použití pro nastavení soketu zpět na blokující režim selžou s WSAEINVAL. Chcete-li nastavit návrat zpět na blokující režim a zabránit chybě WSAEINVAL, musí aplikace nejprve `AsyncSelect` zakázat volání `AsyncSelect` s parametrem *Levent* , který se rovná 0 a pak zavolat `IOCtl`.

- FIONREAD určuje maximální počet bajtů, které lze číst jedním `Receive` voláním z tohoto soketu. `IOCtl` Bod *parametru lpArgument* , vekterémjeuloženývýsledek.`DWORD` Pokud je tento soket typu SOCK_STREAM, vrátí FIONREAD celkové množství dat, které lze číst v jednom `Receive`. to je obvykle stejné jako celková velikost dat zařazených do fronty na soketu. Pokud je tento soket typu SOCK_DGRAM, FIONREAD vrátí velikost prvního datagramu ve frontě na soketu.

- SIOCATMARK určuje, zda byla přečtena všechna data mimo pásmo. To platí jenom pro soket typu SOCK_STREAM, který je nakonfigurovaný pro online příjem všech dat mimo IP síť (SO_OOBINLINE). Pokud žádná data mimo pásmo nečekají na čtení, operace vrátí nenulovou hodnotu. V opačném případě vrátí 0 a další `Receive` nebo `ReceiveFrom` provedený na soketu načte některá nebo všechna data před znakem "označit". aplikace by měla použít operaci SIOCATMARK k určení, zda nějaká data zůstanou. Pokud se před daty "naléhavá" (mimo pásmo) nacházejí normální data, bude přijata v daném pořadí. (Všimněte si, `Receive` že `ReceiveFrom` nebo nikdy nebude kombinovat mimo pásmo a normální data ve stejném volání.) `IOCtl` Bod *parametru lpArgument* , vekterémjeuloženývýsledek.`DWORD`

Tato funkce je podmnožinou `ioctl()` , která se používá v Berkeley Sockets. Konkrétně není k dispozici žádný příkaz, který je ekvivalentní FIOASYNC, zatímco SIOCATMARK je jediný příkaz na úrovni soketu, který je podporován.

##  <a name="listen"></a>CAsyncSocket:: Listen

Voláním této členské funkce naslouchat příchozím žádostem o připojení.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>Parametry

*nConnectionBacklog*<br/>
Maximální délka, do které může růst fronta čekajících připojení. Platný rozsah je od 1 do 5.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEADDRINUSE byl proveden pokus o naslouchání na adrese, která se používá.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAEINVAL soket není svázán s `Bind` nebo je již připojen.

- WSAEISCONN soket je již připojen.

- WSAEMFILE nejsou k dispozici žádné další popisovače souboru.

- WSAENOBUFS není k dispozici žádný prostor vyrovnávací paměti.

- WSAENOTSOCK popisovač není soket.

- WSAEOPNOTSUPP odkazovaný soket není typu, který podporuje `Listen` operaci.

### <a name="remarks"></a>Poznámky

Aby bylo možné přijímat připojení, soket se nejprve vytvoří `Create`s `Accept`. pro příchozí připojení se `Listen`zadává nevyřízená položka a pak se připojení akceptují. `Listen`vztahuje se pouze na sokety, které podporují připojení, tedy na ty, které jsou typu SOCK_STREAM. Tento soket je umístěn do pasivního režimu, ve kterém jsou příchozí připojení potvrzena a zařazen do fronty čekající na přijetí procesem.

Tato funkce se obvykle používá na serverech (nebo libovolné aplikaci, která chce přijímat připojení), která by mohla mít více než jednu žádost o připojení. Pokud požadavek na připojení dorazí do fronty zaplněný, obdrží klient chybu s označením WSAECONNREFUSED.

`Listen`se pokusí nadále fungovat, pokud nejsou k dispozici žádné porty (popisovače). Bude přijímat připojení až do vyprázdnění fronty. Pokud budou porty k dispozici, pozdější volání `Listen` nebo `Accept` ji znovu naplní na aktuální nebo poslední "backlog", pokud je to možné, a obnovit naslouchání příchozím připojením.

##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket

Obsahuje popisovač soketu pro soket zapouzdřený tímto `CAsyncSocket` objektem.

```
SOCKET m_hSocket;
```

##  <a name="onaccept"></a>CAsyncSocket:: Souhlasím

Volá se rozhraním, aby se oznámilo naslouchajícímu soketu, že může přijímat žádosti o připojení, a to voláním členské funkce [Accept](#accept) .

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Poslední chyba soketu. Následující chybové kódy se vztahují na `OnAccept` členskou funkci:

- **0** funkce byla úspěšně provedena.

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [Windows Sockets: Oznámení](../../mfc/windows-sockets-socket-notifications.md)soketu.

##  <a name="onclose"></a>CAsyncSocket::-Close

Volá se rozhraním, které oznamuje tomuto soketu, že připojený soket je uzavřený procesem.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Poslední chyba soketu. Následující chybové kódy se vztahují na `OnClose` členskou funkci:

- **0** funkce byla úspěšně provedena.

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAECONNRESET připojení bylo resetováno na vzdálené straně.

- WSAECONNABORTED připojení bylo přerušeno z důvodu vypršení časového limitu nebo jiného selhání.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [Windows Sockets: Oznámení](../../mfc/windows-sockets-socket-notifications.md)soketu.

##  <a name="onconnect"></a>CAsyncSocket:: Connect

Volá se rozhraním, aby se oznámilo připojení soketu, že se dokončil pokus o připojení, ať už se zdařila, nebo došlo k chybě.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Poslední chyba soketu. Následující chybové kódy se vztahují na `OnConnect` členskou funkci:

- **0** funkce byla úspěšně provedena.

- WSAEADDRINUSE zadaná adresa se už používá.

- WSAEADDRNOTAVAIL zadaná adresa není k dispozici z místního počítače.

- V rámci tohoto soketu nelze používat WSAEAFNOSUPPORT adresy v zadané rodině.

- WSAECONNREFUSED pokus o připojení byl nuceně odmítnut.

- WSAEDESTADDRREQ je vyžadována cílová adresa.

- WSAEFAULT argument *lpSockAddrLen* není správný.

- WSAEINVAL soket již je svázán s adresou.

- WSAEISCONN soket je již připojen.

- WSAEMFILE nejsou k dispozici žádné další popisovače souboru.

- V tuto chvíli není možné WSAENETUNREACH síť kontaktovat z tohoto hostitele.

- WSAENOBUFS není k dispozici žádný prostor vyrovnávací paměti. Soket nelze připojit.

- WSAENOTCONN soket není připojen.

- WSAENOTSOCK popisovač je soubor, nikoli soket.

- WSAETIMEDOUT pokusu o připojení vypršel časový limit bez navázání připojení.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  V [CSocket –](../../mfc/reference/csocket-class.md) `OnConnect` se funkce oznámení nikdy nevolá. V případě připojení jednoduše voláte `Connect`, což vrátí po dokončení připojení (buď úspěšně, nebo v případě chyby). Jak jsou zpracovávána oznámení o připojení, je podrobnostmi implementace knihovny MFC.

Další informace najdete v tématu [Windows Sockets: Oznámení](../../mfc/windows-sockets-socket-notifications.md)soketu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

##  <a name="onoutofbanddata"></a>CAsyncSocket:: OnOutOfBandData

Volá se rozhraním, aby se oznámilo přijímajícímu soketu, že odesílající soket má data mimo IP síť k odeslání.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Poslední chyba soketu. Následující chybové kódy se vztahují na `OnOutOfBandData` členskou funkci:

- **0** funkce byla úspěšně provedena.

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

### <a name="remarks"></a>Poznámky

Data mimo IP síť jsou logicky nezávislý kanál, který je spojen s každou dvojicí připojených soketů typu SOCK_STREAM. Kanál se obecně používá k posílání naléhavých dat.

Knihovna MFC podporuje data mimo IP síť, ale uživatelé třídy `CAsyncSocket` je nedoporučuje používat. Jednodušším způsobem je vytvořit druhý soket pro předávání těchto dat. Další informace o datech mimo IP síť najdete v tématu [Windows Sockets: Oznámení](../../mfc/windows-sockets-socket-notifications.md)soketu.

##  <a name="onreceive"></a>CAsyncSocket:: inreceive

Volá se rozhraním, aby se tomuto soketu oznámilo, že ve vyrovnávací paměti existuje data, která lze `Receive` načíst voláním členské funkce.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Poslední chyba soketu. Následující chybové kódy se vztahují na `OnReceive` členskou funkci:

- **0** funkce byla úspěšně provedena.

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [Windows Sockets: Oznámení](../../mfc/windows-sockets-socket-notifications.md)soketu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

##  <a name="onsend"></a>CAsyncSocket:: Send – odeslání

Volá se rozhraním, aby se upozornilo na soket, že teď může odesílat data `Send` voláním členské funkce.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Poslední chyba soketu. Následující chybové kódy se vztahují na `OnSend` členskou funkci:

- **0** funkce byla úspěšně provedena.

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [Windows Sockets: Oznámení](../../mfc/windows-sockets-socket-notifications.md)soketu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

##  <a name="operator_eq"></a>CAsyncSocket:: operator =

Přiřadí novou hodnotu `CAsyncSocket` objektu.

```
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odkaz na existující `CAsyncSocket` objekt.

### <a name="remarks"></a>Poznámky

Voláním této funkce zkopírujte existující `CAsyncSocket` objekt do jiného `CAsyncSocket` objektu.

##  <a name="operator_socket"></a>CAsyncSocket:: operator – SOKET

Tento operátor použijte k načtení popisovače `CAsyncSocket` soketu objektu.

```
operator SOCKET() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač objektu SOKETu; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Můžete použít popisovač k přímému volání rozhraní API systému Windows.

##  <a name="receive"></a>CAsyncSocket:: Receive

Zavolejte tuto členskou funkci pro příjem dat z soketu.

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Vyrovnávací paměť pro příchozí data.

*nBufLen*<br/>
Délka *lpBuf* v bajtech.

*nFlags*<br/>
Určuje způsob, jakým je provedeno volání. Sémantika této funkce je určena možnostmi soketu a parametrem *nFlags* . Druhá je vytvořena kombinací libovolné z následujících hodnot s C++ operátorem **or** :

- MSG_PEEK si prohlížet příchozí data. Data se zkopírují do vyrovnávací paměti, ale neodstraní se ze vstupní fronty.

- MSG_OOB zpracovávat data mimo pásmo.

### <a name="return-value"></a>Návratová hodnota

Pokud nedojde k žádné chybě `Receive` , vrátí počet přijatých bajtů. Pokud bylo připojení uzavřeno, vrátí hodnotu 0. V opačném případě se vrátí hodnota SOCKET_ERROR a konkrétní kód chyby lze načíst voláním metody [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAENOTCONN soket není připojen.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAENOTSOCK popisovač není soket.

- Byl zadán WSAEOPNOTSUPP MSG_OOB, ale soket není typu SOCK_STREAM.

- WSAESHUTDOWN, že se soket vypnul; Po `Receive` vyvolání`ShutDown` s *Nhow* nastavenou na hodnotu 0 nebo 2 není možné volat na soket.

- WSAEWOULDBLOCK je soket označený jako neblokované a `Receive` operace by měla být zablokovaná.

- WSAEMSGSIZE datagram byl příliš velký, aby se vešel do zadané vyrovnávací paměti a byl zkrácen.

- WSAEINVAL soket není svázán s `Bind`.

- WSAECONNABORTED virtuální okruh byl přerušen z důvodu vypršení časového limitu nebo jiného selhání.

- WSAECONNRESET virtuální okruh byl resetován na vzdálené straně.

### <a name="remarks"></a>Poznámky

Tato funkce se používá pro připojené streamy nebo sokety datagramů a používá se ke čtení příchozích dat.

V případě soketů typu SOCK_STREAM je vráceno množství informací, které jsou aktuálně dostupné až do velikosti poskytnuté vyrovnávací paměti. Pokud byl soket nakonfigurovaný pro online příjem dat mimo pásmo (možnost soketu SO_OOBINLINE) a data mimo IP síť, budou se vracet jenom data mimo pásmo. Aplikace může použít `IOCtlSIOCATMARK` možnost nebo [OnOutOfBandData](#onoutofbanddata) k určení, zda je třeba přečtení jakýchkoli dalších dat mimo pásmo.

Pro sokety datagramů se data extrahují z prvního datagramu ve frontě, až do velikosti dodané vyrovnávací paměti. Pokud je datagram větší než dodaný vyrovnávací paměť, vyrovnávací paměť se vyplní první částí datagramu, přebývající data se ztratí a `Receive` vrátí hodnotu SOCKET_ERROR s kódem chyby nastaveným na WSAEMSGSIZE. Pokud nejsou žádná příchozí data na soketu k dispozici, vrátí se hodnota SOCKET_ERROR s kódem chyby nastaveným na WSAEWOULDBLOCK. Funkce zpětného volání [Receive](#onreceive) se dá použít k určení, kdy přijdete o další data.

Pokud je soket typu SOCK_STREAM a Vzdálená strana řádně vypnula připojení, dojde k `Receive` okamžitému dokončení s 0 bajty. Pokud bylo připojení obnoveno, `Receive` selže chyba WSAECONNRESET.

`Receive`má být volána pouze jednou pro každé volání [CAsyncSocket:: inreceive](#onreceive) .

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CAsyncSocket:: inreceive](#onreceive).

##  <a name="receivefrom"></a>CAsyncSocket:: ReceiveFrom

Tuto členskou funkci volejte pro příjem datagramu a uložte si zdrojovou adresu ve struktuře [SOCKADDR –](/windows/win32/winsock/sockaddr-2) nebo v *rSocketAddress*.

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

*lpBuf*<br/>
Vyrovnávací paměť pro příchozí data.

*nBufLen*<br/>
Délka *lpBuf* v bajtech.

*rSocketAddress*<br/>
Odkaz na `CString` objekt, který obdrží IP adresu s tečkovaným číslem.

*rSocketPort*<br/>
Odkaz na objekt UINT, který ukládá port.

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR –](/windows/win32/winsock/sockaddr-2) , která po návratu obsahuje zdrojovou adresu.

*lpSockAddrLen*<br/>
Ukazatel na délku zdrojové adresy v *lpSockAddr* v bajtech.

*nFlags*<br/>
Určuje způsob, jakým je provedeno volání. Sémantika této funkce je určena možnostmi soketu a parametrem *nFlags* . Druhá je vytvořena kombinací libovolné z následujících hodnot s C++ operátorem **or** :

- MSG_PEEK si prohlížet příchozí data. Data se zkopírují do vyrovnávací paměti, ale neodstraní se ze vstupní fronty.

- MSG_OOB zpracovávat data mimo pásmo.

### <a name="return-value"></a>Návratová hodnota

Pokud nedojde k žádné chybě `ReceiveFrom` , vrátí počet přijatých bajtů. Pokud bylo připojení uzavřeno, vrátí hodnotu 0. V opačném případě se vrátí hodnota SOCKET_ERROR a konkrétní kód chyby lze načíst voláním `GetLastError`. Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEFAULT argument *lpSockAddrLen* byl neplatný: vyrovnávací paměť *lpSockAddr* byla příliš malá, aby mohla pojmout adresu partnerského zařízení.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAEINVAL soket není svázán s `Bind`.

- WSAENOTCONN soket není připojený (jenom SOCK_STREAM).

- WSAENOTSOCK popisovač není soket.

- Byl zadán WSAEOPNOTSUPP MSG_OOB, ale soket není typu SOCK_STREAM.

- WSAESHUTDOWN, že se soket vypnul; Po `ReceiveFrom` vyvolání`ShutDown` s *Nhow* nastavenou na hodnotu 0 nebo 2 není možné volat na soket.

- WSAEWOULDBLOCK je soket označený jako neblokované a `ReceiveFrom` operace by měla být zablokovaná.

- WSAEMSGSIZE datagram byl příliš velký, aby se vešel do zadané vyrovnávací paměti a byl zkrácen.

- WSAECONNABORTED virtuální okruh byl přerušen z důvodu vypršení časového limitu nebo jiného selhání.

- WSAECONNRESET virtuální okruh byl resetován na vzdálené straně.

### <a name="remarks"></a>Poznámky

Tato funkce slouží ke čtení příchozích dat v (případně připojeném) soketu a k zachycení adresy, ze které byla data odeslána.

Pro zpracování IPv6 adres použijte [CAsyncSocket:: ReceiveFromEx](#receivefromex).

V případě soketů typu SOCK_STREAM je vráceno množství informací, které jsou aktuálně dostupné až do velikosti poskytnuté vyrovnávací paměti. Pokud byl soket nakonfigurovaný pro online příjem dat mimo pásmo (možnost soketu SO_OOBINLINE) a data mimo IP síť, budou se vracet jenom data mimo pásmo. Aplikace může použít `IOCtlSIOCATMARK` možnost nebo `OnOutOfBandData` k určení, jestli je potřeba číst jiná data mimo pásmo. Parametry *lpSockAddr* a *lpSockAddrLen* se pro sokety SOCK_STREAM ignorují.

Pro sokety datagramů se data extrahují z prvního datagramu ve frontě, až do velikosti dodané vyrovnávací paměti. Pokud je datagram větší než dodaný vyrovnávací paměť, je vyrovnávací paměť vyplněna první částí zprávy, dojde ke ztrátě přebytečných dat a `ReceiveFrom` vrátí hodnotu SOCKET_ERROR s kódem chyby nastaveným na WSAEMSGSIZE.

Pokud *lpSockAddr* není nula a soket je typu SOCK_DGRAM, bude síťová adresa soketu, která odeslala data, zkopírována do odpovídající struktury [SOCKADDR –](/windows/win32/winsock/sockaddr-2) . Hodnota, na kterou se odkazuje pomocí *lpSockAddrLen* , se inicializuje na velikost této struktury a při návratu se upraví tak, aby označovala skutečnou velikost uložené adresy. Pokud nejsou žádná příchozí data na soketu k dispozici `ReceiveFrom` , volání počká, než se data dostanou, pokud soket neblokuje. V tomto případě se vrátí hodnota SOCKET_ERROR s kódem chyby nastaveným na WSAEWOULDBLOCK. `OnReceive` Zpětné volání lze použít k určení, kdy dorazí více dat.

Pokud je soket typu SOCK_STREAM a Vzdálená strana řádně vypnula připojení, dojde k `ReceiveFrom` okamžitému dokončení s 0 bajty.

##  <a name="receivefromex"></a>CAsyncSocket:: ReceiveFromEx

Tuto členskou funkci volejte pro příjem datagramu a uložte si zdrojovou adresu ve struktuře [SOCKADDR –](/windows/win32/winsock/sockaddr-2) nebo v *rSocketAddress* (zpracovává adresy IPv6).

```
int ReceiveFromEx(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Vyrovnávací paměť pro příchozí data.

*nBufLen*<br/>
Délka *lpBuf* v bajtech.

*rSocketAddress*<br/>
Odkaz na `CString` objekt, který obdrží IP adresu s tečkovaným číslem.

*rSocketPort*<br/>
Odkaz na objekt UINT, který ukládá port.

*nFlags*<br/>
Určuje způsob, jakým je provedeno volání. Sémantika této funkce je určena možnostmi soketu a parametrem *nFlags* . Druhá je vytvořena kombinací libovolné z následujících hodnot s C++ operátorem **or** :

- MSG_PEEK si prohlížet příchozí data. Data se zkopírují do vyrovnávací paměti, ale neodstraní se ze vstupní fronty.

- MSG_OOB zpracovávat data mimo pásmo.

### <a name="return-value"></a>Návratová hodnota

Pokud nedojde k žádné chybě `ReceiveFromEx` , vrátí počet přijatých bajtů. Pokud bylo připojení uzavřeno, vrátí hodnotu 0. V opačném případě se vrátí hodnota SOCKET_ERROR a konkrétní kód chyby lze načíst voláním `GetLastError`. Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEFAULT argument *lpSockAddrLen* byl neplatný: vyrovnávací paměť *lpSockAddr* byla příliš malá, aby mohla pojmout adresu partnerského zařízení.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAEINVAL soket není svázán s `Bind`.

- WSAENOTCONN soket není připojený (jenom SOCK_STREAM).

- WSAENOTSOCK popisovač není soket.

- Byl zadán WSAEOPNOTSUPP MSG_OOB, ale soket není typu SOCK_STREAM.

- WSAESHUTDOWN, že se soket vypnul; Po `ReceiveFromEx` vyvolání`ShutDown` s *Nhow* nastavenou na hodnotu 0 nebo 2 není možné volat na soket.

- WSAEWOULDBLOCK je soket označený jako neblokované a `ReceiveFromEx` operace by měla být zablokovaná.

- WSAEMSGSIZE datagram byl příliš velký, aby se vešel do zadané vyrovnávací paměti a byl zkrácen.

- WSAECONNABORTED virtuální okruh byl přerušen z důvodu vypršení časového limitu nebo jiného selhání.

- WSAECONNRESET virtuální okruh byl resetován na vzdálené straně.

### <a name="remarks"></a>Poznámky

Tato funkce slouží ke čtení příchozích dat v (případně připojeném) soketu a k zachycení adresy, ze které byla data odeslána.

Tato funkce je stejná jako [CAsyncSocket:: ReceiveFrom](#receivefrom) s tím rozdílem, že zpracovává adresy IPv6 i starší protokoly.

V případě soketů typu SOCK_STREAM je vráceno množství informací, které jsou aktuálně dostupné až do velikosti poskytnuté vyrovnávací paměti. Pokud byl soket nakonfigurovaný pro online příjem dat mimo pásmo (možnost soketu SO_OOBINLINE) a data mimo IP síť, budou se vracet jenom data mimo pásmo. Aplikace může použít `IOCtlSIOCATMARK` možnost nebo `OnOutOfBandData` k určení, jestli je potřeba číst jiná data mimo pásmo. Parametry *lpSockAddr* a *lpSockAddrLen* se pro sokety SOCK_STREAM ignorují.

Pro sokety datagramů se data extrahují z prvního datagramu ve frontě, až do velikosti dodané vyrovnávací paměti. Pokud je datagram větší než dodaný vyrovnávací paměť, je vyrovnávací paměť vyplněna první částí zprávy, dojde ke ztrátě přebytečných dat a `ReceiveFromEx` vrátí hodnotu SOCKET_ERROR s kódem chyby nastaveným na WSAEMSGSIZE.

Pokud *lpSockAddr* není nula a soket je typu SOCK_DGRAM, bude síťová adresa soketu, která odeslala data, zkopírována do odpovídající struktury [SOCKADDR –](/windows/win32/winsock/sockaddr-2) . Hodnota, na kterou se odkazuje pomocí *lpSockAddrLen* , se inicializuje na velikost této struktury a při návratu se upraví tak, aby označovala skutečnou velikost uložené adresy. Pokud nejsou žádná příchozí data na soketu k dispozici `ReceiveFromEx` , volání počká, než se data dostanou, pokud soket neblokuje. V tomto případě se vrátí hodnota SOCKET_ERROR s kódem chyby nastaveným na WSAEWOULDBLOCK. `OnReceive` Zpětné volání lze použít k určení, kdy dorazí více dat.

Pokud je soket typu SOCK_STREAM a Vzdálená strana řádně vypnula připojení, dojde k `ReceiveFromEx` okamžitému dokončení s 0 bajty.

##  <a name="send"></a>CAsyncSocket:: Send

Zavolejte tuto členskou funkci pro posílání dat na připojeném soketu.

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Vyrovnávací paměť obsahující data, která mají být přenesena.

*nBufLen*<br/>
Délka dat v *lpBuf* v bajtech.

*nFlags*<br/>
Určuje způsob, jakým je provedeno volání. Sémantika této funkce je určena možnostmi soketu a parametrem *nFlags* . Druhá je vytvořena kombinací libovolné z následujících hodnot s C++ operátorem **or** :

- MSG_DONTROUTE určuje, že by se neměla vztahovat na data směrování. Dodavatel Windows Sockets může zvolit ignorování tohoto příznaku.

- MSG_OOB odesílají data mimo IP síť (jenom SOCK_STREAM).

### <a name="return-value"></a>Návratová hodnota

Pokud nedojde k žádné chybě `Send` , vrátí celkový počet odeslaných znaků. (Všimněte si, že může být menší než číslo uvedené v *nBufLen*.) V opačném případě se vrátí hodnota SOCKET_ERROR a konkrétní kód chyby lze načíst voláním metody [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEACCES požadovaná adresa je adresa všesměrového vysílání, ale nebyl nastaven odpovídající příznak.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAEFAULT argument *lpBuf* není v platné části adresního prostoru uživatele.

- WSAENETRESET připojení je potřeba resetovat, protože implementace rozhraní Windows Sockets ji zrušila.

- WSAENOBUFS implementace rozhraní Windows Sockets hlásí zablokování vyrovnávací paměti.

- WSAENOTCONN soket není připojen.

- WSAENOTSOCK popisovač není soket.

- Byl zadán WSAEOPNOTSUPP MSG_OOB, ale soket není typu SOCK_STREAM.

- WSAESHUTDOWN, že se soket vypnul; Po `Send` vyvolání`ShutDown` s *Nhow* nastavenou na 1 nebo 2 není možné volat na soket.

- WSAEWOULDBLOCK je soket označený jako neblokované a požadovaná operace by byla zablokovaná.

- WSAEMSGSIZE soket je typu SOCK_DGRAM a datagram je větší než maximální délka podporovaná implementací rozhraní Windows Sockets.

- WSAEINVAL soket není svázán s `Bind`.

- WSAECONNABORTED virtuální okruh byl přerušen z důvodu vypršení časového limitu nebo jiného selhání.

- WSAECONNRESET virtuální okruh byl resetován na vzdálené straně.

### <a name="remarks"></a>Poznámky

`Send`slouží k zápisu odchozích dat do propojeného datového proudu nebo soketů datagramů. Pro sokety datagramů musí být nutné dbát na to, aby nepřekročily maximální velikost paketu IP podkladových podsítí, `iMaxUdpDg` která je dána prvkem ve struktuře [WSADATA –](/windows/win32/api/winsock2/ns-winsock2-wsadata) , kterou vrací `AfxSocketInit`. Pokud jsou data příliš dlouhá k atomicky procházela prostřednictvím základního protokolu, vrátí se chyba WSAEMSGSIZE prostřednictvím `GetLastError`a nebudou přenášena žádná data.

Všimněte si, že u soketu datagramu úspěšné `Send` dokončení a neindikuje, že data byla úspěšně doručena.

U `CAsyncSocket` objektů typu SOCK_STREAM může být počet zapsaných bajtů mezi 1 a požadovanou délkou v závislosti na dostupnosti vyrovnávací paměti na místních i zahraničních hostitelích.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CAsyncSocket:: Send](#onsend).

##  <a name="sendto"></a>CAsyncSocket:: SendTo

Zavolejte tuto členskou funkci pro odeslání dat do konkrétního cíle.

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

*lpBuf*<br/>
Vyrovnávací paměť obsahující data, která mají být přenesena.

*nBufLen*<br/>
Délka dat v *lpBuf* v bajtech.

*nHostPort*<br/>
Port identifikující aplikaci soketu.

*lpszHostAddress*<br/>
Síťová adresa soketu, ke kterému je tento objekt připojen: název počítače, například "ftp.microsoft.com" nebo číslo s tečkami, například "128.56.22.8".

*nFlags*<br/>
Určuje způsob, jakým je provedeno volání. Sémantika této funkce je určena možnostmi soketu a parametrem *nFlags* . Druhá je vytvořena kombinací libovolné z následujících hodnot s C++ operátorem **or** :

- MSG_DONTROUTE určuje, že by se neměla vztahovat na data směrování. Dodavatel Windows Sockets může zvolit ignorování tohoto příznaku.

- MSG_OOB odesílají data mimo IP síť (jenom SOCK_STREAM).

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR –](/windows/win32/winsock/sockaddr-2) , která obsahuje adresu cílového soketu.

*nSockAddrLen*<br/>
Délka adresy v *lpSockAddr* v bajtech

### <a name="return-value"></a>Návratová hodnota

Pokud nedojde k žádné chybě `SendTo` , vrátí celkový počet odeslaných znaků. (Všimněte si, že může být menší než číslo uvedené v *nBufLen*.) V opačném případě se vrátí hodnota SOCKET_ERROR a konkrétní kód chyby lze načíst voláním metody [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEACCES požadovaná adresa je adresa všesměrového vysílání, ale nebyl nastaven odpovídající příznak.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAEFAULT parametry *lpBuf* nebo *lpSockAddr* nejsou součástí adresního prostoru uživatele nebo je argument *lpSockAddr* příliš malý (menší než velikost [SOCKADDR –](/windows/win32/winsock/sockaddr-2) struktury).

- WSAEINVAL název hostitele je neplatný.

- WSAENETRESET připojení je potřeba resetovat, protože implementace rozhraní Windows Sockets ji zrušila.

- WSAENOBUFS implementace rozhraní Windows Sockets hlásí zablokování vyrovnávací paměti.

- WSAENOTCONN soket není připojený (jenom SOCK_STREAM).

- WSAENOTSOCK popisovač není soket.

- Byl zadán WSAEOPNOTSUPP MSG_OOB, ale soket není typu SOCK_STREAM.

- WSAESHUTDOWN, že se soket vypnul; Po `SendTo` vyvolání`ShutDown` s *Nhow* nastavenou na 1 nebo 2 není možné volat na soket.

- WSAEWOULDBLOCK je soket označený jako neblokované a požadovaná operace by byla zablokovaná.

- WSAEMSGSIZE soket je typu SOCK_DGRAM a datagram je větší než maximální délka podporovaná implementací rozhraní Windows Sockets.

- WSAECONNABORTED virtuální okruh byl přerušen z důvodu vypršení časového limitu nebo jiného selhání.

- WSAECONNRESET virtuální okruh byl resetován na vzdálené straně.

- WSAEADDRNOTAVAIL zadaná adresa není k dispozici z místního počítače.

- V rámci tohoto soketu nelze používat WSAEAFNOSUPPORT adresy v zadané rodině.

- WSAEDESTADDRREQ je vyžadována cílová adresa.

- V tuto chvíli není možné WSAENETUNREACH síť kontaktovat z tohoto hostitele.

### <a name="remarks"></a>Poznámky

`SendTo`používá se pro datagramy nebo sokety streamu a používá se k zápisu odchozích dat na soketu. Pro sokety datagramů musí být nutné dbát na to, aby nepřekročily maximální velikost paketu IP podkladových podsítí, `iMaxUdpDg` která je dána prvkem ve struktuře [WSADATA –](/windows/win32/api/winsock2/ns-winsock2-wsadata) vyplněnou [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Pokud jsou data příliš dlouhá k atomicky procházela prostřednictvím základního protokolu, vrátí se chyba WSAEMSGSIZE a nebudou přenášena žádná data.

Všimněte si, že úspěšné dokončení a `SendTo` neindikuje, že data byla úspěšně doručena.

`SendTo`se používá jenom na soketu SOCK_DGRAM k odeslání datagramu na konkrétní soket identifikovaný parametrem *lpSockAddr* .

Pokud chcete odeslat všesměrové vysílání (jenom na SOCK_DGRAM), musí být adresa v parametru *lpSockAddr* vytvořená pomocí speciální IP adresy INADDR_BROADCAST (definované v souboru hlaviček rozhraní Windows Sockets. H) spolu s plánovaným číslem portu. Nebo, pokud má parametr *lpszHostAddress* hodnotu null, je soket nakonfigurován pro všesměrové vysílání. Obecně není vhodné, aby datagram všesměrového vysílání překročil velikost, při které může dojít k fragmentaci, což znamená, že datová část datagramu (s výjimkou hlaviček) by neměla překročit 512 bajtů.

Pro zpracování IPv6 adres použijte [CAsyncSocket:: SendToEx](#sendtoex).

##  <a name="sendtoex"></a>CAsyncSocket:: SendToEx

Voláním této členské funkce můžete odesílat data do konkrétního cíle (zpracovává adresy IPv6).

```
int SendToEx(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Vyrovnávací paměť obsahující data, která mají být přenesena.

*nBufLen*<br/>
Délka dat v *lpBuf* v bajtech.

*nHostPort*<br/>
Port identifikující aplikaci soketu.

*lpszHostAddress*<br/>
Síťová adresa soketu, ke kterému je tento objekt připojen: název počítače, například "ftp.microsoft.com" nebo číslo s tečkami, například "128.56.22.8".

*nFlags*<br/>
Určuje způsob, jakým je provedeno volání. Sémantika této funkce je určena možnostmi soketu a parametrem *nFlags* . Druhá je vytvořena kombinací libovolné z následujících hodnot s C++ operátorem **or** :

- MSG_DONTROUTE určuje, že by se neměla vztahovat na data směrování. Dodavatel Windows Sockets může zvolit ignorování tohoto příznaku.

- MSG_OOB odesílají data mimo IP síť (jenom SOCK_STREAM).

### <a name="return-value"></a>Návratová hodnota

Pokud nedojde k žádné chybě `SendToEx` , vrátí celkový počet odeslaných znaků. (Všimněte si, že může být menší než číslo uvedené v *nBufLen*.) V opačném případě se vrátí hodnota SOCKET_ERROR a konkrétní kód chyby lze načíst voláním metody [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEACCES požadovaná adresa je adresa všesměrového vysílání, ale nebyl nastaven odpovídající příznak.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAEFAULT parametry *lpBuf* nebo *lpSockAddr* nejsou součástí adresního prostoru uživatele nebo je argument *lpSockAddr* příliš malý (menší než velikost [SOCKADDR –](/windows/win32/winsock/sockaddr-2) struktury).

- WSAEINVAL název hostitele je neplatný.

- WSAENETRESET připojení je potřeba resetovat, protože implementace rozhraní Windows Sockets ji zrušila.

- WSAENOBUFS implementace rozhraní Windows Sockets hlásí zablokování vyrovnávací paměti.

- WSAENOTCONN soket není připojený (jenom SOCK_STREAM).

- WSAENOTSOCK popisovač není soket.

- Byl zadán WSAEOPNOTSUPP MSG_OOB, ale soket není typu SOCK_STREAM.

- WSAESHUTDOWN, že se soket vypnul; Po `SendToEx` vyvolání`ShutDown` s *Nhow* nastavenou na 1 nebo 2 není možné volat na soket.

- WSAEWOULDBLOCK je soket označený jako neblokované a požadovaná operace by byla zablokovaná.

- WSAEMSGSIZE soket je typu SOCK_DGRAM a datagram je větší než maximální délka podporovaná implementací rozhraní Windows Sockets.

- WSAECONNABORTED virtuální okruh byl přerušen z důvodu vypršení časového limitu nebo jiného selhání.

- WSAECONNRESET virtuální okruh byl resetován na vzdálené straně.

- WSAEADDRNOTAVAIL zadaná adresa není k dispozici z místního počítače.

- V rámci tohoto soketu nelze používat WSAEAFNOSUPPORT adresy v zadané rodině.

- WSAEDESTADDRREQ je vyžadována cílová adresa.

- V tuto chvíli není možné WSAENETUNREACH síť kontaktovat z tohoto hostitele.

### <a name="remarks"></a>Poznámky

Tato metoda je stejná jako [CAsyncSocket:: SendTo](#sendto) s tím rozdílem, že zpracovává adresy IPv6 i starší protokoly.

`SendToEx`používá se pro datagramy nebo sokety streamu a používá se k zápisu odchozích dat na soketu. Pro sokety datagramů musí být nutné dbát na to, aby nepřekročily maximální velikost paketu IP podkladových podsítí, `iMaxUdpDg` která je dána prvkem ve struktuře [WSADATA –](/windows/win32/api/winsock2/ns-winsock2-wsadata) vyplněnou [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Pokud jsou data příliš dlouhá k atomicky procházela prostřednictvím základního protokolu, vrátí se chyba WSAEMSGSIZE a nebudou přenášena žádná data.

Všimněte si, že úspěšné dokončení a `SendToEx` neindikuje, že data byla úspěšně doručena.

`SendToEx`se používá jenom na soketu SOCK_DGRAM k odeslání datagramu na konkrétní soket identifikovaný parametrem *lpSockAddr* .

Pokud chcete odeslat všesměrové vysílání (jenom na SOCK_DGRAM), musí být adresa v parametru *lpSockAddr* vytvořená pomocí speciální IP adresy INADDR_BROADCAST (definované v souboru hlaviček rozhraní Windows Sockets. H) spolu s plánovaným číslem portu. Nebo, pokud má parametr *lpszHostAddress* hodnotu null, je soket nakonfigurován pro všesměrové vysílání. Obecně není vhodné, aby datagram všesměrového vysílání překročil velikost, při které může dojít k fragmentaci, což znamená, že datová část datagramu (s výjimkou hlaviček) by neměla překročit 512 bajtů.

##  <a name="setsockopt"></a>CAsyncSocket:: SetSockOpt

Chcete-li nastavit možnost soketu, zavolejte tuto členskou funkci.

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Parametry

*nOptionName*<br/>
Možnost soketu, pro kterou má být nastavena hodnota.

*lpOptionValue*<br/>
Ukazatel na vyrovnávací paměť, ve které je zadána hodnota požadované možnosti.

*nOptionLen*<br/>
Velikost vyrovnávací paměti *lpOptionValue* v bajtech

*nLevel*<br/>
Úroveň, na které je možnost definována; Jediné podporované úrovně jsou SOL_SOCKET a IPPROTO_TCP.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEFAULT *lpOptionValue* není v platné části adresního prostoru procesu.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAEINVAL *nLevel* není platná nebo nejsou platné informace v *lpOptionValue* .

- Při nastavení SO_KEEPALIVE vypršel časový limit pro připojení WSAENETRESET.

- WSAENOPROTOOPT možnost je neznámá nebo nepodporovaná. Konkrétně SO_BROADCAST není podporován na soketech typu SOCK_STREAM, zatímco SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER a SO_OOBINLINE nejsou podporovány na soketech typu SOCK_DGRAM.

- Připojení WSAENOTCONN se obnovilo, když je nastavená SO_KEEPALIVE.

- WSAENOTSOCK popisovač není soket.

### <a name="remarks"></a>Poznámky

`SetSockOpt`Nastaví aktuální hodnotu možnosti soketu přidruženou ke soketu libovolného typu v libovolném stavu. I když můžou existovat možnosti na více úrovních protokolu, Tato specifikace definuje jenom možnosti, které existují na nejvyšší úrovni soketu. Možnosti ovlivňují operace soketu, například zda jsou v normálním datovém proudu přijímány urychlená data, zda je možné odesílat zprávy všesměrového vysílání na soketu a tak dále.

Existují dva typy možností soketu: Logické možnosti, které povolují nebo zakazují funkci nebo chování a možnosti, které vyžadují celočíselnou hodnotu nebo strukturu. Chcete-li povolit logickou možnost, *lpOptionValue* odkazuje na nenulové celé číslo. Chcete-li zakázat možnost *lpOptionValue* Points na celé číslo, které se rovná nule. *nOptionLen* by se měl rovnat `sizeof(BOOL)` pro logické možnosti. Pro jiné možnosti *lpOptionValue* odkazuje na celé číslo nebo strukturu, která obsahuje požadovanou hodnotu pro možnost a *nOptionLen* je délka celého čísla nebo struktury.

SO_LINGER řídí akci provedenou v případě, že neodeslané údaje jsou zařazeny do `Close` fronty na soketu a zavolá se funkce pro zavření soketu.

Ve výchozím nastavení nemůže být soket vázaný (viz [BIND](#bind)) na místní adresu, která je již používána. V některých případech ale může být vhodné tuto adresu tímto způsobem znovu použít. Vzhledem k tomu, že každé připojení je jednoznačně identifikováno kombinací místních a vzdálených adres, není k dispozici žádný problém se dvěma sokety vázanými na stejnou místní adresu, pokud se vzdálené adresy liší.

Aby bylo možné informovat o implementaci rozhraní Windows `Bind` Sockets, že volání na soket by nemělo být zakázáno, protože požadovaná adresa je již používána jiným soketem, aplikace by měla před vydáním služby nastavit možnost soketu SO_REUSEADDR pro soket. `Bind` volání. Všimněte si, že možnost je interpretována pouze v době `Bind` volání: je tedy zbytečné (ale neškodné) pro nastavení možnosti na soketu, která nemá být vázána na existující adresu a nastavení nebo obnovení možnosti `Bind` po volání žádný vliv na tento nebo žádný jiný soket.

Aplikace může požádat o to, aby implementace rozhraní Windows Sockets povolovala použití paketů Keep-Alive v připojeních protokolu TCP (Transmission Control Protocol) zapnutím možnosti soketu SO_KEEPALIVE. Implementace rozhraní Windows Sockets nemusí podporovat použití Keep-Alive: Pokud má, bude Přesná sémantika specifická pro konkrétní implementaci, ale měla by odpovídat části 4.2.3.6 dokumentu RFC 1122: "Požadavky na hostitele v Internetu – komunikační vrstvy." Pokud je připojení vyřazené jako výsledek "Keep-Alive", kód chyby WSAENETRESET se vrátí do všech probíhajících volání na soketu a jakákoli následná volání selžou s WSAENOTCONN.

Možnost TCP_NODELAY zakáže Nagle algoritmus. Algoritmus Nagle se používá ke snížení počtu malých paketů odesílaných hostitelem pomocí ukládání nepotvrzených odesílaných dat do vyrovnávací paměti, dokud nebude možné odeslat paket o plné velikosti. U některých aplikací ale tento algoritmus může mít vliv na výkon a TCP_NODELAY je možné použít k jeho vypnutí. Modul pro zápis aplikací by neměl nastavovat TCP_NODELAY, pokud není dopad jejich nevhodně srozumitelný a žádoucí, protože nastavení TCP_NODELAY může mít významný negativní dopad na výkon sítě. TCP_NODELAY je jediná podporovaná možnost soketu, která používá úroveň IPPROTO_TCP; všechny ostatní možnosti používají úroveň SOL_SOCKET.

Některé implementace rozhraní Windows Sockets poskytují výstupní ladicí informace, pokud je možnost SO_DEBUG nastavena aplikací.

Pro můžete `SetSockOpt`použít následující možnosti. Typ identifikuje typ dat řešených *lpOptionValue*.

|Value|type|Význam|
|-----------|----------|-------------|
|SO_BROADCAST|LOGICK|Povolí přenos zpráv všesměrového vysílání na soketu.|
|SO_DEBUG|LOGICK|Zaznamenat informace o ladění.|
|SO_DONTLINGER|LOGICK|Neblokovat `Close` čekání na odeslání neodeslaných dat Nastavení této možnosti je stejné jako nastavení SO_LINGER s `l_onoff` nastavením na nulu.|
|SO_DONTROUTE|LOGICK|Nesměrovat: odesílat přímo do rozhraní.|
|SO_KEEPALIVE|LOGICK|Odeslání Keep-Alive.|
|SO_LINGER|`struct LINGER`|Zaplatí `Close` v případě, že jsou k dispozici neodesílaná data.|
|SO_OOBINLINE|LOGICK|Příjem dat mimo IP síť v normálním datovém proudu.|
|SO_RCVBUF|**int**|Určete velikost vyrovnávací paměti pro přijetí.|
|SO_REUSEADDR|LOGICK|Povolí vazbu soketu na adresu, která je již používána. (Viz [BIND](#bind).)|
|SO_SNDBUF|**int**|Určete velikost vyrovnávací paměti pro odeslání.|
|TCP_NODELAY|LOGICK|Zakáže Nagle algoritmus pro odesílání slučovacích.|

Možnosti služby Berkeley Software Distribution (BSD) nejsou podporované `SetSockOpt` pro:

|Value|type|Význam|
|-----------|----------|-------------|
|SO_ACCEPTCONN|LOGICK|Soket naslouchá|
|SO_ERROR|**int**|Získejte stav chyby a zrušte zaškrtnutí.|
|SO_RCVLOWAT|**int**|Příjem značky s nízkou vodou.|
|SO_RCVTIMEO|**int**|Časový limit příjmu|
|SO_SNDLOWAT|**int**|Poslat nízkou značku na vodu|
|SO_SNDTIMEO|**int**|Časový limit odeslání|
|SO_TYPE|**int**|Typ soketu.|
|IP_OPTIONS||Nastavte pole možností v hlavičce protokolu IP.|

##  <a name="shutdown"></a>CAsyncSocket:: ShutDown

Voláním této členské funkce zakážete odesílání, přijímání nebo obojí na soketu.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>Parametry

*nHow*<br/>
Příznak popisující, které typy operací již nebudou povoleny, pomocí následujících výčtových hodnot:

- **přijetí = 0**

- **Odeslat = 1**

- **obojí = 2**

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním funkce [GetLastError](#getlasterror). Následující chyby se vztahují na tuto členskou funkci:

- Před použitím tohoto rozhraní API musí dojít k WSANOTINITIALISED úspěšnému [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) .

- WSAENETDOWN implementaci rozhraní Windows Sockets zjistila, že došlo k selhání síťového subsystému.

- WSAEINVAL *Nhow* není platný.

- WSAEINPROGRESS, že probíhá zablokování operace Windows Sockets.

- WSAENOTCONN soket není připojený (jenom SOCK_STREAM).

- WSAENOTSOCK popisovač není soket.

### <a name="remarks"></a>Poznámky

`ShutDown`se používá na všech typech soketů pro zákaz příjmu, přenosu nebo obojího. Pokud je *Nhow* 0, následné přijímání na soketu se nepovolí. To nemá žádný vliv na nižší vrstvy protokolu.

V případě protokolu TCP (Transmission Control Protocol) se okno TCP nemění a příchozí data budou přijata (ale ne potvrzení) až do vyčerpání okna. Pro protokol UDP (User Datagram Protocol) jsou příchozí datagramy přijímány a zařazeny do fronty. V opačném případě se vygeneruje chybový paket ICMP. Pokud je *Nhow* 1, následné odeslání se nepovolí. Pro sokety TCP se pošle FIN. Nastavení *Nhow* na 2 zakáže odesílání i přijímání, jak je popsáno výše.

Všimněte si `ShutDown` , že neukončí zásuvku a prostředky připojené k soketu nebudou uvolněny, dokud se `Close` nespustí. Aplikace by neměla spoléhat na to, že po vypnutí bude možné znovu použít soket. Konkrétně implementace rozhraní Windows Sockets není nutná k podpoře použití `Connect` na takovém soketu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CAsyncSocket:: inreceive](#onreceive).

##  <a name="socket"></a>CASyncSocket:: Socket

Přidělí popisovač soketu.

```
BOOL Socket(
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    int nProtocolType = 0,
    int nAddressFormat = PF_INET);
```

### <a name="parameters"></a>Parametry

*nSocketType*<br/>
Určuje `SOCK_STREAM` nebo `SOCK_DGRAM`.

*lEvent*<br/>
Bitová maska, která určuje kombinaci událostí sítě, ve kterých se aplikace zajímá.

- `FD_READ`: Chcete dostávat oznámení o připravenosti na čtení.

- `FD_WRITE`: Chcete dostávat oznámení o připravenosti na zápis.

- `FD_OOB`: Chcete dostávat oznámení o doručení dat mimo pásmo.

- `FD_ACCEPT`: Chcete dostávat oznámení o příchozích připojeních.

- `FD_CONNECT`: Chcete dostávat oznámení o dokončeném připojení.

- `FD_CLOSE`: Chcete dostávat oznámení o uzavření soketu.

*nProtocolType*<br/>
Protokol, který se má použít u soketu, který je specifický pro určenou rodinu adres.

*nAddressFormat*<br/>
Specifikace rodiny adres.

### <a name="return-value"></a>Návratová hodnota

Při `TRUE` chybě vrátí na `FALSE` úspěch.

### <a name="remarks"></a>Poznámky

Tato metoda přiděluje popisovač soketu. Nevolá [CAsyncSocket:: bind](#bind) k navázání soketu na zadanou adresu, takže je potřeba zavolat `Bind` později, aby se soket navázal na zadanou adresu. Pomocí [CAsyncSocket:: setsockopt](#setsockopt) můžete nastavit možnost soketu před tím, než je svázána.

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CSocket – třída](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
