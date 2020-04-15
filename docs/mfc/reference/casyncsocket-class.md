---
title: Třída CAsyncSocket
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
ms.openlocfilehash: 7ab02dba4bf10b04dddac4e2e954623223af42d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353029"
---
# <a name="casyncsocket-class"></a>Třída CAsyncSocket

Představuje Soket systému Windows — koncový bod síťové komunikace.

## <a name="syntax"></a>Syntaxe

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|Vytvoří `CAsyncSocket` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAsyncSocket::Přijmout](#accept)|Přijme připojení na soketu.|
|[CAsyncSocket::AsyncSelect](#asyncselect)|Požaduje oznámení události pro soket.|
|[CAsyncSocket::Připojit](#attach)|Připojí popisovač soketu k objektu. `CAsyncSocket`|
|[CAsyncSocket::Vazba](#bind)|Přidruží místní adresu ke soketu.|
|[CAsyncSocket::Zavřít](#close)|Zavře zásuvku.|
|[CAsyncSocket::Připojit](#connect)|Naváže připojení k partnerské soketu.|
|[CAsyncSocket::Vytvořit](#create)|Vytvoří soket.|
|[CAsyncSocket::Detach](#detach)|Odpojí popisovač soketu od objektu. `CAsyncSocket`|
|[CAsyncSocket::FromHandle](#fromhandle)|Vrátí ukazatel na `CAsyncSocket` objekt, daný popisovač soketu.|
|[CAsyncSocket::GetLastError](#getlasterror)|Získá stav chyby pro poslední operaci, která se nezdařila.|
|[CAsyncSocket::GetPeerName](#getpeername)|Získá adresu partnera soketu, ke kterému je připojen soket.|
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Získá adresu partnera soketu, ke kterému je připojen (zpracovává adresy IPv6).|
|[CAsyncSocket::GetSockName](#getsockname)|Získá místní název soketu.|
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Získá místní název soketu (zpracovává adresy IPv6).|
|[CAsyncSocket::GetSockOpt](#getsockopt)|Načte možnost soketu.|
|[CAsyncSocket::IOCtl](#ioctl)|Řídí režim zásuvky.|
|[CAsyncSocket::Naslouchání](#listen)|Vytvoří soket pro naslouchání příchozím požadavkům na připojení.|
|[CAsyncSocket::Příjem](#receive)|Přijímá data ze soketu.|
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Přijme datagram a uloží zdrojovou adresu.|
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Přijme datagram a uloží zdrojovou adresu (zpracovává adresy IPv6).|
|[CAsyncSocket::Odeslat](#send)|Odešle data do připojeného soketu.|
|[CAsyncSocket::SendTo](#sendto)|Odešle data do určitého cíle.|
|[CAsyncSocket::SendToex](#sendtoex)|Odešle data do určitého cíle (zpracovává adresy IPv6).|
|[CAsyncSocket::SetSockOpt](#setsockopt)|Nastaví možnost soketu.|
|[CAsyncSocket::Vypnutí](#shutdown)|Zakáže `Send` a/nebo `Receive` zavolá na soketu.|
|[CASyncSocket::Soket](#socket)|Přiděluje popisovač soketu.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAsyncSocket::OnAccept](#onaccept)|Upozorní naslouchání soketu, který může přijímat `Accept`čekající požadavky na připojení voláním .|
|[CAsyncSocket::OnClose](#onclose)|Upozorní soketu, že zásuvka, která je k němu připojena, byla uzavřena.|
|[CAsyncSocket::OnConnect](#onconnect)|Upozorní připojení soketu, že pokus o připojení je dokončen, ať už úspěšně nebo omylem.|
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Upozorní přijímající soket, že je out-of-band data ke čtení na soketu, obvykle naléhavou zprávu.|
|[CAsyncSocket::OnReceive](#onreceive)|Upozorní naslouchání soketu, že je data, `Receive`která mají být načteny voláním .|
|[CAsyncSocket::OnSend](#onsend)|Upozorní soketu, že může odesílat data voláním `Send`.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAsyncSocket::operátor =](#operator_eq)|Přiřadí objektu novou `CAsyncSocket` hodnotu.|
|[CAsyncSocket::OPERÁTOR SOCKET](#operator_socket)|Tento operátor slouží k načtení `CAsyncSocket` popisovače SOCKET objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CAsyncSocket::m_hSocket](#m_hsocket)|Označuje popisovač SOCKET připojený `CAsyncSocket` k tomuto objektu.|

## <a name="remarks"></a>Poznámky

Třída `CAsyncSocket` zapouzdřuje rozhraní API funkce soketu systému Windows a poskytuje objektově orientovanou abstrakcí pro programátory, kteří chtějí používat rozhraní Windows Sockets ve spojení s knihovnou MFC.

Tato třída je založena na předpokladu, že rozumíte síťové komunikaci. Jste zodpovědní za zpracování blokování, rozdíly pořadí bajtů a převody mezi unicode a vícebajtové znakové sady (MBCS) řetězce. Pokud chcete pohodlnější rozhraní, které spravuje tyto problémy za vás, naleznete v tématu třídy [CSocket](../../mfc/reference/csocket-class.md).

Chcete-li `CAsyncSocket` použít objekt, zavolejte jeho konstruktor, pak volání [Vytvořit](#create) funkce k vytvoření základní hostož (typ `SOCKET`), s výjimkou přijatých soketů. Pro server soketu volání [Listen](#listen) členské funkce a pro klienta soket volání [připojit](#connect) členskou funkci. Server soket by měl volat [Accept](#accept) funkce po obdržení požadavku na připojení. Zbývající `CAsyncSocket` funkce použijte k provádění komunikace mezi zásuvkami. Po dokončení zničte `CAsyncSocket` objekt, pokud byl vytvořen na haldě; destruktor automaticky zavolá funkci [Zavřít.](#close) Datový typ SOCKET je popsán v článku [Windows Sockets: Background](../../mfc/windows-sockets-background.md).

> [!NOTE]
> Při použití soketů knihovny MFC v sekundárních vláknech `AfxSocketInit` v staticky propojené aplikaci knihovny MFC je nutné volat v každém vlákně, které používá sokety k inicializaci knihoven soketu. Ve výchozím `AfxSocketInit` nastavení se nazývá pouze v primárním vlákně.

Další informace naleznete [v tématu Windows Sockets: Using Class CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) and related articles., as well as [as Windows Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxsock.h

## <a name="casyncsocketaccept"></a><a name="accept"></a>CAsyncSocket::Přijmout

Volání této členské funkce přijmout připojení na soketu.

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
Ukazatel na strukturu [SOCKADDR,](/windows/win32/winsock/sockaddr-2) která přijímá adresu připojovacího soketu, jak je známo v síti. Přesný formát *argumentu lpSockAddr* je určen rodinou adres vytvořenou při vytvoření soketu. Pokud *lpSockAddr* a/nebo *lpSockAddrLen* se rovnají HODNOTĚ NULL, nebudou vráceny žádné informace o vzdálené adrese přijatého soketu.

*lpSockAddrLen*<br/>
Ukazatel na délku adresy v *lpSockAddr* v bajtů. *LpSockAddrLen* je parametr value-result: měl by zpočátku obsahovat množství místa, na které poukazuje *lpSockAddr*; při vrácení bude obsahovat skutečnou délku (v bajtů) vrácené adresy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEFAULT Argument *lpSockAddrLen* je příliš malý (menší než velikost struktury [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINPROGRESS Probíhá blokování volání zásuvek systému Windows.

- WSAEINVAL `Listen` nebyl vyvolán před přijetím.

- WSAEMFILE Fronta je při vstupu prázdná a nejsou k dispozici žádné popisovače.

- WSAENOBUFS Není k dispozici žádné vyrovnávací místo.

- WSAENOTSOCK Popisovač není soket.

- WSAEOPNOTSUPP Odkazovaný soket není typ, který podporuje službu orientovanou na připojení.

- WSAEWOULDBLOCK Soket je označen jako neblokující a nejsou k dispozici žádná připojení, která by byla přijata.

### <a name="remarks"></a>Poznámky

Tato rutina extrahuje první připojení ve frontě čekající připojení, vytvoří nový soket se stejnými vlastnostmi jako tento soket a připojí jej k *rConnectedSocket*. Pokud ve frontě nejsou žádná `Accept` čekající `GetLastError` připojení, vrátí nulu a vrátí chybu. Přijatý soket *(rConnectedSocket)* nelze použít k přijetí více připojení. Původní soket zůstane otevřený a naslouchání.

Argument *lpSockAddr* je výsledek parametr, který je vyplněn s adresou připojení soketu, jak je známo komunikační vrstvy. `Accept`se používá s typy soketů založených na připojení, jako je SOCK_STREAM.

## <a name="casyncsocketasyncselect"></a><a name="asyncselect"></a>CAsyncSocket::AsyncSelect

Volání této členské funkce požádat o oznámení události pro soket.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parametry

*lUdálost*<br/>
Bitová maska, která určuje kombinaci síťových událostí, o které má aplikace zájem.

- FD_READ Chcete dostávat oznámení o připravenosti ke čtení.

- FD_WRITE Chcete dostávat oznámení, když jsou data k dispozici ke čtení.

- FD_OOB Chcete dostávat oznámení o příchodu nepásových dat.

- FD_ACCEPT Chcete dostávat oznámení o příchozích připojeních.

- FD_CONNECT Chcete dostávat oznámení o výsledcích připojení.

- FD_CLOSE Chcete dostávat oznámení, pokud byl soket uzavřen druhou stranou.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEINVAL Označuje, že jeden ze zadaných parametrů byl neplatný.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k určení, které funkce oznámení zpětného volání knihovny MFC budou volány pro soket. `AsyncSelect`automaticky nastaví tuto zásuvku do neblokovacího režimu. Další informace naleznete v článku [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketattach"></a><a name="attach"></a>CAsyncSocket::Připojit

Volání této členské funkce připojit *hSocket* popisovač objektu. `CAsyncSocket`

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Obsahuje popisovač do soketu.

*lUdálost*<br/>
Bitová maska, která určuje kombinaci síťových událostí, o které má aplikace zájem.

- FD_READ Chcete dostávat oznámení o připravenosti ke čtení.

- FD_WRITE Chcete dostávat oznámení, když jsou data k dispozici ke čtení.

- FD_OOB Chcete dostávat oznámení o příchodu nepásových dat.

- FD_ACCEPT Chcete dostávat oznámení o příchozích připojeních.

- FD_CONNECT Chcete dostávat oznámení o výsledcích připojení.

- FD_CLOSE Chcete dostávat oznámení, pokud byl soket uzavřen druhou stranou.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná.

### <a name="remarks"></a>Poznámky

Popisovač SOCKET je uložen v [datovém](#m_hsocket) členu m_hSocket objektu.

## <a name="casyncsocketbind"></a><a name="bind"></a>CAsyncSocket::Vazba

Volání této členské funkce přidružit místní adresu soketu.

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
Síťová adresa, tečkované číslo, například "128.56.22.8". Předání řetězce NULL pro tento `CAsyncSocket` parametr znamená, že instance by měla naslouchat aktivitě klienta ve všech síťových rozhraních.

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR,](/windows/win32/winsock/sockaddr-2) která obsahuje adresu přiřadit k tomuto soketu.

*nSockAddrLen*<br/>
Délka adresy v *lpSockAddr* v bajtů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Následující seznam obsahuje několik chyb, které mohou být vráceny. Úplný seznam naleznete v tématu [Chybové kódy zásuvek systému Windows](/windows/win32/winsock/windows-sockets-error-codes-2).

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEADDRINUSE Zadaná adresa je již používána. (Viz možnost SO_REUSEADDR soketu v části [SetSockOpt](#setsockopt).)

- WSAEFAULT Argument *nSockAddrLen* je příliš malý (menší než velikost struktury [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINPROGRESS Probíhá blokování volání zásuvek systému Windows.

- WSAEAFNOSUPPORT Zadaná rodina adres není tímto portem podporována.

- WSAEINVAL Soket je již vázán na adresu.

- WSAENOBUFS Není k dispozici dostatek vyrovnávacích pamětí, příliš mnoho připojení.

- WSAENOTSOCK Popisovač není soket.

### <a name="remarks"></a>Poznámky

Tato rutina se používá na nepřipojené datagram `Connect` `Listen` nebo soketu datového proudu, před následnými nebo volání. Před přijetím požadavků na připojení musí odposlouchávací server vybrat číslo portu `Bind`a zpřístupnit jej službě Windows Sockets voláním . `Bind`vytvoří místní přidružení (číslo adresy hostitele/portu) soketu přiřazením místního názvu nepojmenovanému soketu.

## <a name="casyncsocketcasyncsocket"></a><a name="casyncsocket"></a>CAsyncSocket::CAsyncSocket

Vytvoří prázdný objekt soketu.

```
CAsyncSocket();
```

### <a name="remarks"></a>Poznámky

Po vytvoření objektu je nutné `Create` volat jeho člennou funkci k vytvoření datové struktury SOCKET a svázání její adresy. (Na straně serveru komunikace Windows Sockets při naslouchání soketu `Accept` vytvoří soket `Create` pro použití v volání, není volání pro tento soket.)

## <a name="casyncsocketclose"></a><a name="close"></a>CAsyncSocket::Zavřít

Zavře zásuvku.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Tato funkce uvolní popisovač soketu tak, aby další odkazy na něj se nezdaří s chybou WSAENOTSOCK. Pokud se jedná o poslední odkaz na podkladový soket, jsou zahozeny přidružené informace o pojmenování a data ve frontě. Destruktor objektu soketu vás volá. `Close`

Pro `CAsyncSocket`, ale `CSocket`ne pro , `Close` sémantiku jsou ovlivněny možnosti soketu SO_LINGER a SO_DONTLINGER. Další informace naleznete v `GetSockOpt`tématu členská funkce .

## <a name="casyncsocketconnect"></a><a name="connect"></a>CAsyncSocket::Připojit

Volání této členské funkce k navázání připojení k nepřipojenému datovému proudu nebo soketu datagramu.

```
BOOL Connect(
    LPCTSTR lpszHostAddress,
    UINT nHostPort);

BOOL Connect(
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>Parametry

*lpszHostAdresa*<br/>
Síťová adresa soketu, ke kterému je tento objekt připojen: název počítače, například "ftp.microsoft.com", nebo tečkované číslo, například "128.56.22.8".

*nHostPort*<br/>
Port identifikující aplikaci soketu.

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR,](/windows/win32/winsock/sockaddr-2) která obsahuje adresu připojeného soketu.

*nSockAddrLen*<br/>
Délka adresy v *lpSockAddr* v bajtů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pokud to znamená kód chyby WSAEWOULDBLOCK a aplikace používá overridable zpětná volání, aplikace obdrží zprávu `OnConnect` po dokončení operace připojení. Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEADDRINUSE Zadaná adresa je již používána.

- WSAEINPROGRESS Probíhá blokování volání zásuvek systému Windows.

- WSAEADDRNOTAVAIL Zadaná adresa není k dispozici z místního počítače.

- S tímto soketem nelze použít adresy WSAEAFNOSUPPORT v zadané rodině.

- WSAECONNREFUSED Pokus o připojení byl odmítnut.

- WSAEDESTADDRREQ Je vyžadována cílová adresa.

- WSAEFAULT Argument *nSockAddrLen* je nesprávný.

- WSAEINVAL Neplatná adresa hostitele.

- WSAEISCONN Soket je již připojen.

- WSAEMFILE Nejsou k dispozici žádné další popisovače souborů.

- WSAENETUNREACH V tuto chvíli není z tohoto hostitele dosaženo.

- WSAENOBUFS Není k dispozici žádné vyrovnávací místo. Soket nelze připojit.

- WSAENOTSOCK Popisovač není soket.

- WSAETIMEDOUT Pokus o připojení vypršel bez navázání připojení.

- WSAEWOULDBLOCK Soket je označen jako neblokující a připojení nelze dokončit okamžitě.

### <a name="remarks"></a>Poznámky

Pokud je soket nevázaný, jsou systémem přiřazeny k místnímu přidružení jedinečné hodnoty a soket je označen jako vázaný. Všimněte si, že pokud je pole adresy `Connect` struktury názvů všechny nuly, vrátí nulu. Chcete-li získat rozšířené `GetLastError` informace o chybě, zavolejte členní funkci.

U soketů datového proudu (typ SOCK_STREAM) je inicializováno aktivní připojení k cizímu hostiteli. Po úspěšném dokončení volání soketu je soket připraven k odesílání a přijímání dat.

Pro soket datagramu (typ SOCK_DGRAM) je nastaven výchozí `Send` `Receive` cíl, který bude použit při následných voláních a voláních.

## <a name="casyncsocketcreate"></a><a name="create"></a>CAsyncSocket::Vytvořit

Volání `Create` členské funkce po vytvoření objektu soketu k vytvoření soketu systému Windows a připojení.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Známý port, který má být použit se soketem, nebo 0, pokud chcete, aby aplikace Windows Sockets vyberte port.

*nTyp socket*<br/>
SOCK_STREAM nebo SOCK_DGRAM.

*lUdálost*<br/>
Bitová maska, která určuje kombinaci síťových událostí, o které má aplikace zájem.

- FD_READ Chcete dostávat oznámení o připravenosti ke čtení.

- FD_WRITE Chcete dostávat oznámení o připravenosti k zápisu.

- FD_OOB Chcete dostávat oznámení o příchodu nepásových dat.

- FD_ACCEPT Chcete dostávat oznámení o příchozích připojeních.

- FD_CONNECT Chcete dostávat oznámení o dokončeném připojení.

- FD_CLOSE Chcete dostávat oznámení o uzavření soketu.

*lpszSockAdresa*<br/>
Ukazatel na řetězec obsahující síťovou adresu připojeného soketu, tečkované číslo, například "128.56.22.8". Předání řetězce NULL pro tento `CAsyncSocket` parametr znamená, že instance by měla naslouchat aktivitě klienta ve všech síťových rozhraních.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEAFNOSUPPORT Zadaná rodina adres není podporována.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAEMFILE Nejsou k dispozici žádné další popisovače souborů.

- WSAENOBUFS Není k dispozici žádné vyrovnávací místo. Soket nelze vytvořit.

- WSAEPROTONOSUPPORT Zadaný port není podporován.

- WSAEPROTOTYPE Zadaný port je pro tento soket nesprávný typ.

- WSAESOCKTNOSUPPORT Zadaný typ soketu není v této rodině adres podporován.

### <a name="remarks"></a>Poznámky

`Create`volá [Socket](#socket) a v případě úspěchu volá [Bind](#bind) svázat soket na zadanou adresu. Podporovány jsou následující typy soketů:

- SOCK_STREAM Poskytuje sekvenční, spolehlivé, plně duplexní bajtové datové proudy založené na připojení. Používá protokol TCP (Transmission Control Protocol) pro rodinu internetových adres.

- SOCK_DGRAM Podporuje datové gramy, což jsou nespolehlivé pakety bez připojení s pevnou (obvykle malou) maximální délkou. Používá protokol UDP (User Datagram Protocol) pro rodinu internetových adres.

    > [!NOTE]
    >  Členská `Accept` funkce přebírá jako svůj `CSocket` parametr odkaz na nový prázdný objekt. Tento objekt je nutné `Accept`vytvořit před voláním . Mějte na paměti, že pokud tento objekt soketu přejde mimo rozsah, připojení se zavře. Nevolejte `Create` tento nový objekt soketu.

> [!IMPORTANT]
> `Create`**není** bezpečný pro přístup z více vláken.  Pokud jej voláte v prostředí s více vlákny, kde by mohla být vyvolána současně různými vlákny, nezapomeňte chránit každé volání pomocí objektu mutex nebo jiného zámku synchronizace.

Další informace o soketech datových proudů a datových gramů naleznete v článcích [Rozhraní Windows Sockets: Background](../../mfc/windows-sockets-background.md) and Windows [Sockets: Ports and Socket Addresses](../../mfc/windows-sockets-ports-and-socket-addresses.md) and [Windows Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="casyncsocketdetach"></a><a name="detach"></a>CAsyncSocket::Detach

Volání této členské funkce odpojit *m_hSocket* popisovač SOCKET `CAsyncSocket` v m_hSocket datový člen z objektu a nastavte *m_hSocket* na hodnotu NULL.

```
SOCKET Detach();
```

## <a name="casyncsocketfromhandle"></a><a name="fromhandle"></a>CAsyncSocket::FromHandle

Vrátí ukazatel na `CAsyncSocket` objekt.

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Obsahuje popisovač do soketu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CAsyncSocket` objekt nebo NULL, pokud `CAsyncSocket` není připojen žádný objekt *hSocket*.

### <a name="remarks"></a>Poznámky

Pokud je k popisovaču `CAsyncSocket` přidělen popisovač SOCKET, členská funkce vrátí hodnotu NULL.

## <a name="casyncsocketgetlasterror"></a><a name="getlasterror"></a>CAsyncSocket::GetLastError

Volání této členské funkce získat stav chyby pro poslední operaci, která se nezdařila.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota označuje kód chyby pro poslední rutinu rozhraní API rozhraní Windows Sockets, kterou provádí toto vlákno.

### <a name="remarks"></a>Poznámky

Pokud určitá členská funkce označuje, `GetLastError` že došlo k chybě, by měla být volána k načtení příslušného kódu chyby. Seznam příslušných kódů chyb naleznete v popisech jednotlivých členských funkcí.

Další informace o kódech chyb naleznete v tématu [Rozhraní API rozhraní Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="casyncsocketgetpeername"></a><a name="getpeername"></a>CAsyncSocket::GetPeerName

Volání této členské funkce získat adresu peer socket, ke kterému je připojen tento soket.

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);

BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Parametry

*rAdresa peer*<br/>
Odkaz na `CString` objekt, který obdrží tečkovanou adresu IP čísla.

*rPeerPort*<br/>
Odkaz na UINT, který ukládá port.

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR,](/windows/win32/winsock/sockaddr-2) která přijímá název partnera soketu.

*lpSockAddrLen*<br/>
Ukazatel na délku adresy v *lpSockAddr* v bajtů. Při návratu *argument lpSockAddrLen* obsahuje skutečnou velikost *lpSockAddr* vrácené v bajtů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEFAULT Argument *lpSockAddrLen* není dostatečně velký.

- WSAEINPROGRESS Probíhá blokování volání zásuvek systému Windows.

- WSAENOTCONN Soket není připojen.

- WSAENOTSOCK Popisovač není soket.

### <a name="remarks"></a>Poznámky

Chcete-li zpracovat adresy IPv6, použijte [CAsyncSocket::GetPeerNameEx](#getpeernameex).

## <a name="casyncsocketgetpeernameex"></a><a name="getpeernameex"></a>CAsyncSocket::GetPeerNameEx

Volání této členské funkce získat adresu peer socket, ke kterému je připojen tento soket (zpracovává adresy IPv6).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>Parametry

*rAdresa peer*<br/>
Odkaz na `CString` objekt, který obdrží tečkovanou adresu IP čísla.

*rPeerPort*<br/>
Odkaz na UINT, který ukládá port.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEFAULT Argument *lpSockAddrLen* není dostatečně velký.

- WSAEINPROGRESS Probíhá blokování volání zásuvek systému Windows.

- WSAENOTCONN Soket není připojen.

- WSAENOTSOCK Popisovač není soket.

### <a name="remarks"></a>Poznámky

Tato funkce je stejná jako [CAsyncSocket::GetPeerName](#getpeername) s tím rozdílem, že zpracovává adresy IPv6, stejně jako starší protokoly.

## <a name="casyncsocketgetsockname"></a><a name="getsockname"></a>CAsyncSocket::GetSockName

Volání této členské funkce získat místní název soketu.

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
Odkaz na `CString` objekt, který obdrží tečkovanou adresu IP čísla.

*rSocketPort*<br/>
Odkaz na UINT, který ukládá port.

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR,](/windows/win32/winsock/sockaddr-2) která přijímá adresu soketu.

*lpSockAddrLen*<br/>
Ukazatel na délku adresy v *lpSockAddr* v bajtů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEFAULT Argument *lpSockAddrLen* není dostatečně velký.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAENOTSOCK Popisovač není soket.

- WSAEINVAL Soket nebyl vázán na `Bind`adresu s .

### <a name="remarks"></a>Poznámky

Toto volání je `Connect` užitečné zejména v případě, že bylo provedeno volání bez provedení `Bind` první; Toto volání poskytuje jediný způsob, kterým můžete určit místní přidružení, které bylo nastaveno systémem.

Pro zpracování adres IPv6 použijte [CAsyncSocket::GetSockNameEx](#getsocknameex)

## <a name="casyncsocketgetsocknameex"></a><a name="getsocknameex"></a>CAsyncSocket::GetSockNameEx

Volání této členské funkce získat místní název soketu (zpracovává adresy IPv6).

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>Parametry

*rSocketAddress*<br/>
Odkaz na `CString` objekt, který obdrží tečkovanou adresu IP čísla.

*rSocketPort*<br/>
Odkaz na UINT, který ukládá port.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEFAULT Argument *lpSockAddrLen* není dostatečně velký.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAENOTSOCK Popisovač není soket.

- WSAEINVAL Soket nebyl vázán na `Bind`adresu s .

### <a name="remarks"></a>Poznámky

Toto volání je stejné jako [CAsyncSocket::GetSockName](#getsockname) s tím rozdílem, že zpracovává adresy IPv6, stejně jako starší protokoly.

Toto volání je `Connect` užitečné zejména v případě, že bylo provedeno volání bez provedení `Bind` první; Toto volání poskytuje jediný způsob, kterým můžete určit místní přidružení, které bylo nastaveno systémem.

## <a name="casyncsocketgetsockopt"></a><a name="getsockopt"></a>CAsyncSocket::GetSockOpt

Volání této členské funkce načíst možnost soketu.

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Parametry

*nNázev_opčních_*<br/>
Možnost soketu, pro kterou má být načtena hodnota.

*hodnota lpOption*<br/>
Ukazatel na vyrovnávací paměť, ve kterém má být vrácena hodnota pro požadovanou možnost. Hodnota přidružená k vybrané možnosti je vrácena ve vyrovnávací paměti *lpOptionValue*. Celé číslo, na které je uvedeno *lpOptionLen,* by mělo původně obsahovat velikost této vyrovnávací paměti v bajtů; a po návratu bude nastavena na velikost vrácené hodnoty. Pro SO_LINGER to bude velikost `LINGER` struktury; pro všechny ostatní možnosti to bude velikost BOOL nebo **int**, v závislosti na možnosti. Podívejte se na seznam možností a jejich velikosti v části Poznámky.

*lpOptionLen*<br/>
Ukazatel na velikost vyrovnávací paměti *lpOptionValue* v bajtech.

*nÚroveň*<br/>
Úroveň, na které je definována možnost; jediné podporované úrovně jsou SOL_SOCKET a IPPROTO_TCP.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pokud možnost nebyla `SetSockOpt`nikdy `GetSockOpt` nastavena s , vrátí výchozí hodnotu pro tuto možnost. Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEFAULT Argument *lpOptionLen* byl neplatný.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAENOPROTOOPT Možnost není známa nebo není podporována. Zejména SO_BROADCAST není podporována na sokety typu SOCK_STREAM, zatímco SO_ACCEPTCONN, SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER a SO_OOBINLINE nejsou podporovány na sokecích typu SOCK_DGRAM.

- WSAENOTSOCK Popisovač není soket.

### <a name="remarks"></a>Poznámky

`GetSockOpt`načte aktuální hodnotu pro možnost soketu přidruženou k soketu libovolného typu v libovolném stavu a uloží výsledek do *lpOptionValue*. Možnosti ovlivňují operace soketu, jako je například směrování paketů, nepásmový přenos dat a tak dále.

Následující možnosti jsou `GetSockOpt`podporovány pro . Typ identifikuje typ dat adresovaných *lpOptionValue*. Možnost TCP_NODELAY používá úroveň IPPROTO_TCP; všechny ostatní možnosti používají úroveň SOL_SOCKET.

|Hodnota|Typ|Význam|
|-----------|----------|-------------|
|SO_ACCEPTCONN|Bool|Socket poslouchá.|
|SO_BROADCAST|Bool|Socket je nakonfigurován pro přenos všesměrových zpráv.|
|SO_DEBUG|Bool|Ladění je povoleno.|
|SO_DONTLINGER|Bool|Pokud true, možnost SO_LINGER je zakázána.|
|SO_DONTROUTE|Bool|Směrování je zakázáno.|
|SO_ERROR|**int**|Načíst stav chyby a vymazat.|
|SO_KEEPALIVE|Bool|Jsou posílány životy.|
|SO_LINGER|`struct LINGER`|Vrátí aktuální možnosti prodlévání.|
|SO_OOBINLINE|Bool|V normálním datovém proudu jsou přijímána nepásmová data.|
|SO_RCVBUF|int|Velikost vyrovnávací paměti pro příjem.|
|SO_REUSEADDR|Bool|Soket může být vázán na adresu, která je již používána.|
|SO_SNDBUF|**int**|Velikost vyrovnávací paměti pro odeslání.|
|SO_TYPE|**int**|Typ soketu (například SOCK_STREAM).|
|TCP_NODELAY|Bool|Zakáže algoritmus Nagle pro odesílání slučování.|

Možnosti distribuce softwaru Berkeley (BSD), pro které nejsou podporovány, `GetSockOpt` jsou:

|Hodnota|Typ|Význam|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|Získejte značku s nízkou hladinou vody.|
|SO_RCVTIMEO|**int**|Příjem časového času.|
|SO_SNDLOWAT|**int**|Pošlete značku s nízkou hladinou vody.|
|SO_SNDTIMEO|**int**|Odeslat časový čas.|
|IP_OPTIONS||Získejte možnosti v záhlaví IP.|
|TCP_MAXSEG|**int**|Získejte maximální velikost segmentu protokolu TCP.|

Volání `GetSockOpt` s nepodporovanou možností bude mít za následek vrácení kódu chyby wsaenoprotoopt z `GetLastError`.

## <a name="casyncsocketioctl"></a><a name="ioctl"></a>CAsyncSocket::IOCtl

Volání této členské funkce k řízení režimu soketu.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>Parametry

*lCommand*<br/>
Příkaz, který má být v soketu.

*lpArgument*<br/>
Ukazatel na parametr pro *lCommand*.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEINVAL *lCommand* není platný příkaz nebo *lpArgument* není přijatelný parametr pro *lCommand*nebo příkaz není použitelný pro typ dodaného soketu.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAENOTSOCK Popisovač není soket.

### <a name="remarks"></a>Poznámky

Tuto rutinu lze použít na libovolném soketu v libovolném stavu. Používá se k získání nebo načtení provozních parametrů spojených se soketem, nezávisle na protokolu a komunikačním subsystému. Podporovány jsou následující příkazy:

- FIONBIO Povolit nebo zakázat neblokovací režim na soketu. Parametr *lpArgument* ukazuje `DWORD`na , což je nenulová, pokud má být povolen neblokovací režim, a nula, pokud má být zakázán. Pokud `AsyncSelect` byl vydán na soketu, pak `IOCtl` jakýkoli pokus o nastavení soketu zpět do režimu blokování se nezdaří s WSAEINVAL. Chcete-li nastavit soket zpět do režimu blokování a zabránit chybě `AsyncSelect` WSAEINVAL, musí aplikace nejprve zakázat voláním `AsyncSelect` s parametrem *lEvent* rovným 0 a potom voláním `IOCtl`.

- FIONREAD Určete maximální počet bajtů, které `Receive` lze číst pomocí jednoho volání z tohoto soketu. Parametr *lpArgument* ukazuje `DWORD` na, `IOCtl` ve kterém ukládá výsledek. Pokud je tento soket typu typu SOCK_STREAM, funkce FIONREAD vrátí `Receive`celkové množství dat, která lze číst v jednom ; Obvykle je to stejné jako celkové množství dat zařazených do fronty na soketu. Pokud je tento soket typu typu SOCK_DGRAM, funkce FIONREAD vrátí velikost prvního datagramu zařazeného do fronty na soketu.

- SIOCATMARK Zjistěte, zda byla přečtena všechna data mimo pásmo. To platí pouze pro soket typu SOCK_STREAM který byl nakonfigurován pro in-line příjem všech nepásových dat (SO_OOBINLINE). Pokud žádná data mimo pásmo čeká na čtení, operace vrátí nenulovou hodnotu. V opačném případě vrátí `Receive` 0 `ReceiveFrom` a další nebo provedené na soketu načte některá nebo všechna data předcházející "značka"; aplikace by měla použít operaci SIOCATMARK k určení, zda zůstanou nějaká data. Pokud existují normální data předcházející "naléhavé" (out-of-band) data, budou přijata v pořádku. (Všimněte `Receive` si, že nebo `ReceiveFrom` nikdy nebude kombinovat out-of-band a normální data ve stejném volání.) Parametr *lpArgument* ukazuje `DWORD` na, `IOCtl` ve kterém ukládá výsledek.

Tato funkce je podmnožinou, `ioctl()` která se používá v soketech Berkeley. Zejména neexistuje žádný příkaz, který je ekvivalentní FIOASYNC, zatímco SIOCATMARK je jediný příkaz na úrovni soketu, který je podporován.

## <a name="casyncsocketlisten"></a><a name="listen"></a>CAsyncSocket::Naslouchání

Volání této členské funkce naslouchat příchozí žádosti o připojení.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>Parametry

*nConnectionBacklog*<br/>
Maximální délka, na kterou může zvětšovat fronty čekající připojení. Platný rozsah je od 1 do 5.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEADDRINUSE Byl proveden pokus o naslouchání na uvolňovanou adresu.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAEINVAL Soket nebyl `Bind` svázán nebo je již připojen.

- WSAEISCONN Soket je již připojen.

- WSAEMFILE Nejsou k dispozici žádné další popisovače souborů.

- WSAENOBUFS Není k dispozici žádné vyrovnávací místo.

- WSAENOTSOCK Popisovač není soket.

- WSAEOPNOTSUPP Odkazovaný soket není typu, `Listen` který operaci podporuje.

### <a name="remarks"></a>Poznámky

Chcete-li přijmout připojení, soket je nejprve vytvořen `Create`pomocí `Listen`, nevyřízené položky `Accept`pro příchozí připojení je určen s a potom jsou přijaty připojení s . `Listen`platí pouze pro sokety, které podporují připojení, to znamená, že typ SOCK_STREAM. Tento soket je uveden do "pasivního" režimu, kde jsou příchozí připojení potvrzena a zařazena do fronty čekající na přijetí procesem.

Tato funkce je obvykle používána servery (nebo jakoukoli aplikací, která chce přijímat připojení), které mohou mít více než jeden požadavek na připojení najednou: pokud požadavek na připojení dorazí s plnou frontou, klient obdrží chybu s označením WSAECONNREFUSED.

`Listen`pokusí i nadále fungovat racionálně, pokud nejsou k dispozici žádné porty (popisovače). Bude přijímat připojení, dokud není fronta vyprázdněna. Pokud budou k dispozici porty, později `Listen` volání nebo `Accept` doplnění fronty na aktuální nebo poslední "nevyřízené položky", pokud je to možné, a pokračovat v naslouchání pro příchozí připojení.

## <a name="casyncsocketm_hsocket"></a><a name="m_hsocket"></a>CAsyncSocket::m_hSocket

Obsahuje popisovač SOCKET pro soket `CAsyncSocket` zapouzdřený tímto objektem.

```
SOCKET m_hSocket;
```

## <a name="casyncsocketonaccept"></a><a name="onaccept"></a>CAsyncSocket::OnAccept

Volat rámci upozornit naslouchání soketu, že může přijímat čekající požadavky na připojení voláním [Přijmout](#accept) členské funkce.

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorKód*<br/>
Poslední chyba v soketu. Pro členní `OnAccept` funkci platí následující kódy chyb:

- **0** Funkce byla úspěšně provedena.

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonclose"></a><a name="onclose"></a>CAsyncSocket::OnClose

Volat rámci upozornit tento soket, že připojený soket je uzavřen jeho procesem.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorKód*<br/>
Poslední chyba v soketu. Pro členní funkci `OnClose` platí následující kódy chyb:

- **0** Funkce byla úspěšně provedena.

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAECONNRESET Připojení bylo resetováno vzdálenou stranou.

- WSAECONNABORTED Připojení bylo přerušeno z důvodu časového limitu nebo jiného selhání.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonconnect"></a><a name="onconnect"></a>CAsyncSocket::OnConnect

Volat rámci upozornit tento připojení soketu, že jeho pokus o připojení je dokončena, ať už úspěšně nebo omylem.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorKód*<br/>
Poslední chyba v soketu. Pro členní funkci `OnConnect` platí následující kódy chyb:

- **0** Funkce byla úspěšně provedena.

- WSAEADDRINUSE Zadaná adresa je již používána.

- WSAEADDRNOTAVAIL Zadaná adresa není k dispozici z místního počítače.

- S tímto soketem nelze použít adresy WSAEAFNOSUPPORT v zadané rodině.

- WSAECONNREFUSED Pokus o připojení byl důrazně odmítnut.

- WSAEDESTADDRREQ Je vyžadována cílová adresa.

- WSAEFAULT Argument *lpSockAddrLen* je nesprávný.

- WSAEINVAL Soket je již vázán na adresu.

- WSAEISCONN Soket je již připojen.

- WSAEMFILE Nejsou k dispozici žádné další popisovače souborů.

- WSAENETUNREACH V tuto chvíli není z tohoto hostitele dosaženo.

- WSAENOBUFS Není k dispozici žádné vyrovnávací místo. Soket nelze připojit.

- WSAENOTCONN Soket není připojen.

- WSAENOTSOCK Popisovač je soubor, nikoli soket.

- WSAETIMEDOUT Pokus o připojení vypršel bez navázání připojení.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> V [CSocket](../../mfc/reference/csocket-class.md) `OnConnect` , funkce oznámení je nikdy volána. Pro připojení jednoduše `Connect`zavoláte , který se vrátí po dokončení připojení (úspěšně nebo omylem). Způsob zpracování oznámení o připojení je podrobnosti implementace knihovny MFC.

Další informace naleznete v tématu [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

## <a name="casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a>CAsyncSocket::OnOutOfBandData

Volat rámci upozornit přijímající soket, že odesílání soketu má out-of-band data k odeslání.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorKód*<br/>
Poslední chyba v soketu. Pro členní funkci `OnOutOfBandData` platí následující kódy chyb:

- **0** Funkce byla úspěšně provedena.

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

### <a name="remarks"></a>Poznámky

Nepásmová data jsou logicky nezávislý kanál, který je přidružen ke každé dvojici připojených soketů typu SOCK_STREAM. Kanál se obecně používá k odesílání naléhavých dat.

Knihovna MFC podporuje nepásmová data, `CAsyncSocket` ale uživatelé třídy se nedoporučuje používat. Jednodušší způsob je vytvořit druhý soket pro předávání těchto dat. Další informace o nepásových datech naleznete v tématu [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonreceive"></a><a name="onreceive"></a>CAsyncSocket::OnReceive

Volat rámci upozornit tento soket, že jsou data ve vyrovnávací `Receive` paměti, které lze načíst voláním členské funkce.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorKód*<br/>
Poslední chyba v soketu. Pro členní funkci `OnReceive` platí následující kódy chyb:

- **0** Funkce byla úspěšně provedena.

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

## <a name="casyncsocketonsend"></a><a name="onsend"></a>CAsyncSocket::OnSend

Volat rámci upozornit soketu, že nyní můžete `Send` odesílat data voláním členské funkce.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorKód*<br/>
Poslední chyba v soketu. Pro členní funkci `OnSend` platí následující kódy chyb:

- **0** Funkce byla úspěšně provedena.

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

## <a name="casyncsocketoperator-"></a><a name="operator_eq"></a>CAsyncSocket::operátor =

Přiřadí objektu novou `CAsyncSocket` hodnotu.

```
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odkaz na existující `CAsyncSocket` objekt.

### <a name="remarks"></a>Poznámky

Volání této funkce zkopírovat `CAsyncSocket` existující `CAsyncSocket` objekt do jiného objektu.

## <a name="casyncsocketoperator-socket"></a><a name="operator_socket"></a>CAsyncSocket::OPERÁTOR SOCKET

Tento operátor slouží k načtení `CAsyncSocket` popisovače SOCKET objektu.

```
operator SOCKET() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač objektu SOCKET; jinak NULL.

### <a name="remarks"></a>Poznámky

Pomocí popisovače můžete volat přímo windows api.

## <a name="casyncsocketreceive"></a><a name="receive"></a>CAsyncSocket::Příjem

Volání této členské funkce pro příjem dat ze soketu.

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
Délka *lpBuf* v bajtů.

*nPříznaky*<br/>
Určuje způsob, jakým je volání provedeno. Sémantiku této funkce jsou určeny možnosti soketu a *nFlags* parametr. Ten je vytvořen kombinací některé z následujících hodnot s operátorem C++ **OR:**

- MSG_PEEK Náhled na příchozí data. Data jsou zkopírována do vyrovnávací paměti, ale nejsou odebrána ze vstupní fronty.

- MSG_OOB Zpracování nepásových dat.

### <a name="return-value"></a>Návratová hodnota

Pokud nedojde k `Receive` žádné chybě, vrátí počet přijatých bajtů. Pokud bylo připojení uzavřeno, vrátí hodnotu 0. V opačném případě je vrácena hodnota SOCKET_ERROR a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAENOTCONN Soket není připojen.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAENOTSOCK Popisovač není soket.

- Byl zadán MSG_OOB WSAEOPNOTSUPP, ale soket není typu SOCK_STREAM.

- WSAESHUTDOWN Soket byl vypnut; není možné volat `Receive` na soketu po `ShutDown` byl vyvolán s *nHow* nastavit 0 nebo 2.

- WSAEWOULDBLOCK Soket je označen `Receive` jako neblokující a operace by blokovat.

- WSAEMSGSIZE Datový gram byl příliš velký, aby se vešel do zadané vyrovnávací paměti a byl zkrácen.

- WSAEINVAL Soket nebyl `Bind`svázán s .

- WSAECONNABORTED Virtuální okruh byl přerušen z důvodu časového data nebo jiného selhání.

- WSAECONNRESET Virtuální okruh byl resetován vzdálenou stranou.

### <a name="remarks"></a>Poznámky

Tato funkce se používá pro připojené datové proudy nebo sokety datových gramů a používá se ke čtení příchozích dat.

Pro sokety typu SOCK_STREAM je vráceno tolik informací, kolik je aktuálně k dispozici až do velikosti zadané vyrovnávací paměti. Pokud byl soket nakonfigurován pro in-line příjem nepásových dat (možnost soketu SO_OOBINLINE) a data mimo pásmo jsou nepřečtená, budou vrácena pouze data mimo pásmo. Aplikace můžete použít `IOCtlSIOCATMARK` možnost nebo [OnOutOfBandData](#onoutofbanddata) k určení, zda další out-of-band data zbývá číst.

U soketů datagramu jsou data extrahována z prvního datagramu zařazeného do fronty až do velikosti zadané vyrovnávací paměti. Pokud je datagram větší než zadaná vyrovnávací paměť, vyrovnávací paměť je vyplněna první `Receive` částí datagramu, nadbytečná data budou ztracena a vrátí hodnotu SOCKET_ERROR s kódem chyby nastaveným na WSAEMSGSIZE. Pokud v soketu nejsou k dispozici žádná příchozí data, je vrácena hodnota SOCKET_ERROR s kódem chyby nastaveným na WSAEWOULDBLOCK. [Funkce zpětného](#onreceive) volání OnReceive lze určit, kdy dorazí další data.

Pokud je soket typu SOCK_STREAM a vzdálená strana řádně `Receive` ukončila připojení, bude okamžitě dokončena 0 bajtů přijatých. Pokud bylo připojení resetováno, a `Receive` selhat s chybou WSAECONNRESET.

`Receive`by měla být volána pouze jednou pro pokaždé, když [CAsyncSocket::OnReceive](#onreceive) je volána.

### <a name="example"></a>Příklad

  Viz příklad pro [CAsyncSocket::OnReceive](#onreceive).

## <a name="casyncsocketreceivefrom"></a><a name="receivefrom"></a>CAsyncSocket::ReceiveFrom

Volání této členské funkce pro příjem datagramu a uložení zdrojové adresy ve struktuře [SOCKADDR](/windows/win32/winsock/sockaddr-2) nebo v *rSocketAddress*.

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
Délka *lpBuf* v bajtů.

*rSocketAddress*<br/>
Odkaz na `CString` objekt, který obdrží tečkovanou adresu IP čísla.

*rSocketPort*<br/>
Odkaz na UINT, který ukládá port.

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR,](/windows/win32/winsock/sockaddr-2) která obsahuje zdrojovou adresu při návratu.

*lpSockAddrLen*<br/>
Ukazatel na délku zdrojové adresy v *lpSockAddr* v bajtů.

*nPříznaky*<br/>
Určuje způsob, jakým je volání provedeno. Sémantiku této funkce jsou určeny možnosti soketu a *nFlags* parametr. Ten je vytvořen kombinací některé z následujících hodnot s operátorem C++ **OR:**

- MSG_PEEK Náhled na příchozí data. Data jsou zkopírována do vyrovnávací paměti, ale nejsou odebrána ze vstupní fronty.

- MSG_OOB Zpracování nepásových dat.

### <a name="return-value"></a>Návratová hodnota

Pokud nedojde k `ReceiveFrom` žádné chybě, vrátí počet přijatých bajtů. Pokud bylo připojení uzavřeno, vrátí hodnotu 0. V opačném případě je vrácena hodnota SOCKET_ERROR a konkrétní kód `GetLastError`chyby lze načíst voláním . Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEFAULT Argument *lpSockAddrLen* byl neplatný: vyrovnávací paměť *lpSockAddr* byla příliš malá pro umístění adresy partnera.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAEINVAL Soket nebyl `Bind`svázán s .

- WSAENOTCONN Soket není připojen (pouze SOCK_STREAM).

- WSAENOTSOCK Popisovač není soket.

- Byl zadán MSG_OOB WSAEOPNOTSUPP, ale soket není typu SOCK_STREAM.

- WSAESHUTDOWN Soket byl vypnut; není možné volat `ReceiveFrom` na soketu po `ShutDown` byl vyvolán s *nHow* nastavit 0 nebo 2.

- WSAEWOULDBLOCK Soket je označen `ReceiveFrom` jako neblokující a operace by blokovat.

- WSAEMSGSIZE Datový gram byl příliš velký, aby se vešel do zadané vyrovnávací paměti a byl zkrácen.

- WSAECONNABORTED Virtuální okruh byl přerušen z důvodu časového data nebo jiného selhání.

- WSAECONNRESET Virtuální okruh byl resetován vzdálenou stranou.

### <a name="remarks"></a>Poznámky

Tato funkce slouží ke čtení příchozích dat na (případně připojeném) soketu a k zachycení adresy, ze které byla data odeslána.

Chcete-li zpracovat adresy IPv6, použijte [CAsyncSocket::ReceiveFromEx](#receivefromex).

Pro sokety typu SOCK_STREAM je vráceno tolik informací, kolik je aktuálně k dispozici až do velikosti zadané vyrovnávací paměti. Pokud byl soket nakonfigurován pro in-line příjem nepásových dat (možnost soketu SO_OOBINLINE) a data mimo pásmo jsou nepřečtená, budou vrácena pouze data mimo pásmo. Aplikace můžete použít `IOCtlSIOCATMARK` možnost `OnOutOfBandData` nebo k určení, zda další data mimo pásmo zbývá číst. Parametry *lpSockAddr* a *lpSockAddrLen* jsou ignorovány pro SOCK_STREAM sokety.

U soketů datagramu jsou data extrahována z prvního datagramu zařazeného do fronty až do velikosti zadané vyrovnávací paměti. Pokud je datagram větší než zadaná vyrovnávací paměť, vyrovnávací paměť je vyplněna první `ReceiveFrom` částí zprávy, nadbytečná data budou ztracena a vrátí hodnotu SOCKET_ERROR s kódem chyby nastaveným na WSAEMSGSIZE.

Pokud *lpSockAddr* je nenulová a soket je typu SOCK_DGRAM, síťová adresa soketu, který odeslal data je zkopírován do odpovídající struktury [SOCKADDR.](/windows/win32/winsock/sockaddr-2) Hodnota, na kterou poukazuje *lpSockAddrLen,* je inicializována na velikost této struktury a je po návratu upravena tak, aby označovala skutečnou velikost adresy, která je zde uložena. Pokud žádná příchozí data je k `ReceiveFrom` dispozici na soketu, volání čeká na data k doručení, pokud soket je neblokující. V tomto případě je vrácena hodnota SOCKET_ERROR s kódem chyby nastaveným na WSAEWOULDBLOCK. Zpětné `OnReceive` volání lze určit, kdy dorazí další data.

Pokud je soket typu SOCK_STREAM a vzdálená strana řádně `ReceiveFrom` ukončila připojení, bude okamžitě dokončena 0 bajtů přijatých.

## <a name="casyncsocketreceivefromex"></a><a name="receivefromex"></a>CAsyncSocket::ReceiveFromEx

Volání této členské funkce pro příjem datagramu a uložení zdrojové adresy ve struktuře [SOCKADDR](/windows/win32/winsock/sockaddr-2) nebo v *rSocketAddress* (zpracovává adresy IPv6).

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
Délka *lpBuf* v bajtů.

*rSocketAddress*<br/>
Odkaz na `CString` objekt, který obdrží tečkovanou adresu IP čísla.

*rSocketPort*<br/>
Odkaz na UINT, který ukládá port.

*nPříznaky*<br/>
Určuje způsob, jakým je volání provedeno. Sémantiku této funkce jsou určeny možnosti soketu a *nFlags* parametr. Ten je vytvořen kombinací některé z následujících hodnot s operátorem C++ **OR:**

- MSG_PEEK Náhled na příchozí data. Data jsou zkopírována do vyrovnávací paměti, ale nejsou odebrána ze vstupní fronty.

- MSG_OOB Zpracování nepásových dat.

### <a name="return-value"></a>Návratová hodnota

Pokud nedojde k `ReceiveFromEx` žádné chybě, vrátí počet přijatých bajtů. Pokud bylo připojení uzavřeno, vrátí hodnotu 0. V opačném případě je vrácena hodnota SOCKET_ERROR a konkrétní kód `GetLastError`chyby lze načíst voláním . Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEFAULT Argument *lpSockAddrLen* byl neplatný: vyrovnávací paměť *lpSockAddr* byla příliš malá pro umístění adresy partnera.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAEINVAL Soket nebyl `Bind`svázán s .

- WSAENOTCONN Soket není připojen (pouze SOCK_STREAM).

- WSAENOTSOCK Popisovač není soket.

- Byl zadán MSG_OOB WSAEOPNOTSUPP, ale soket není typu SOCK_STREAM.

- WSAESHUTDOWN Soket byl vypnut; není možné volat `ReceiveFromEx` na soketu po `ShutDown` byl vyvolán s *nHow* nastavit 0 nebo 2.

- WSAEWOULDBLOCK Soket je označen `ReceiveFromEx` jako neblokující a operace by blokovat.

- WSAEMSGSIZE Datový gram byl příliš velký, aby se vešel do zadané vyrovnávací paměti a byl zkrácen.

- WSAECONNABORTED Virtuální okruh byl přerušen z důvodu časového data nebo jiného selhání.

- WSAECONNRESET Virtuální okruh byl resetován vzdálenou stranou.

### <a name="remarks"></a>Poznámky

Tato funkce slouží ke čtení příchozích dat na (případně připojeném) soketu a k zachycení adresy, ze které byla data odeslána.

Tato funkce je stejná jako [CAsyncSocket::ReceiveFrom](#receivefrom) s tím rozdílem, že zpracovává adresy IPv6, stejně jako starší protokoly.

Pro sokety typu SOCK_STREAM je vráceno tolik informací, kolik je aktuálně k dispozici až do velikosti zadané vyrovnávací paměti. Pokud byl soket nakonfigurován pro in-line příjem nepásových dat (možnost soketu SO_OOBINLINE) a data mimo pásmo jsou nepřečtená, budou vrácena pouze data mimo pásmo. Aplikace můžete použít `IOCtlSIOCATMARK` možnost `OnOutOfBandData` nebo k určení, zda další data mimo pásmo zbývá číst. Parametry *lpSockAddr* a *lpSockAddrLen* jsou ignorovány pro SOCK_STREAM sokety.

U soketů datagramu jsou data extrahována z prvního datagramu zařazeného do fronty až do velikosti zadané vyrovnávací paměti. Pokud je datagram větší než zadaná vyrovnávací paměť, vyrovnávací paměť je vyplněna první `ReceiveFromEx` částí zprávy, nadbytečná data budou ztracena a vrátí hodnotu SOCKET_ERROR s kódem chyby nastaveným na WSAEMSGSIZE.

Pokud *lpSockAddr* je nenulová a soket je typu SOCK_DGRAM, síťová adresa soketu, který odeslal data je zkopírován do odpovídající struktury [SOCKADDR.](/windows/win32/winsock/sockaddr-2) Hodnota, na kterou poukazuje *lpSockAddrLen,* je inicializována na velikost této struktury a je po návratu upravena tak, aby označovala skutečnou velikost adresy, která je zde uložena. Pokud žádná příchozí data je k `ReceiveFromEx` dispozici na soketu, volání čeká na data k doručení, pokud soket je neblokující. V tomto případě je vrácena hodnota SOCKET_ERROR s kódem chyby nastaveným na WSAEWOULDBLOCK. Zpětné `OnReceive` volání lze určit, kdy dorazí další data.

Pokud je soket typu SOCK_STREAM a vzdálená strana řádně `ReceiveFromEx` ukončila připojení, bude okamžitě dokončena 0 bajtů přijatých.

## <a name="casyncsocketsend"></a><a name="send"></a>CAsyncSocket::Odeslat

Volání této členské funkce k odeslání dat na připojeném soketu.

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Vyrovnávací paměť obsahující data, která mají být přenášena.

*nBufLen*<br/>
Délka dat v *lpBuf* v bajtů.

*nPříznaky*<br/>
Určuje způsob, jakým je volání provedeno. Sémantiku této funkce jsou určeny možnosti soketu a *nFlags* parametr. Ten je vytvořen kombinací některé z následujících hodnot s operátorem C++ **OR:**

- MSG_DONTROUTE Určuje, že data by neměla podléhat směrování. Dodavatel windows sockets můžete zvolit ignorovat tento příznak.

- MSG_OOB Odesílat nepásmová data (pouze SOCK_STREAM).

### <a name="return-value"></a>Návratová hodnota

Pokud nedojde k `Send` žádné chybě, vrátí celkový počet odeslaných znaků. (Všimněte si, že to může být menší než číslo uvedené *nBufLen*.) V opačném případě je vrácena hodnota SOCKET_ERROR a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEACCES Požadovaná adresa je adresa všesměrového vysílání, ale příslušný příznak nebyl nastaven.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAEFAULT Argument *lpBuf* není v platné části adresního prostoru uživatele.

- WSAENETRESET Připojení musí být resetováno, protože implementace Windows Sockets jej vyřadila.

- WSAENOBUFS Implementace rozhraní Windows Sockets hlásí zablokování vyrovnávací paměti.

- WSAENOTCONN Soket není připojen.

- WSAENOTSOCK Popisovač není soket.

- Byl zadán MSG_OOB WSAEOPNOTSUPP, ale soket není typu SOCK_STREAM.

- WSAESHUTDOWN Soket byl vypnut; není možné volat `Send` na soketu po `ShutDown` byl vyvolán s *nHow* nastavena na 1 nebo 2.

- WSAEWOULDBLOCK Soket je označen jako neblokující a požadovaná operace by blokovala.

- WSAEMSGSIZE Soket je typu SOCK_DGRAM a datagram je větší než maximální podporované implementací Windows Sockets.

- WSAEINVAL Soket nebyl `Bind`svázán s .

- WSAECONNABORTED Virtuální okruh byl přerušen z důvodu časového data nebo jiného selhání.

- WSAECONNRESET Virtuální okruh byl resetován vzdálenou stranou.

### <a name="remarks"></a>Poznámky

`Send`se používá k zápisu odchozích dat do připojených datových proudů nebo soketů datových gramů. U soketů datagramu je třeba dbát na to, aby nebyla překročena `iMaxUdpDg` maximální velikost paketu IP `AfxSocketInit`podkladových podsítí, kterou je dán a prvek ve struktuře [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) vrácený programem . Pokud data je příliš dlouhá předat atomicky prostřednictvím základního protokolu, chyba WSAEMSGSIZE je vrácena prostřednictvím `GetLastError`a žádná data jsou přenášena.

Všimněte si, že pro soket datagram úspěšné dokončení `Send` neznamená, že data byla úspěšně doručena.

U `CAsyncSocket` objektů typu SOCK_STREAM může být počet zapsaných bajtů mezi 1 a požadovanou délkou v závislosti na dostupnosti vyrovnávací paměti na místním i zahraničním hostiteli.

### <a name="example"></a>Příklad

  Viz příklad [pro CAsyncSocket::OnSend](#onsend).

## <a name="casyncsocketsendto"></a><a name="sendto"></a>CAsyncSocket::SendTo

Volání této členské funkce k odeslání dat do určitého cíle.

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
Vyrovnávací paměť obsahující data, která mají být přenášena.

*nBufLen*<br/>
Délka dat v *lpBuf* v bajtů.

*nHostPort*<br/>
Port identifikující aplikaci soketu.

*lpszHostAdresa*<br/>
Síťová adresa soketu, ke kterému je tento objekt připojen: název počítače, například "ftp.microsoft.com", nebo tečkované číslo, například "128.56.22.8".

*nPříznaky*<br/>
Určuje způsob, jakým je volání provedeno. Sémantiku této funkce jsou určeny možnosti soketu a *nFlags* parametr. Ten je vytvořen kombinací některé z následujících hodnot s operátorem C++ **OR:**

- MSG_DONTROUTE Určuje, že data by neměla podléhat směrování. Dodavatel windows sockets můžete zvolit ignorovat tento příznak.

- MSG_OOB Odesílat nepásmová data (pouze SOCK_STREAM).

*lpSockAddr*<br/>
Ukazatel na strukturu [SOCKADDR,](/windows/win32/winsock/sockaddr-2) která obsahuje adresu cílového soketu.

*nSockAddrLen*<br/>
Délka adresy v *lpSockAddr* v bajtů.

### <a name="return-value"></a>Návratová hodnota

Pokud nedojde k `SendTo` žádné chybě, vrátí celkový počet odeslaných znaků. (Všimněte si, že to může být menší než číslo uvedené *nBufLen*.) V opačném případě je vrácena hodnota SOCKET_ERROR a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEACCES Požadovaná adresa je adresa všesměrového vysílání, ale příslušný příznak nebyl nastaven.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAEFAULT Parametry *lpBuf* nebo *lpSockAddr* nejsou součástí adresního prostoru uživatele nebo argument *lpSockAddr* je příliš malý (menší než velikost struktury [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINVAL Název hostitele je neplatný.

- WSAENETRESET Připojení musí být resetováno, protože implementace Windows Sockets jej vyřadila.

- WSAENOBUFS Implementace rozhraní Windows Sockets hlásí zablokování vyrovnávací paměti.

- WSAENOTCONN Soket není připojen (pouze SOCK_STREAM).

- WSAENOTSOCK Popisovač není soket.

- Byl zadán MSG_OOB WSAEOPNOTSUPP, ale soket není typu SOCK_STREAM.

- WSAESHUTDOWN Soket byl vypnut; není možné volat `SendTo` na soketu po `ShutDown` byl vyvolán s *nHow* nastavena na 1 nebo 2.

- WSAEWOULDBLOCK Soket je označen jako neblokující a požadovaná operace by blokovala.

- WSAEMSGSIZE Soket je typu SOCK_DGRAM a datagram je větší než maximální podporované implementací Windows Sockets.

- WSAECONNABORTED Virtuální okruh byl přerušen z důvodu časového data nebo jiného selhání.

- WSAECONNRESET Virtuální okruh byl resetován vzdálenou stranou.

- WSAEADDRNOTAVAIL Zadaná adresa není k dispozici z místního počítače.

- S tímto soketem nelze použít adresy WSAEAFNOSUPPORT v zadané rodině.

- WSAEDESTADDRREQ Je vyžadována cílová adresa.

- WSAENETUNREACH V tuto chvíli není z tohoto hostitele dosaženo.

### <a name="remarks"></a>Poznámky

`SendTo`se používá na datagram nebo datové hodu sokety a slouží k zápisu odchozích dat na soketu. U soketů datagramu je třeba dbát na to, aby nebyla překročena `iMaxUdpDg` maximální velikost paketu IP podkladových podsítí, kterou je dán aprvek ve struktuře [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) vyplněný [rozhraním AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Pokud data je příliš dlouhá předat atomicky prostřednictvím základního protokolu, je vrácena chyba WSAEMSGSIZE a žádná data jsou přenášena.

Všimněte si, že `SendTo` úspěšné dokončení a neznamená, že data byla úspěšně doručena.

`SendTo`používá se pouze na SOCK_DGRAM soketu k odeslání datagramu do konkrétního soketu identifikovaného parametrem *lpSockAddr.*

Chcete-li odeslat všesměrové vysílání (pouze na SOCK_DGRAM), adresa v parametru *lpSockAddr* by měla být vytvořena pomocí speciální adresy IP INADDR_BROADCAST (definované v souboru hlavičky Windows Sockets WINSOCK. H) spolu s zamýšleným číslem portu. Nebo pokud je parametr *lpszHostAddress* NULL, soket je nakonfigurován pro vysílání. Obecně není vhodné, aby datový gram všesměrového vysílání překročil velikost, při které může dojít k fragmentaci, což znamená, že datová část datagramu (s výjimkou záhlaví) by neměla překročit 512 bajtů.

Chcete-li zpracovat adresy IPv6, použijte [CAsyncSocket::SendToEx](#sendtoex).

## <a name="casyncsocketsendtoex"></a><a name="sendtoex"></a>CAsyncSocket::SendToex

Volání této členské funkce k odeslání dat do určitého cíle (zpracovává adresy IPv6).

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
Vyrovnávací paměť obsahující data, která mají být přenášena.

*nBufLen*<br/>
Délka dat v *lpBuf* v bajtů.

*nHostPort*<br/>
Port identifikující aplikaci soketu.

*lpszHostAdresa*<br/>
Síťová adresa soketu, ke kterému je tento objekt připojen: název počítače, například "ftp.microsoft.com", nebo tečkované číslo, například "128.56.22.8".

*nPříznaky*<br/>
Určuje způsob, jakým je volání provedeno. Sémantiku této funkce jsou určeny možnosti soketu a *nFlags* parametr. Ten je vytvořen kombinací některé z následujících hodnot s operátorem C++ **OR:**

- MSG_DONTROUTE Určuje, že data by neměla podléhat směrování. Dodavatel windows sockets můžete zvolit ignorovat tento příznak.

- MSG_OOB Odesílat nepásmová data (pouze SOCK_STREAM).

### <a name="return-value"></a>Návratová hodnota

Pokud nedojde k `SendToEx` žádné chybě, vrátí celkový počet odeslaných znaků. (Všimněte si, že to může být menší než číslo uvedené *nBufLen*.) V opačném případě je vrácena hodnota SOCKET_ERROR a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEACCES Požadovaná adresa je adresa všesměrového vysílání, ale příslušný příznak nebyl nastaven.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAEFAULT Parametry *lpBuf* nebo *lpSockAddr* nejsou součástí adresního prostoru uživatele nebo argument *lpSockAddr* je příliš malý (menší než velikost struktury [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINVAL Název hostitele je neplatný.

- WSAENETRESET Připojení musí být resetováno, protože implementace Windows Sockets jej vyřadila.

- WSAENOBUFS Implementace rozhraní Windows Sockets hlásí zablokování vyrovnávací paměti.

- WSAENOTCONN Soket není připojen (pouze SOCK_STREAM).

- WSAENOTSOCK Popisovač není soket.

- Byl zadán MSG_OOB WSAEOPNOTSUPP, ale soket není typu SOCK_STREAM.

- WSAESHUTDOWN Soket byl vypnut; není možné volat `SendToEx` na soketu po `ShutDown` byl vyvolán s *nHow* nastavena na 1 nebo 2.

- WSAEWOULDBLOCK Soket je označen jako neblokující a požadovaná operace by blokovala.

- WSAEMSGSIZE Soket je typu SOCK_DGRAM a datagram je větší než maximální podporované implementací Windows Sockets.

- WSAECONNABORTED Virtuální okruh byl přerušen z důvodu časového data nebo jiného selhání.

- WSAECONNRESET Virtuální okruh byl resetován vzdálenou stranou.

- WSAEADDRNOTAVAIL Zadaná adresa není k dispozici z místního počítače.

- S tímto soketem nelze použít adresy WSAEAFNOSUPPORT v zadané rodině.

- WSAEDESTADDRREQ Je vyžadována cílová adresa.

- WSAENETUNREACH V tuto chvíli není z tohoto hostitele dosaženo.

### <a name="remarks"></a>Poznámky

Tato metoda je stejná jako [CAsyncSocket::SendTo](#sendto) s tím rozdílem, že zpracovává adresy IPv6, stejně jako starší protokoly.

`SendToEx`se používá na datagram nebo datové hodu sokety a slouží k zápisu odchozích dat na soketu. U soketů datagramu je třeba dbát na to, aby nebyla překročena `iMaxUdpDg` maximální velikost paketu IP podkladových podsítí, kterou je dán aprvek ve struktuře [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) vyplněný [rozhraním AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Pokud data je příliš dlouhá předat atomicky prostřednictvím základního protokolu, je vrácena chyba WSAEMSGSIZE a žádná data jsou přenášena.

Všimněte si, že `SendToEx` úspěšné dokončení a neznamená, že data byla úspěšně doručena.

`SendToEx`používá se pouze na SOCK_DGRAM soketu k odeslání datagramu do konkrétního soketu identifikovaného parametrem *lpSockAddr.*

Chcete-li odeslat všesměrové vysílání (pouze na SOCK_DGRAM), adresa v parametru *lpSockAddr* by měla být vytvořena pomocí speciální adresy IP INADDR_BROADCAST (definované v souboru hlavičky Windows Sockets WINSOCK. H) spolu s zamýšleným číslem portu. Nebo pokud je parametr *lpszHostAddress* NULL, soket je nakonfigurován pro vysílání. Obecně není vhodné, aby datový gram všesměrového vysílání překročil velikost, při které může dojít k fragmentaci, což znamená, že datová část datagramu (s výjimkou záhlaví) by neměla překročit 512 bajtů.

## <a name="casyncsocketsetsockopt"></a><a name="setsockopt"></a>CAsyncSocket::SetSockOpt

Volání této členské funkce nastavit možnost soketu.

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Parametry

*nNázev_opčních_*<br/>
Možnost soketu, pro kterou má být nastavena hodnota.

*hodnota lpOption*<br/>
Ukazatel na vyrovnávací paměť, ve které je zadána hodnota pro požadovanou možnost.

*nOptionLen*<br/>
Velikost vyrovnávací paměti *lpOptionValue* v bajtech.

*nÚroveň*<br/>
Úroveň, na které je definována možnost; jediné podporované úrovně jsou SOL_SOCKET a IPPROTO_TCP.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEFAULT *lpOptionValue* není v platné části adresního prostoru procesu.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAEINVAL *nLevel* není platný nebo informace v *lpOptionValue* není platný.

- WSAENETRESET Připojení vypršel, když je nastaven SO_KEEPALIVE.

- WSAENOPROTOOPT Možnost není známa nebo není podporována. Zejména SO_BROADCAST není podporována na sokecích typu SOCK_STREAM, zatímco SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER a SO_OOBINLINE nejsou podporovány na sokecích typu SOCK_DGRAM.

- Připojení WSAENOTCONN bylo resetováno, když je nastaveno SO_KEEPALIVE.

- WSAENOTSOCK Popisovač není soket.

### <a name="remarks"></a>Poznámky

`SetSockOpt`nastaví aktuální hodnotu pro možnost soketu přidružené k soketu libovolného typu v libovolném stavu. Přestože možnosti mohou existovat na více úrovních protokolu, tato specifikace definuje pouze možnosti, které existují na nejvyšší úrovni "soketu". Možnosti ovlivňují operace soketu, například zda jsou urychlená data přijímána v normálním datovém proudu, zda mohou být zprávy všesměrového vysílání odesílány v soketu a tak dále.

Existují dva typy možností soketu: Logické možnosti, které povolují nebo zakazují funkci nebo chování, a možnosti, které vyžadují hodnotu nebo strukturu celého čísla. Chcete-li povolit logickou možnost, *lpOptionValue* odkazuje na nenulové celé číslo. Chcete-li zakázat možnost *lpOptionValue* odkazuje na celé číslo rovnající se nule. *nOptionLen* by měla `sizeof(BOOL)` být rovna pro logické možnosti. Pro ostatní možnosti *lpOptionValue* odkazuje na celé číslo nebo strukturu, která obsahuje požadovanou hodnotu pro možnost a *nOptionLen* je délka celého čísla nebo struktury.

SO_LINGER řídí akci přijatou v případě, že neodeslaná data jsou zařazena do fronty na soketu a `Close` funkce je volána k uzavření soketu.

Ve výchozím nastavení nelze soket svázat (viz [vazba)](#bind)na místní adresu, která je již používána. Příležitostně však může být žádoucí "znovu použít" adresu tímto způsobem. Vzhledem k tomu, že každé připojení je jednoznačně identifikováno kombinací místních a vzdálených adres, není problém s tím, že dva sokety jsou vázány na stejnou místní adresu, pokud se vzdálené adresy liší.

Chcete-li informovat implementaci Windows `Bind` Sockets, že volání na soketu by nemělo být zakázáno, protože požadovaná adresa je již `Bind` používána jiným soketem, měla by aplikace nastavit možnost SO_REUSEADDR soketu pro soket před vydáním volání. Všimněte si, že možnost je interpretována pouze v době `Bind` volání: je proto zbytečné (ale neškodné) nastavit možnost na soketu, který `Bind` nemá být vázán na existující adresu a nastavení nebo resetování možnost i po volání nemá žádný vliv na tento nebo jiný soket.

Aplikace může požadovat, aby implementace rozhraní Windows Sockets umožnila použití paketů "keep-alive" na připojení tcp (Transmission Control Protocol) zapnutím možnosti SO_KEEPALIVE soketu. Implementace Windows Sockets nemusí podporovat použití keep-alives: pokud ano, přesné sémantiku jsou specifické pro implementaci, ale by měly odpovídat části 4.2.3.6 RFC 1122: "Požadavky na internetové hostitele – komunikační vrstvy." Pokud je připojení přerušeno v důsledku "keep-alives" kód chyby WSAENETRESET je vrácena všechna probíhající volání na soketu a všechna další volání se nezdaří s WSAENOTCONN.

Možnost TCP_NODELAY zakáže algoritmus Nagle. Algoritmus Nagle se používá ke snížení počtu malých paketů odeslaných hostitelem ukládáním nepotvrzených odesílaných dat do vyrovnávací paměti, dokud nebude možné odeslat paket plné velikosti. Pro některé aplikace však tento algoritmus může bránit výkonu a TCP_NODELAY lze vypnout. Autoři aplikací by neměli nastavit TCP_NODELAY, pokud není dobře pochopen a žádoucí dopad, protože nastavení TCP_NODELAY může mít významný negativní dopad na výkon sítě. TCP_NODELAY je jediná podporovaná možnost soketu, která používá úroveň IPPROTO_TCP; všechny ostatní možnosti používají úroveň SOL_SOCKET.

Některé implementace Windows Sockets poskytují informace o ladění výstupu, pokud je možnost SO_DEBUG nastavena aplikací.

Následující možnosti jsou `SetSockOpt`podporovány pro . Typ identifikuje typ dat adresovaných *lpOptionValue*.

|Hodnota|Typ|Význam|
|-----------|----------|-------------|
|SO_BROADCAST|Bool|Povolit přenos všesměrových zpráv na soketu.|
|SO_DEBUG|Bool|Zaznamenejte informace o ladění.|
|SO_DONTLINGER|Bool|Neblokujte `Close` čekání na odeslání neodeslaných dat. Nastavení této možnosti je `l_onoff` ekvivalentní nastavení SO_LINGER s nastavenou na nulu.|
|SO_DONTROUTE|Bool|Nesměrovat: poslat přímo do rozhraní.|
|SO_KEEPALIVE|Bool|Pošlete keep-alives.|
|SO_LINGER|`struct LINGER`|Přetrvávají `Close` na, pokud jsou přítomna neodeslaná data.|
|SO_OOBINLINE|Bool|Příjem nepásových dat v normálním datovém proudu.|
|SO_RCVBUF|**int**|Zadejte velikost vyrovnávací paměti pro příjem.|
|SO_REUSEADDR|Bool|Povolit soket být vázán na adresu, která je již používána. (Viz [Vazba](#bind).)|
|SO_SNDBUF|**int**|Zadejte velikost vyrovnávací paměti pro odeslání.|
|TCP_NODELAY|Bool|Zakáže algoritmus Nagle pro odesílání slučování.|

Možnosti distribuce softwaru Berkeley (BSD), pro které nejsou podporovány, `SetSockOpt` jsou:

|Hodnota|Typ|Význam|
|-----------|----------|-------------|
|SO_ACCEPTCONN|Bool|Socket naslouchá|
|SO_ERROR|**int**|Získejte stav chyby a vymazání.|
|SO_RCVLOWAT|**int**|Získejte značku s nízkou hladinou vody.|
|SO_RCVTIMEO|**int**|Příjem časového času|
|SO_SNDLOWAT|**int**|Pošlete značku s nízkou hladinou vody.|
|SO_SNDTIMEO|**int**|Odeslat časový čas.|
|SO_TYPE|**int**|Typ zásuvky.|
|IP_OPTIONS||Nastavte pole možností v hlavičce IP.|

## <a name="casyncsocketshutdown"></a><a name="shutdown"></a>CAsyncSocket::Vypnutí

Volání této členské funkce zakázat odesílá, přijímá nebo obojí na soketu.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>Parametry

*Nhow*<br/>
Příznak, který popisuje, jaké typy operací již nebudou povoleny, pomocí následujících výčtových hodnot:

- **přijímá = 0**

- **odešle = 1**

- **oba = 2**

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním [GetLastError](#getlasterror). Pro tuto člennou funkci platí následující chyby:

- WSANOTINITIALISED Před použitím tohoto rozhraní API musí dojít k úspěšnému [afxSocketInitu.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementace zásuvek systému Windows zjistila, že se nezdařil o síťový podsystém.

- WSAEINVAL *nJak* není platný.

- WSAEINPROGRESS Probíhá blokující operace windows sockets.

- WSAENOTCONN Soket není připojen (pouze SOCK_STREAM).

- WSAENOTSOCK Popisovač není soket.

### <a name="remarks"></a>Poznámky

`ShutDown`se používá na všech typech soketů zakázat příjem, přenos, nebo obojí. Pokud *nHow* je 0, následné příjem na soketu bude zakázáno. To nemá žádný vliv na nižší vrstvy protokolu.

U protokolu TCP (Transmission Control Protocol) se okno TCP nezmění a příchozí data budou přijata (ale nebudou potvrzena), dokud nebude okno vyčerpáno. Pro protokol UDP (User Datagram Protocol) jsou příchozí datagramy přijímány a zařazeny do fronty. V žádném případě nebude generován chybový paket ICMP. Pokud *nHow* je 1, následné odešle jsou zakázány. Pro tcp sokety bude odeslána FIN. Nastavení *nHow* na 2 zakáže odesílá i přijímá, jak je popsáno výše.

Všimněte `ShutDown` si, že nezavře soket a prostředky připojené `Close` k soketu nebudou uvolněny, dokud nebude volána. Aplikace by neměla spoléhat na možnost opětovného použití soketu po jeho vypnutí. Zejména implementace Windows Sockets není nutné podporovat použití `Connect` na takové soketu.

### <a name="example"></a>Příklad

  Viz příklad pro [CAsyncSocket::OnReceive](#onreceive).

## <a name="casyncsocketsocket"></a><a name="socket"></a>CASyncSocket::Soket

Přiděluje popisovač soketu.

```
BOOL Socket(
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    int nProtocolType = 0,
    int nAddressFormat = PF_INET);
```

### <a name="parameters"></a>Parametry

*nTyp socket*<br/>
Určuje `SOCK_STREAM` nebo `SOCK_DGRAM`.

*lUdálost*<br/>
Bitová maska, která určuje kombinaci síťových událostí, o které má aplikace zájem.

- `FD_READ`: Chcete dostávat oznámení o připravenosti ke čtení.

- `FD_WRITE`: Chcete dostávat oznámení o připravenosti k zápisu.

- `FD_OOB`: Chcete dostávat oznámení o příchodu nepásových dat.

- `FD_ACCEPT`: Chcete dostávat oznámení o příchozích připojeních.

- `FD_CONNECT`: Chcete dostávat oznámení o dokončeném připojení.

- `FD_CLOSE`: Chcete dostávat oznámení o uzavření soketu.

*nTyp protokolu*<br/>
Protokol, který má být použit se soketem, který je specifický pro uvedenou rodinu adres.

*nAddressFormat*<br/>
Specifikace rodiny adres.

### <a name="return-value"></a>Návratová hodnota

Vrací `TRUE` se `FALSE` k úspěchu, k neúspěchu.

### <a name="remarks"></a>Poznámky

Tato metoda přiděluje popisovač soketu. Nevolá [CAsyncSocket::Bind](#bind) svázat soket na zadanou adresu, `Bind` takže je třeba volat později svázat soketu na zadanou adresu. Můžete použít [CAsyncSocket::SetSockOpt](#setsockopt) nastavit možnost soketu před tím, než je vázán.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CSocket – třída](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
