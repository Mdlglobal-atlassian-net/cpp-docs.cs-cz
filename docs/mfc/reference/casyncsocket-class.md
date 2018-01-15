---
title: "CAsyncSocket – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24ef9c6e39d72e756b95472daee46b7d39503943
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="casyncsocket-class"></a>CAsyncSocket – třída
Představuje Windows soketu – koncový bod síťové komunikace.  
  
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
|[CAsyncSocket::Accept](#accept)|Přijme připojení na soketu.|  
|[CAsyncSocket::AsyncSelect](#asyncselect)|Oznámení o události požadavky pro soket.|  
|[CAsyncSocket::Attach](#attach)|Připojí popisovač soketu pro `CAsyncSocket` objektu.|  
|[CAsyncSocket::Bind](#bind)|Přidruží místní adresu soketu.|  
|[CAsyncSocket::Close](#close)|Zavře soketu.|  
|[CAsyncSocket::Connect](#connect)|Naváže připojení k soketu partnera.|  
|[CAsyncSocket::Create](#create)|Vytvoří soketu.|  
|[CAsyncSocket::Detach](#detach)|Umožňuje odpojit popisovač soketu z `CAsyncSocket` objektu.|  
|[CAsyncSocket::FromHandle](#fromhandle)|Vrátí ukazatel na `CAsyncSocket` objekt, daný popisovač soketu.|  
|[CAsyncSocket::GetLastError](#getlasterror)|Získá stav chyby pro poslední operace, která se nezdařila.|  
|[CAsyncSocket::GetPeerName](#getpeername)|Získá adresu soketu sdílené, k němuž je připojen soket.|  
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Získá adresu soketu sdílené, ke kterému je soket připojené (popisovačů adresy IPv6).|  
|[CAsyncSocket::GetSockName](#getsockname)|Získá místní název pro soket.|  
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Získá název místního soketu (popisovačů adresy IPv6).|  
|[CAsyncSocket::GetSockOpt](#getsockopt)|Načte možnost soketu.|  
|[CAsyncSocket::IOCtl](#ioctl)|Určuje režim soketu.|  
|[CAsyncSocket::Listen](#listen)|Určuje soketu naslouchat pro příchozí požadavky na připojení.|  
|[CAsyncSocket::Receive](#receive)|Přijímá data ze soketu.|  
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Získá datagram a uloží zdrojovou adresu.|  
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Obdrží datagram a ukládá zdrojové adresy (popisovačů adresy IPv6).|  
|[CAsyncSocket::Send](#send)|Odešle data na připojených soket.|  
|[CAsyncSocket::SendTo](#sendto)|Odešle data na určité cíle.|  
|[CAsyncSocket::SendToEx](#sendtoex)|Odešle data na určité cílové místo (popisovačů adresy IPv6).|  
|[CAsyncSocket::SetSockOpt](#setsockopt)|Nastaví možnost soketu.|  
|[CAsyncSocket::ShutDown](#shutdown)|Zakáže **odeslat** nebo **Receive** volání na soket.|  
|[CASyncSocket::Socket](#socket)|Přiděluje popisovač soketu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAsyncSocket::OnAccept](#onaccept)|Upozorní naslouchání soketu, který může přijmout čekající žádosti o připojení voláním **přijmout**.|  
|[CAsyncSocket::OnClose](#onclose)|Upozorní, že je zavřená soketů, které k němu připojená soketu.|  
|[CAsyncSocket::OnConnect](#onconnect)|Oznámí připojování soketu, pokus o připojení je dokončena, zda úspěšně, nebo v chybě.|  
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Upozorní přijímající soketu se out-of-band dat ke čtení na soket, obvykle naléhavé zprávy.|  
|[CAsyncSocket::OnReceive](#onreceive)|Naslouchání soketu upozorní, že se data mají být načteny voláním **Receive**.|  
|[CAsyncSocket::OnSend](#onsend)|Upozorní soketu voláním, kterou může odesílat data **odeslat**.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAsyncSocket::operator =](#operator_eq)|Přiřadí novou hodnotu k `CAsyncSocket` objektu.|  
|[CAsyncSocket::operator SOKETŮ](#operator_socket)|Tento operátor umožňuje načíst **SOKETU** zpracování z `CAsyncSocket` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAsyncSocket::m_hSocket](#m_hsocket)|Určuje, **SOKETU** popisovač připojených k tomuto `CAsyncSocket` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Třída `CAsyncSocket` zapouzdří soket funkce rozhraní API systému Windows, poskytuje abstrakci objektově orientované pro programátory, kteří chtějí používat ve spojení s MFC rozhraní Windows Sockets.  
  
 Tato třída vychází z předpokladu, že rozumíte síťové komunikace. Je zodpovědná za zpracování blokování pořadí bajtů rozdílů, a nastavte převody mezi kódování Unicode a vícebajtové znakové řetězce (MBCS). Pokud chcete pohodlnější rozhraní, které spravuje za vás tyto problémy, viz třídy [CSocket](../../mfc/reference/csocket-class.md).  
  
 Použít `CAsyncSocket` objektu, volání jeho konstruktoru, pak zavolají [vytvořit](#create) funkce pro vytvoření základní popisovač soketu (typ `SOCKET`), s výjimkou na přijatém sokety. Pro server soketu volání [naslouchání](#listen) – členská funkce a volání soketu klienta [připojit](#connect) – členská funkce. Časový limit soketu serveru by měly volat [přijmout](#accept) funkce při přijetí žádosti o připojení. Použít zbývající `CAsyncSocket` funkce provádět komunikace mezi sokety. Po dokončení zrušení `CAsyncSocket` objektu, pokud byla vytvořena v haldě; automaticky volání destruktoru [Zavřít](#close) funkce. `SOCKET` Datový typ je popsána v článku [Windows Sockets: pozadí](../../mfc/windows-sockets-background.md).  
  
> [!NOTE]
>  Pokud používáte MFC sockets v sekundární vláken v staticky propojené knihovny MFC aplikaci, musí volat `AfxSocketInit` v každé vlákno, která používá sockets k chybě při inicializaci knihovny soketů. Ve výchozím nastavení `AfxSocketInit` je volán jen v primárních vlákno.  
  
 Další informace najdete v tématu [Windows Sockets: použití třídy CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) a související články., a také [rozhraní API systému Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAsyncSocket`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxsock.h  
  
##  <a name="accept"></a>CAsyncSocket::Accept  
 Volání této funkce člen přijmout připojení na soket.  
  
```  
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,  
    SOCKADDR* lpSockAddr = NULL,  
    int* lpSockAddrLen = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `rConnectedSocket`  
 Odkaz identifikace nové soketu, který je k dispozici pro připojení.  
  
 `lpSockAddr`  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura, která přijímá adresu připojení soketu, protože znám v síti. Přesný formát `lpSockAddr` argument je dáno rodina adres navázat, když byla vytvořena soketu. Pokud `lpSockAddr` nebo `lpSockAddrLen` rovná **NULL**, je vrácena žádné informace o vzdálené adresy přijatý soketu.  
  
 `lpSockAddrLen`  
 Ukazatel na délku adresy v `lpSockAddr` v bajtech. `lpSockAddrLen` Je výsledkem hodnota parametru: nejprve musí obsahovat množství místa, na kterou odkazuje `lpSockAddr`; návratu bude obsahovat skutečná délka (v bajtech) adresu vrácenou z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEFAULT** `lpSockAddrLen` argument je příliš malý (menší než velikost [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura).  
  
- **WSAEINPROGRESS** blokování volání rozhraní Windows Sockets právě probíhá.  
  
- **WSAEINVAL** `Listen` nebyla vyvolaná před přijmout.  
  
- **WSAEMFILE** je fronta prázdná při vstupu, tak, aby přijímal a nejsou k dispozici žádné popisovače.  
  
- `WSAENOBUFS`Vyrovnávací paměť není k dispozici.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
- **WSAEOPNOTSUPP** odkazované soketu není typem, který podporuje službu orientovaná na připojení.  
  
- **WSAEWOULDBLOCK** soketu je označen jako neblokový a žádná připojení nejsou přípustné.  
  
### <a name="remarks"></a>Poznámky  
 Tato rutina extrahuje prvního připojení ve frontě služby čeká na připojení, vytvoří novou soketu se stejné vlastnosti jako tento soketu a připojí jej k `rConnectedSocket`. Pokud nejsou žádné čekající připojení ve frontě, **přijmout** vrátí hodnotu 0 a `GetLastError` vrátí chybu. Přijatý soketů ( *rConnectedSocket)* nelze použít tak, aby přijímal více připojení. Původní soketu zůstane otevřený a naslouchá.  
  
 Argument `lpSockAddr` je parametr výsledek, který obsahuje adresu připojování soketu jako ví, že komunikace vrstvy. **Přijměte** je třeba použít s typy založeného na připojení soketu **SOCK_STREAM**.  
  
##  <a name="asyncselect"></a>CAsyncSocket::AsyncSelect  
 Volání této funkce člen požádat o oznámení události pro soket.  
  
```  
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>Parametry  
 `lEvent`  
 Bitová maska, která určuje kombinaci události sítě, ve kterých je zájmu aplikace.  
  
- **FD_READ** chcete dostávat oznámení o připravenosti pro čtení.  
  
- **FD_WRITE** chcete dostávat oznámení, když jsou k dispozici možné načíst data.  
  
- **FD_OOB** chcete dostávat oznámení o doručení out-of-band data.  
  
- **FD_ACCEPT** chcete dostávat oznámení o příchozích připojení.  
  
- **FD_CONNECT** chcete dostávat oznámení o výsledků připojení.  
  
- **FD_CLOSE** chcete dostávat oznámení při uzavření soketu partnerského uzlu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEINVAL** znamená, že jeden ze zadaných parametrů byla neplatná.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží k určení, které funkce MFC zpětné volání oznámení bude volána pro soket. `AsyncSelect`automaticky nastaví tato soketu neblokový režimu. Další informace najdete v článku [Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="attach"></a>CAsyncSocket::Attach  
 Volání této funkce člen připojit `hSocket` popisovače `CAsyncSocket` objektu.  
  
```  
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>Parametry  
 `hSocket`  
 Obsahuje popisovač pro soket.  
  
 `lEvent`  
 Bitová maska, která určuje kombinaci události sítě, ve kterých je zájmu aplikace.  
  
- **FD_READ** chcete dostávat oznámení o připravenosti pro čtení.  
  
- **FD_WRITE** chcete dostávat oznámení, když jsou k dispozici možné načíst data.  
  
- **FD_OOB** chcete dostávat oznámení o doručení out-of-band data.  
  
- **FD_ACCEPT** chcete dostávat oznámení o příchozích připojení.  
  
- **FD_CONNECT** chcete dostávat oznámení o výsledků připojení.  
  
- **FD_CLOSE** chcete dostávat oznámení při uzavření soketu partnerského uzlu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěšného funkce.  
  
### <a name="remarks"></a>Poznámky  
 **SOKETU** popisovač je uložený v objektu [m_hSocket](#m_hsocket) – datový člen.  
  
##  <a name="bind"></a>CAsyncSocket::Bind  
 Volání této funkce člena pro přidružení místní adresu soketu.  
  
```  
BOOL Bind(
    UINT nSocketPort,  
    LPCTSTR lpszSocketAddress = NULL);

 
BOOL Bind (
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>Parametry  
 `nSocketPort`  
 Port identifikace aplikace soketu.  
  
 `lpszSocketAddress`  
 Síťová adresa, jako je například "128.56.22.8" desítkovém číslo. Předávání **NULL** řetězec pro tento parametr určuje **CAsyncSocket** instance má naslouchat činnost klienta na všech síťových rozhraní.  
  
 `lpSockAddr`  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura, která obsahuje adresu přiřadit k tomuto soketu.  
  
 `nSockAddrLen`  
 Délka adresu v `lpSockAddr` v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEADDRINUSE** zadaná adresa je již používán. (Viz **SO_REUSEADDR** soketu možnosti v části [SetSockOpt](#setsockopt).)  
  
- **WSAEFAULT** `nSockAddrLen` argument je příliš malý (menší než velikost [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura).  
  
- **WSAEINPROGRESS** blokování volání rozhraní Windows Sockets právě probíhá.  
  
- **WSAEAFNOSUPPORT** rodiny zadaná adresa není podporován tímto portem.  
  
- **WSAEINVAL** soket je již vázána na adresu.  
  
- `WSAENOBUFS`Nedostatek vyrovnávací paměti k dispozici příliš mnoho připojení.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
### <a name="remarks"></a>Poznámky  
 Tato rutina se používá na nepřipojené datagram nebo datový proud soketu před následné **připojit** nebo `Listen` volání. Předtím, než může přijímat žádosti o připojení, naslouchá server soketu musí vybrat číslo portu a nastavit ho známé rozhraní Windows Sockets voláním **vazby**. **Vytvoření vazby** vytvoří místní přidružení (číslo adresy a portu hostitele) soketu přiřazením místní název nepojmenované soketu.  
  
##  <a name="casyncsocket"></a>CAsyncSocket::CAsyncSocket  
 Vytvoří objekt prázdné soketu.  
  
```  
CAsyncSocket();
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytváření objektu, musí volat jeho **vytvořit** – členská funkce vytvořit **SOKETU** datové struktury a vytvořte vazbu adresy. (Na straně serveru Windows Sockets komunikace, když vytváří naslouchání soketu soket pro použití v **přijmout** volání, nevolejte **vytvořit** této soketu.)  
  
##  <a name="close"></a>CAsyncSocket::Close  
 Zavře soketu.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce uvolní popisovač soketu tak, aby další na ni odkazují selže s chybou **WSAENOTSOCK**. Pokud je to poslední odkaz na základní soket, související informace pro pojmenování a zařazených do fronty data jsou zahozeny. Objekt soketu volání destruktoru **Zavřít** za vás.  
  
 Pro `CAsyncSocket`, ale ne pro `CSocket`, sémantika **Zavřít** jsou ovlivněné možnosti soketu **SO_LINGER** a **SO_DONTLINGER**. Další informace najdete v tématu – členská funkce `GetSockOpt`.  
  
##  <a name="connect"></a>CAsyncSocket::Connect  
 Volání této funkce člen k navázání připojení k bez připojení datového proudu nebo datagram soketu.  
  
```  
BOOL Connect(
    LPCTSTR lpszHostAddress,  
    UINT nHostPort);

 
BOOL Connect(
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszHostAddress`  
 Síťová adresa soketu, k němuž je připojen tento objekt: název počítače, jako je například "ftp.microsoft.com" nebo desítkovém číslo jako je například "128.56.22.8".  
  
 `nHostPort`  
 Port identifikace aplikace soketu.  
  
 `lpSockAddr`  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura, která obsahuje adresu připojené soketu.  
  
 `nSockAddrLen`  
 Délka adresu v `lpSockAddr` v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Pokud to znamená chybový kód **WSAEWOULDBLOCK**a vaše aplikace používá přepisovatelné zpětná volání, vaše aplikace bude přijímat `OnConnect` zprávu po dokončení operace připojení. Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEADDRINUSE** zadaná adresa je již používán.  
  
- **WSAEINPROGRESS** blokování volání rozhraní Windows Sockets právě probíhá.  
  
- **WSAEADDRNOTAVAIL** zadaná adresa není k dispozici z místního počítače.  
  
- **WSAEAFNOSUPPORT** adresy zadaný řady nelze použít s Tento soketu.  
  
- **WSAECONNREFUSED** odmítl pokus o připojení.  
  
- **WSAEDESTADDRREQ** cílové adresa je povinná.  
  
- **WSAEFAULT** `nSockAddrLen` argumentu je nesprávný.  
  
- **WSAEINVAL** neplatný hostitel adresu.  
  
- **WSAEISCONN** soket je již připojen.  
  
- **WSAEMFILE** jsou k dispozici žádné další popisovače souborů.  
  
- **WSAENETUNREACH** síti není dosažitelné z tohoto hostitele v tuto chvíli.  
  
- `WSAENOBUFS`Vyrovnávací paměť není k dispozici. Soket nemůže být připojen.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
- **WSAETIMEDOUT** pokus o připojení vypršela bez navázání připojení.  
  
- **WSAEWOULDBLOCK** soketu je označen jako neblokový a připojení nelze dokončit okamžitě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud soket není vázaný, jedinečné hodnoty přiřazené k přidružení místní systém a soketu je označena jako vázána. Všimněte si, že pokud je pole adresy struktury název samých nul, **Connect** vrátí nula. Chcete-li získat rozšířené informace o chybě, zavolejte `GetLastError` – členská funkce.  
  
 Pro sokety datového proudu (typ **SOCK_STREAM**), je cizí hostitele iniciované aktivní připojení. Po úspěšném dokončení volání soketu je připraven k odesílání a přijímání dat soketu.  
  
 Datagram soketu (typ **SOCK_DGRAM**), výchozí cíl nastavená, který se použije při následných **odeslat** a **Receive** volání.  
  
##  <a name="create"></a>CAsyncSocket::Create  
 Volání **vytvořit** – členská funkce poté, co vytvořen objekt soketu se vytvořit soket Windows a jeho připojení.  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nSocketPort`  
 Dobře známé port pro použití s soket nebo 0, pokud chcete, aby Windows Sockets vyberte port.  
  
 `nSocketType`  
 **SOCK_STREAM** nebo **SOCK_DGRAM**.  
  
 `lEvent`  
 Bitová maska, která určuje kombinaci události sítě, ve kterých je zájmu aplikace.  
  
- **FD_READ** chcete dostávat oznámení o připravenosti pro čtení.  
  
- **FD_WRITE** chcete dostávat oznámení o připravenosti pro zápis.  
  
- **FD_OOB** chcete dostávat oznámení o doručení out-of-band data.  
  
- **FD_ACCEPT** chcete dostávat oznámení o příchozích připojení.  
  
- **FD_CONNECT** chcete dostávat oznámení o dokončené připojení.  
  
- **FD_CLOSE** chcete dostávat oznámení o uzavření soketu.  
  
 *lpszSockAddress*  
 Ukazatel na řetězec obsahující síťovou adresu připojené soketu desítkovém číslo, například "128.56.22.8". Předávání **NULL** řetězec pro tento parametr určuje **CAsyncSocket** instance má naslouchat činnost klienta na všech síťových rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEAFNOSUPPORT** rodiny zadaná adresa není podporována.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAEMFILE** jsou k dispozici žádné další popisovače souborů.  
  
- `WSAENOBUFS`Vyrovnávací paměť není k dispozici. Nelze vytvořit soket.  
  
- **WSAEPROTONOSUPPORT** nepodporuje zadaný port.  
  
- **WSAEPROTOTYPE** zadaný port je nesprávný typ. Tento soketu.  
  
- **WSAESOCKTNOSUPPORT** soketu zadaný typ není podporován v této rodině adres.  
  
### <a name="remarks"></a>Poznámky  
 **Vytvoření** volání [soketu](#socket) a v případě úspěšného volání [vazby](#bind) pro vazbu na zadanou adresu soketu. Jsou podporovány následující typy soketu:  
  
- **SOCK_STREAM** sekvencování, poskytuje spolehlivé, plně duplexní, založeného na připojení bajtové datové proudy. Rodina adres Internetu používá protokolu TCP (Transmission Control).  
  
- **SOCK_DGRAM** podporuje datagramy, které jsou bez připojení nespolehlivé pakety pevné (obvykle malé) maximální délky. Protokolu UDP (User Datagram) se používá pro rodina adres Internetu.  
  
    > [!NOTE]
    >  **Přijmout** – členská funkce trvá odkaz na nový, prázdný `CSocket` objektu jako její parametr. Je nutné vytvořit tento objekt před voláním **přijmout**. Mějte na paměti, že pokud tento objekt soketu prochází oboru, zavře připojení. Nevolejte **vytvořit** pro tento nový objekt soketu.  
  
> [!IMPORTANT]
> **Vytvoření** je **není** bezpečné pro přístup z více vláken.  Při volání ho v prostředí s více procesy kde se může vyvolat současně různých vláknech, je nutné chránit každé volání s mutex nebo jiných zámek synchronizace.  
  
 Další informace o sokety datového proudu a datagram, najdete v článcích [Windows Sockets: pozadí](../../mfc/windows-sockets-background.md) a [Windows Sockets: porty a adresy soketů](../../mfc/windows-sockets-ports-and-socket-addresses.md) a [2rozhraníAPIsystémuWindowsSockets](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="detach"></a>CAsyncSocket::Detach  
 Volání této funkce člen odpojit **SOKETU** zpracování v `m_hSocket` – datový člen z `CAsyncSocket` objektu a nastavte `m_hSocket` k **NULL**.  
  
```  
SOCKET Detach();
```  
  
##  <a name="fromhandle"></a>CAsyncSocket::FromHandle  
 Vrátí ukazatel na `CAsyncSocket` objektu.  
  
```  
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>Parametry  
 `hSocket`  
 Obsahuje popisovač pro soket.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CAsyncSocket` objekt, nebo **NULL** Pokud neexistuje žádné `CAsyncSocket` objekt připojený k `hSocket`.  
  
### <a name="remarks"></a>Poznámky  
 Při zadané **SOKETU** zpracování, pokud `CAsyncSocket` objektu není připojený k popisovač, vrátí funkce člen **NULL**.  
  
##  <a name="getlasterror"></a>CAsyncSocket::GetLastError  
 Volání této funkce člen získat stav chyby poslední operace, která se nezdařila.  
  
```  
static int PASCAL GetLastError();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota označuje kód chyby pro poslední rozhraní API systému Windows Sockets rutinu provádí tento přístup z více vláken.  
  
### <a name="remarks"></a>Poznámky  
 Při konkrétní členské funkce označuje, že došlo k chybě, `GetLastError` by měla být volána načíst kód odpovídající chyby. V popisech jednotlivými členy funkce seznam kódů chyb použít.  
  
 Další informace o chybových kódech najdete v tématu [rozhraní API systému Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="getpeername"></a>CAsyncSocket::GetPeerName  
 Volání této funkce člen získat adresu soketu sdílené, ke kterému je připojený tento soketu.  
  
```  
BOOL GetPeerName(
    CString& rPeerAddress,  
    UINT& rPeerPort);

 
BOOL GetPeerName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>Parametry  
 `rPeerAddress`  
 Odkaz na `CString` objekt, který přijme desítkovém číslo IP adresu.  
  
 `rPeerPort`  
 Odkaz na **Celé_číslo** , ukládá port.  
  
 `lpSockAddr`  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura, která přijímá název sdílené soketu.  
  
 `lpSockAddrLen`  
 Ukazatel na délku adresy v `lpSockAddr` v bajtech. Při návratu `lpSockAddrLen` argument obsahuje skutečná velikost `lpSockAddr` vrátila v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEFAULT** `lpSockAddrLen` argument není dostatečně velký.  
  
- **WSAEINPROGRESS** blokování volání rozhraní Windows Sockets právě probíhá.  
  
- **WSAENOTCONN** soket není připojen.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zpracovat adresy IPv6, použijte [CAsyncSocket::GetPeerNameEx](#getpeernameex).  
  
##  <a name="getpeernameex"></a>CAsyncSocket::GetPeerNameEx  
 Volání této funkce člen získat adresu partnera soketu, ke kterému je tento soketu připojené (popisovačů adresy IPv6).  
  
```  
BOOL GetPeerNameEx(
    CString& rPeerAddress,  
    UINT& rPeerPort);
```  
  
### <a name="parameters"></a>Parametry  
 `rPeerAddress`  
 Odkaz na `CString` objekt, který přijme desítkovém číslo IP adresu.  
  
 `rPeerPort`  
 Odkaz na **Celé_číslo** , ukládá port.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEFAULT** `lpSockAddrLen` argument není dostatečně velký.  
  
- **WSAEINPROGRESS** blokování volání rozhraní Windows Sockets právě probíhá.  
  
- **WSAENOTCONN** soket není připojen.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je stejný jako [CAsyncSocket::GetPeerName](#getpeername) s tím rozdílem, že zpracovává IPv6 adres i starší protokoly.  
  
##  <a name="getsockname"></a>CAsyncSocket::GetSockName  
 Volání této funkce člen získat místní název pro soket.  
  
```  
BOOL GetSockName(
    CString& rSocketAddress,  
    UINT& rSocketPort);

 
BOOL GetSockName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>Parametry  
 `rSocketAddress`  
 Odkaz na `CString` objekt, který přijme desítkovém číslo IP adresu.  
  
 `rSocketPort`  
 Odkaz na **Celé_číslo** , ukládá port.  
  
 `lpSockAddr`  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura, která přijímá adresu soketu.  
  
 `lpSockAddrLen`  
 Ukazatel na délku adresy v `lpSockAddr` v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEFAULT** `lpSockAddrLen` argument není dostatečně velký.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
- **WSAEINVAL** soket nebyl byla svázána se adresu s **vazby**.  
  
### <a name="remarks"></a>Poznámky  
 Toto volání je obzvláště užitečná při **připojit** aniž by to byl proveden volání **vazby** nejprve; toto volání poskytuje pouze prostředky, pomocí kterého můžete určit místní přidružení, která byla nastavena pomocí systém.  
  
 Chcete-li zpracovat adresy IPv6, použijte [CAsyncSocket::GetSockNameEx](#getsocknameex)  
  
##  <a name="getsocknameex"></a>CAsyncSocket::GetSockNameEx  
 Volání této funkce člen získat název místního soketu (popisovačů adresy IPv6).  
  
```  
BOOL GetSockNameEx(
    CString& rSocketAddress,  
    UINT& rSocketPort);
```  
  
### <a name="parameters"></a>Parametry  
 `rSocketAddress`  
 Odkaz na `CString` objekt, který přijme desítkovém číslo IP adresu.  
  
 `rSocketPort`  
 Odkaz na **Celé_číslo** , ukládá port.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEFAULT** `lpSockAddrLen` argument není dostatečně velký.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
- **WSAEINVAL** soket nebyl byla svázána se adresu s **vazby**.  
  
### <a name="remarks"></a>Poznámky  
 Toto volání je stejný jako [CAsyncSocket::GetSockName](#getsockname) s tím rozdílem, že zpracovává IPv6 adres i starší protokoly.  
  
 Toto volání je obzvláště užitečná při **připojit** aniž by to byl proveden volání **vazby** nejprve; toto volání poskytuje pouze prostředky, pomocí kterého můžete určit místní přidružení, která byla nastavena pomocí systém.  
  
##  <a name="getsockopt"></a>CAsyncSocket::GetSockOpt  
 Volání této funkce člen načíst možnost soketu.  
  
```  
BOOL GetSockOpt(
    int nOptionName,  
    void* lpOptionValue,  
    int* lpOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>Parametry  
 `nOptionName`  
 Možnost soketu pro kterou je hodnota má být načtena.  
  
 `lpOptionValue`  
 Ukazatel do vyrovnávací paměti, ve kterém má být vrácen hodnota pro požadovanou možnost. Ve vyrovnávací paměti je vrácena hodnota spojené s vybranou možnost `lpOptionValue`. Celé číslo na kterou odkazuje `lpOptionLen` by měl obsahovat původně velikosti této vyrovnávací paměti v bajtech; a na vrátit, nastaví se velikost hodnota vrácená. Pro **SO_LINGER**, bude jím velikost `LINGER` struktury; pro všechny ostatní možnosti se bude velikost **BOOL** nebo `int`, v závislosti na možnosti. Zobrazit seznam možností a jejich velikosti v oddílu Poznámky.  
  
 `lpOptionLen`  
 Ukazatel na velikost `lpOptionValue` vyrovnávací paměti v bajtech.  
  
 `nLevel`  
 Úroveň, ve kterém je definována možnost; jsou pouze podporované úrovně **SOL_SOCKET** a **IPPROTO_TCP**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Pokud nikdy nastavit možnost s `SetSockOpt`, pak `GetSockOpt` vrátí výchozí hodnota pro možnost. Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEFAULT** `lpOptionLen` argument byl neplatný.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAENOPROTOOPT** možnost je neznámý nebo nepodporovaný. Konkrétně **SO_BROADCAST** nepodporuje sockets typu **SOCK_STREAM**, zatímco **SO_ACCEPTCONN**, **SO_DONTLINGER**,  **SO_KEEPALIVE**, **SO_LINGER**, a **SO_OOBINLINE** nejsou podporovány na sockets typu **SOCK_DGRAM**.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
### <a name="remarks"></a>Poznámky  
 `GetSockOpt`načte aktuální hodnota možnosti soketu přidružená k soketu libovolného typu, v libovolném stavu a ukládá výsledky v `lpOptionValue`. Možnosti ovlivňují soketů operace, například směrování paketů, přenos dat out-of-band a tak dále.  
  
 Jsou podporovány následující možnosti pro `GetSockOpt`. Typ jsou uvedeny typy dat používala `lpOptionValue`. **TCP_NODELAY** možnost používá úroveň **IPPROTO_TCP**; všechny ostatní možnosti použít úroveň **SOL_SOCKET**.  
  
|Hodnota|Typ|Význam|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|Socket naslouchá.|  
|**SO_BROADCAST**|**BOOL**|Socket je nakonfigurován pro přenos zpráv všesměrového vysílání.|  
|**SO_DEBUG**|**BOOL**|Je povoleno ladění.|  
|**SO_DONTLINGER**|**BOOL**|V případě hodnoty true **SO_LINGER** možnost je zakázaná.|  
|**SO_DONTROUTE**|**BOOL**|Směrování je zakázána.|  
|**SO_ERROR**|`int`|Načíst stav chyby a zrušte.|  
|**SO_KEEPALIVE**|**BOOL**|Udržování otevřených připojení jsou odesílány.|  
|**SO_LINGER**|**linger – struktura**|Vrátí aktuální linger – možnosti.|  
|**SO_OOBINLINE**|**BOOL**|Přijímání dat Out-of-band v normálním datový proud.|  
|**ASYNCHRONNÍ**|`int`|Velikost vyrovnávací paměti pro obdrží.|  
|**SO_REUSEADDR**|**BOOL**|Soket mohou být vázány na adresu, která je již používán.|  
|**SO_SNDBUF**|`int`|Velikost vyrovnávací paměti pro odešle.|  
|**SO_TYPE**|`int`|Typ soketu (například **SOCK_STREAM**).|  
|**TCP_NODELAY**|**BOOL**|Zakáže algoritmus Nagle pro odeslání slučování.|  
  
 Možnosti Berkeley Software Distribution (BSD) není podporován pro `GetSockOpt` jsou:  
  
|Hodnota|Typ|Význam|  
|-----------|----------|-------------|  
|**SO_RCVLOWAT**|`int`|Zobrazí dolní meze.|  
|**SO_RCVTIMEO**|`int`|Zobrazí časový limit.|  
|**SO_SNDLOWAT**|`int`|Odešlete dolní meze.|  
|**SO_SNDTIMEO**|`int`|Časového limitu odesílání.|  
|**IP_OPTIONS**||Získání možnosti v hlavičce protokolu IP.|  
|**TCP_MAXSEG**|`int`|Získáte TCP maximální velikost segmentu.|  
  
 Volání metody `GetSockOpt` s Nepodporovaná možnost bude mít za následek chybový kód **WSAENOPROTOOPT** návratu z `GetLastError`.  
  
##  <a name="ioctl"></a>CAsyncSocket::IOCtl  
 Volání této funkce člen k řízení režimu soketu.  
  
```  
BOOL IOCtl(
    long lCommand,  
    DWORD* lpArgument);
```  
  
### <a name="parameters"></a>Parametry  
 `lCommand`  
 Příkaz k provedení na soketu.  
  
 `lpArgument`  
 Ukazatel na parametr `lCommand`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEINVAL** `lCommand` není platný příkaz nebo `lpArgument` není přijatelný parametr pro `lCommand`, nebo příkaz není pro typ zadaný soketu.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
### <a name="remarks"></a>Poznámky  
 Tato rutina lze použít na všechny soketu v libovolném stavu. Slouží k získání nebo načíst parametry přidružené k soketu, nezávisle na podsystému protokolu a komunikaci. Podporovány jsou následující příkazy:  
  
- **FIONBIO** povolit nebo zakázat režim neblokový na soketu. `lpArgument` Parametr odkazuje na `DWORD`, což je nenulové hodnoty, pokud má být povoleno neblokový režimu a nula v případě je zakázán. Pokud `AsyncSelect` byl vydán na soket, pak žádný pokus o použití **IOCtl** nastavit časový limit soketu zpět na režim blokování se nezdaří s **WSAEINVAL**. Nastavit časový limit soketu zpět na režim blokování a zabránit **WSAEINVAL** chybu, aplikace musíte nejdřív zakázat `AsyncSelect` voláním `AsyncSelect` s `lEvent` parametr rovná 0, pak zavolají **IOCtl** .  
  
- **FIONREAD** určit maximální počet bajtů, které může číst s jedním **Receive** volat z této soketu. `lpArgument` Parametr odkazuje na `DWORD` ve kterém **IOCtl** ukládá výsledek. Pokud je tento soketu typu **SOCK_STREAM**, **FIONREAD** vrátí celkové množství dat, který lze číst v jediném **Receive**; je to obvykle stejné jako celkovou velikost data ve frontě na soket. Pokud je tento soketu typu **SOCK_DGRAM**, **FIONREAD** vrátí velikost první datagram ve frontě na soket.  
  
- **SIOCATMARK** určit, zda všechna data out-of-band byl načten. Vztahuje se pouze na soket typu **SOCK_STREAM** který byl nakonfigurován pro příjem vložené žádná data out-of-band ( **SO_OOBINLINE**). Pokud žádná data out-of-band čeká na přečíst, vrátí nenulovou operaci. V opačném případě vrátí 0 a další **Receive** nebo `ReceiveFrom` provést na soket budou načítat některé nebo všechny předchozí "znak" dat; by aplikace měla použít **SIOCATMARK** operace Určí, zda zůstává žádná data. Pokud neexistují žádné normální data předcházející "naléhavé" dat (out-of-band), nebudou přijímány v pořadí. (Všimněte si, že **Receive** nebo `ReceiveFrom` se nikdy kombinovat data out-of-band a normální ve stejném volání.) `lpArgument` Parametr odkazuje na `DWORD` ve kterém **IOCtl** ukládá výsledek.  
  
 Tato funkce je podmnožinou **ioctl()** v rámci Berkeley sokety. Zejména, neexistuje žádný příkaz, který je ekvivalentní **FIOASYNC**, zatímco **SIOCATMARK** je příkaz pouze soketu úrovni, který není podporován.  
  
##  <a name="listen"></a>CAsyncSocket::Listen  
 Volání této funkce člen naslouchat pro příchozí požadavky na připojení.  
  
```  
BOOL Listen(int nConnectionBacklog = 5);
```  
  
### <a name="parameters"></a>Parametry  
 *nConnectionBacklog*  
 Maximální délka, ke kterému můžou růst frontu čeká na připojení. Platný rozsah je od 1 do 5.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEADDRINUSE** byl proveden pokus o naslouchat na adresu používán.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAEINVAL** soket nebyl byla svázána s **vazby** nebo je již připojen.  
  
- **WSAEISCONN** soket je již připojen.  
  
- **WSAEMFILE** jsou k dispozici žádné další popisovače souborů.  
  
- `WSAENOBUFS`Vyrovnávací paměť není k dispozici.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
- **WSAEOPNOTSUPP** odkazované soketu není typu, který podporuje `Listen` operaci.  
  
### <a name="remarks"></a>Poznámky  
 Přijmout připojení, je prvním vytvoření soketu s **vytvořit**, nevyřízených položek pro příchozí připojení je definován s `Listen`, a pak přijímat připojení jsou s **přijmout**. `Listen`platí pouze pro soketů, které podporují připojení, který je typu **SOCK_STREAM**. Tato soketu je uvést do "pasivní" režim, kde jsou příchozí připojení potvrzeny a ve frontě čekajících přijetí procesem.  
  
 Tato funkce se obvykle používá servery (nebo jakékoli aplikace, která chce, aby se tak, aby přijímal připojení), může mít více než jeden požadavek na připojení najednou: Pokud dorazí požadavek na připojení s úplné fronty, klient se zobrazí chyba s uvedením  **WSAECONNREFUSED**.  
  
 `Listen`pokusí se i nadále fungovat nejracionálnější, pokud nejsou dostupné žádné porty (popisovače). Dokud vyprázdnění fronty se bude akceptovat připojení. Pokud porty k dispozici, novější volání `Listen` nebo **přijmout** doplnění fronty k aktuální nebo poslední "backlogu,", pokud je to možné a pokračovat v čekání na příchozí připojení.  
  
##  <a name="m_hsocket"></a>CAsyncSocket::m_hSocket  
 Obsahuje **SOKETU** zpracování soketu zapouzdřené to `CAsyncSocket` objektu.  
  
```  
SOCKET m_hSocket;  
```  
  
##  <a name="onaccept"></a>CAsyncSocket::OnAccept  
 Voláno rámcem oznámit naslouchání soketu, který může přijmout čekající žádosti o připojení pomocí volání [přijmout](#accept) – členská funkce.  
  
```  
virtual void OnAccept(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrorCode`  
 Poslední chyba na soketu. Následující kódy chyb platí pro `OnAccept` – členská funkce:  
  
- **0** funkce byla úspěšně provedena.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="onclose"></a>CAsyncSocket::OnClose  
 Voláno rámcem upozornit tento soketu, zpracování uzavřené připojené soketu.  
  
```  
virtual void OnClose(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrorCode`  
 Poslední chyba na soketu. Použít následující kódy chyb `OnClose` – členská funkce:  
  
- **0** funkce byla úspěšně provedena.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAECONNRESET** připojení bylo resetováno na vzdálené straně.  
  
- **WSAECONNABORTED** připojení byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="onconnect"></a>CAsyncSocket::OnConnect  
 Voláno rámcem tento připojování soketu oznámit, že skončí její pokus o připojení, ať už úspěšně nebo chyba.  
  
```  
virtual void OnConnect(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrorCode`  
 Poslední chyba na soketu. Použít následující kódy chyb `OnConnect` – členská funkce:  
  
- **0** funkce byla úspěšně provedena.  
  
- **WSAEADDRINUSE** zadaná adresa je již používán.  
  
- **WSAEADDRNOTAVAIL** zadaná adresa není k dispozici z místního počítače.  
  
- **WSAEAFNOSUPPORT** adresy zadaný řady nelze použít s Tento soketu.  
  
- **WSAECONNREFUSED** vynuceně odmítl pokus o připojení.  
  
- **WSAEDESTADDRREQ** cílové adresa je povinná.  
  
- **WSAEFAULT** `lpSockAddrLen` argumentu je nesprávný.  
  
- **WSAEINVAL** soket je již vázána na adresu.  
  
- **WSAEISCONN** soket je již připojen.  
  
- **WSAEMFILE** jsou k dispozici žádné další popisovače souborů.  
  
- **WSAENETUNREACH** síti není dosažitelné z tohoto hostitele v tuto chvíli.  
  
- `WSAENOBUFS`Vyrovnávací paměť není k dispozici. Soket nemůže být připojen.  
  
- **WSAENOTCONN** soket není připojen.  
  
- **WSAENOTSOCK** popisovač je soubor, není soketu.  
  
- **WSAETIMEDOUT** pokus o připojení vypršel časový limit bez navázání připojení.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  V [CSocket](../../mfc/reference/csocket-class.md), `OnConnect` volána funkce oznámení. Pro připojení, můžete jednoduše volání **Connect**, který se vrátí po dokončení připojení (úspěšně nebo chyba). Zpracování oznámení připojení je podrobností implementace MFC.  
  
 Další informace najdete v tématu [Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]  
  
##  <a name="onoutofbanddata"></a>CAsyncSocket::OnOutOfBandData  
 Voláno rámcem přijímající soketu, který odesílání soketu má out-of-band data k odeslání oznámení.  
  
```  
virtual void OnOutOfBandData(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrorCode`  
 Poslední chyba na soketu. Použít následující kódy chyb `OnOutOfBandData` – členská funkce:  
  
- **0** funkce byla úspěšně provedena.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Out-of-band data jsou logicky nezávislý na kanál, který je přidružen každý pár připojené soketů typu **SOCK_STREAM**. Kanál se obvykle používá k odesílání naléhavá data.  
  
 MFC podporuje out-of-band data, ale uživatelé třídy `CAsyncSocket` se nedoporučuje v jeho použití. Jednodušší způsob je vytvořit druhý soket pro předávání taková data. Další informace o datech out-of-band najdete v tématu [Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="onreceive"></a>CAsyncSocket::OnReceive  
 Voláno rámcem upozornit tento soketu se data ve vyrovnávací paměti, který může načíst volání **Receive** – členská funkce.  
  
```  
virtual void OnReceive(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrorCode`  
 Poslední chyba na soketu. Použít následující kódy chyb `OnReceive` – členská funkce:  
  
- **0** funkce byla úspěšně provedena.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]  
  
##  <a name="onsend"></a>CAsyncSocket::OnSend  
 Voláno rámcem oznámit soket, kterou nyní odesílat data volání **odeslat** – členská funkce.  
  
```  
virtual void OnSend(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrorCode`  
 Poslední chyba na soketu. Použít následující kódy chyb `OnSend` – členská funkce:  
  
- **0** funkce byla úspěšně provedena.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [Windows Sockets: oznámení soketů](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]  
  
##  <a name="operator_eq"></a>CAsyncSocket::operator =  
 Přiřadí novou hodnotu k `CAsyncSocket` objektu.  
  
```  
void operator=(const CAsyncSocket& rSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Odkaz na existující `CAsyncSocket` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce můžete zkopírovat stávající `CAsyncSocket` objektu na jiný `CAsyncSocket` objektu.  
  
##  <a name="operator_socket"></a>CAsyncSocket::operator SOKETŮ  
 Tento operátor umožňuje načíst **SOKETU** zpracování z `CAsyncSocket` objektu.  
  
```  
operator SOCKET() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného popisovač **SOKETU** objektu; jinak, **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač můžete přímo volat rozhraní API systému Windows.  
  
##  <a name="receive"></a>CAsyncSocket::Receive  
 Volání této funkce člena na příjem dat ze soketu.  
  
```  
virtual int Receive(
    void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Vyrovnávací paměť pro příchozí data.  
  
 `nBufLen`  
 Délka `lpBuf` v bajtech.  
  
 `nFlags`  
 Určuje způsob, jak při volání. Sémantika této funkce jsou závisí na možnostech soketu a `nFlags` parametr. Je vytvořený kombinací některý z následujících hodnot C++ `OR` operátor:  
  
- **MSG_PEEK** prohlížet příchozí data. Data se zkopírují do vyrovnávací paměti, ale není odebraný ze vstupní fronty.  
  
- **MSG_OOB** zpracovat out-of-band data.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nedojde k žádné chybě **Receive** vrátí počet bajtů přijatých. Pokud připojení bylo ukončeno, vrátí hodnotu 0. Jinak hodnota **SOCKET_ERROR** se vrátí, a určitý kód chyby nelze získat voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAENOTCONN** soket není připojen.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
- **WSAEOPNOTSUPP MSG_OOB** byla zadána, ale soket není typu **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** byla vypnuta soket; není možné volat **Receive** na soket po `ShutDown` metoda byla volána s `nHow` nastavena na 0 nebo 2.  
  
- **WSAEWOULDBLOCK** soketu je označen jako neblokový a **Receive** operace by blokovat.  
  
- **WSAEMSGSIZE** datagram byla příliš velká a nevejde se do zadané vyrovnávací paměti a byla zkrácena.  
  
- **WSAEINVAL** soket nebyl byla svázána s **vazby**.  
  
- **WSAECONNABORTED** virtuální okruh byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
- **WSAECONNRESET** virtuální okruh bylo resetováno na vzdálené straně.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se používá pro připojené datový proud nebo sokety datagramů a slouží k načtení příchozí data.  
  
 Sokety typu **SOCK_STREAM**, jak se vrátí mnohem informace, jako je nyní k dispozici až po velikost poskytnutá vyrovnávací paměť. Pokud soket nakonfigurovaný pro příjem vložené out-of-band dat (možnost soketu **SO_OOBINLINE**) a out-of-band dat nepřečtená, bude vrácena pouze out-of-band data. Aplikace můžete použít **IOCtlSIOCATMARK** možnost nebo [OnOutOfBandData](#onoutofbanddata) k určení, zda žádná data více out-of-band zůstane čtení.  
  
 Pro sokety datagramu jsou extrahována data ze první datagram zařazených do fronty, až velikost poskytnutá vyrovnávací paměť. Pokud datagram je větší než poskytnutá vyrovnávací paměť, vyrovnávací paměť je plná první část datagramu, dojde ke ztrátě nebo nadbytečná data a **Receive** vrací hodnotu **SOCKET_ERROR** s kódem chyby nastavit na **WSAEMSGSIZE**. Pokud žádná příchozí data je k dispozici na soket hodnota **SOCKET_ERROR** se vrátil s kódem chyby nastavena na **WSAEWOULDBLOCK**. [Události OnReceive](#onreceive) funkce zpětného volání lze použít k určení, když dorazí další data.  
  
 Pokud je časový limit soketu typu **SOCK_STREAM** a na vzdálené straně má řádné ukončení připojení, **Receive** dokončí okamžitě s 0 bajtů přijatých. Pokud připojení, **Receive** se nezdaří s chybou **WSAECONNRESET**.  
  
 **Přijímat** by měla být volána pouze jednou po každém [CAsyncSocket::OnReceive](#onreceive) je volána.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAsyncSocket::OnReceive](#onreceive).  
  
##  <a name="receivefrom"></a>CAsyncSocket::ReceiveFrom  
 Volání této funkce člen přijmout datagram a ukládání zdrojovou adresu v [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura nebo v `rSocketAddress`.  
  
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
 `lpBuf`  
 Vyrovnávací paměť pro příchozí data.  
  
 `nBufLen`  
 Délka `lpBuf` v bajtech.  
  
 `rSocketAddress`  
 Odkaz na `CString` objekt, který přijme desítkovém číslo IP adresu.  
  
 `rSocketPort`  
 Odkaz na **Celé_číslo** , ukládá port.  
  
 `lpSockAddr`  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura, která obsahuje po návratu zdrojovou adresu.  
  
 `lpSockAddrLen`  
 Ukazatel na délku zdrojovou adresu v `lpSockAddr` v bajtech.  
  
 `nFlags`  
 Určuje způsob, jak při volání. Sémantika této funkce jsou závisí na možnostech soketu a `nFlags` parametr. Je vytvořený kombinací některý z následujících hodnot C++ `OR` operátor:  
  
- **MSG_PEEK** prohlížet příchozí data. Data se zkopírují do vyrovnávací paměti, ale není odebraný ze vstupní fronty.  
  
- **MSG_OOB** zpracovat out-of-band data.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nedojde k žádné chybě `ReceiveFrom` vrátí počet bajtů přijatých. Pokud připojení bylo ukončeno, vrátí hodnotu 0. Jinak hodnota **SOCKET_ERROR** se vrátí, a určitý kód chyby nelze získat voláním `GetLastError`. Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEFAULT** `lpSockAddrLen` byl neplatný argument: `lpSockAddr` vyrovnávací paměť je příliš malá, aby dokázala pojmout adresy partnerského uzlu.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAEINVAL** soket nebyl byla svázána s **vazby**.  
  
- **WSAENOTCONN** soket není připojen ( **SOCK_STREAM** pouze).  
  
- **WSAENOTSOCK** popisovač není soket.  
  
- **WSAEOPNOTSUPP MSG_OOB** byla zadána, ale soket není typu **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** byla vypnuta soket; není možné volat `ReceiveFrom` na soket po `ShutDown` metoda byla volána s `nHow` nastavena na 0 nebo 2.  
  
- **WSAEWOULDBLOCK** soketu je označen jako neblokový a `ReceiveFrom` operace by blokovat.  
  
- **WSAEMSGSIZE** datagram byla příliš velká a nevejde se do zadané vyrovnávací paměti a byla zkrácena.  
  
- **WSAECONNABORTED** virtuální okruh byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
- **WSAECONNRESET** virtuální okruh bylo resetováno na vzdálené straně.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží ke čtení příchozích dat (pravděpodobně připojeným) soketem a zachycení na adresu, ze kterého se data byla odeslána.  
  
 Chcete-li zpracovat adresy IPv6, použijte [CAsyncSocket::ReceiveFromEx](#receivefromex).  
  
 Sokety typu **SOCK_STREAM**, jak se vrátí mnohem informace, jako je nyní k dispozici až po velikost poskytnutá vyrovnávací paměť. Pokud soket nakonfigurovaný pro příjem vložené out-of-band dat (možnost soketu **SO_OOBINLINE**) a out-of-band dat nepřečtená, bude vrácena pouze out-of-band data. Aplikace můžete použít **IOCtlSIOCATMARK** možnost nebo `OnOutOfBandData` k určení, zda žádná data více out-of-band zůstane čtení. `lpSockAddr` a `lpSockAddrLen` parametry jsou ignorovány pro **SOCK_STREAM** sokety.  
  
 Pro sokety datagramu jsou extrahována data ze první datagram zařazených do fronty, až velikost poskytnutá vyrovnávací paměť. Pokud datagram je větší než poskytnutá vyrovnávací paměť, vyrovnávací paměť je plná první část zprávy, dojde ke ztrátě nebo nadbytečná data a `ReceiveFrom` vrací hodnotu **SOCKET_ERROR** s kódem chyby nastavit na  **WSAEMSGSIZE**.  
  
 Pokud `lpSockAddr` je nenulové hodnoty, a soketu je typu **SOCK_DGRAM**, síťovou adresu soketů, které odeslat data se zkopíruje do odpovídajících [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura. Hodnota na kterou odkazuje `lpSockAddrLen` je inicializována tak, aby velikost tuto strukturu a je změnit při návratu do znamenat skutečná velikost adresy v ní uloženy. Pokud je k dispozici žádná příchozí data na soket, `ReceiveFrom` volání čeká data dorazí, pokud je časový limit soketu neblokový. V tomto případě hodnotu **SOCKET_ERROR** se vrátil s kódem chyby nastavena na **WSAEWOULDBLOCK**. `OnReceive` Zpětného volání lze použít k určení, když dorazí další data.  
  
 Pokud je časový limit soketu typu **SOCK_STREAM** a na vzdálené straně má řádné ukončení připojení, `ReceiveFrom` dokončí okamžitě s 0 bajtů přijatých.  
  
##  <a name="receivefromex"></a>CAsyncSocket::ReceiveFromEx  
 Volání této funkce člen přijmout datagram a ukládání zdrojovou adresu v [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura nebo v `rSocketAddress` (zpracovává adresy IPv6).  
  
```  
int ReceiveFromEx(
    void* lpBuf,  
    int nBufLen,  
    CString& rSocketAddress,  
    UINT& rSocketPort,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Vyrovnávací paměť pro příchozí data.  
  
 `nBufLen`  
 Délka `lpBuf` v bajtech.  
  
 `rSocketAddress`  
 Odkaz na `CString` objekt, který přijme desítkovém číslo IP adresu.  
  
 `rSocketPort`  
 Odkaz na **Celé_číslo** , ukládá port.  
  
 `nFlags`  
 Určuje způsob, jak při volání. Sémantika této funkce jsou závisí na možnostech soketu a `nFlags` parametr. Je vytvořený kombinací některý z následujících hodnot C++ `OR` operátor:  
  
- **MSG_PEEK** prohlížet příchozí data. Data se zkopírují do vyrovnávací paměti, ale není odebraný ze vstupní fronty.  
  
- **MSG_OOB** zpracovat out-of-band data.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nedojde k žádné chybě `ReceiveFromEx` vrátí počet bajtů přijatých. Pokud připojení bylo ukončeno, vrátí hodnotu 0. Jinak hodnota **SOCKET_ERROR** se vrátí, a určitý kód chyby nelze získat voláním `GetLastError`. Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEFAULT** `lpSockAddrLen` byl neplatný argument: `lpSockAddr` vyrovnávací paměť je příliš malá, aby dokázala pojmout adresy partnerského uzlu.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAEINVAL** soket nebyl byla svázána s **vazby**.  
  
- **WSAENOTCONN** soket není připojen ( **SOCK_STREAM** pouze).  
  
- **WSAENOTSOCK** popisovač není soket.  
  
- **WSAEOPNOTSUPP MSG_OOB** byla zadána, ale soket není typu **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** byla vypnuta soket; není možné volat `ReceiveFromEx` na soket po `ShutDown` metoda byla volána s `nHow` nastavena na 0 nebo 2.  
  
- **WSAEWOULDBLOCK** soketu je označen jako neblokový a `ReceiveFromEx` operace by blokovat.  
  
- **WSAEMSGSIZE** datagram byla příliš velká a nevejde se do zadané vyrovnávací paměti a byla zkrácena.  
  
- **WSAECONNABORTED** virtuální okruh byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
- **WSAECONNRESET** virtuální okruh bylo resetováno na vzdálené straně.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží ke čtení příchozích dat (pravděpodobně připojeným) soketem a zachycení na adresu, ze kterého se data byla odeslána.  
  
 Tato funkce je stejný jako [CAsyncSocket::ReceiveFrom](#receivefrom) s tím rozdílem, že zpracovává IPv6 adres i starší protokoly.  
  
 Sokety typu **SOCK_STREAM**, jak se vrátí mnohem informace, jako je nyní k dispozici až po velikost poskytnutá vyrovnávací paměť. Pokud soket nakonfigurovaný pro příjem vložené out-of-band dat (možnost soketu **SO_OOBINLINE**) a out-of-band dat nepřečtená, bude vrácena pouze out-of-band data. Aplikace můžete použít **IOCtlSIOCATMARK** možnost nebo `OnOutOfBandData` k určení, zda žádná data více out-of-band zůstane čtení. `lpSockAddr` a `lpSockAddrLen` parametry jsou ignorovány pro **SOCK_STREAM** sokety.  
  
 Pro sokety datagramu jsou extrahována data ze první datagram zařazených do fronty, až velikost poskytnutá vyrovnávací paměť. Pokud datagram je větší než poskytnutá vyrovnávací paměť, vyrovnávací paměť je plná první část zprávy, dojde ke ztrátě nebo nadbytečná data a `ReceiveFromEx` vrací hodnotu **SOCKET_ERROR** s kódem chyby nastavit na  **WSAEMSGSIZE**.  
  
 Pokud `lpSockAddr` je nenulové hodnoty, a soketu je typu **SOCK_DGRAM**, síťovou adresu soketů, které odeslat data se zkopíruje do odpovídajících [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura. Hodnota na kterou odkazuje `lpSockAddrLen` je inicializována tak, aby velikost tuto strukturu a je změnit při návratu do znamenat skutečná velikost adresy v ní uloženy. Pokud je k dispozici žádná příchozí data na soket, `ReceiveFromEx` volání čeká data dorazí, pokud je časový limit soketu neblokový. V tomto případě hodnotu **SOCKET_ERROR** se vrátil s kódem chyby nastavena na **WSAEWOULDBLOCK**. `OnReceive` Zpětného volání lze použít k určení, když dorazí další data.  
  
 Pokud je časový limit soketu typu **SOCK_STREAM** a na vzdálené straně má řádné ukončení připojení, `ReceiveFromEx` dokončí okamžitě s 0 bajtů přijatých.  
  
##  <a name="send"></a>CAsyncSocket::Send  
 Volání této funkce člen odeslat data na připojených soketu.  
  
```  
virtual int Send(
    const void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Vyrovnávací paměť obsahující data, která mají být odeslány.  
  
 `nBufLen`  
 Délka dat v `lpBuf` v bajtech.  
  
 `nFlags`  
 Určuje způsob, jak při volání. Sémantika této funkce jsou závisí na možnostech soketu a `nFlags` parametr. Je vytvořený kombinací některý z následujících hodnot C++ `OR` operátor:  
  
- **MSG_DONTROUTE** Určuje, že data by neměl být předmětem směrování. Windows Sockets dodavatele můžete ignorovat tento příznak.  
  
- **MSG_OOB** odesílat data out-of-band ( **SOCK_STREAM** pouze).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nedojde k žádné chybě **odeslat** vrátí celkový počet odeslaných znaků. (Všimněte si, že to může být menší než číslo indikován `nBufLen`.) Jinak hodnota **SOCKET_ERROR** se vrátí, a určitý kód chyby nelze získat voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEACCES** požadovaná adresa je adresa všesměrového vysílání, ale odpovídající příznak nebyla nastavena.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAEFAULT** `lpBuf` argument není platný součástí adresního prostoru uživatele.  
  
- **WSAENETRESET** připojení, musí se obnovit, protože implementace rozhraní Windows Sockets ho vyřadit.  
  
- `WSAENOBUFS`Implementace rozhraní Windows Sockets hlásí zablokování vyrovnávací paměti.  
  
- **WSAENOTCONN** soket není připojen.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
- **WSAEOPNOTSUPP MSG_OOB** byla zadána, ale soket není typu **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** byla vypnuta soket; není možné volat **odeslat** na soket po `ShutDown` metoda byla volána s `nHow` nastavena na hodnotu 1 nebo 2.  
  
- **WSAEWOULDBLOCK** soketu je označen jako neblokový a bude blokovat požadovanou operaci.  
  
- **WSAEMSGSIZE** soketu je typu **SOCK_DGRAM**, a je větší než maximální počet podporovaný implementací rozhraní Windows Sockets datagram.  
  
- **WSAEINVAL** soket nebyl byla svázána s **vazby**.  
  
- **WSAECONNABORTED** virtuální okruh byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
- **WSAECONNRESET** virtuální okruh bylo resetováno na vzdálené straně.  
  
### <a name="remarks"></a>Poznámky  
 **Odeslat** se používá k zápisu odchozí data na připojených sokety datového proudu nebo datagram. Pro sokety datagramu, se musí věnovat nepřesahující maximální velikost paketu IP základní podsítě, která je **iMaxUdpDg** element v [wsadata –](../../mfc/reference/wsadata-structure.md) struktura vrácený `AfxSocketInit`. Pokud data je příliš dlouhý a předáte atomicky základního protokolu chyba **WSAEMSGSIZE** je vrácen prostřednictvím `GetLastError`, a je odesláno žádná data.  
  
 Všimněte si, že pro datagram soketu úspěšné dokončení **odeslat** nevyplývá, že data byla úspěšně doručena.  
  
 Na `CAsyncSocket` objekty typu **SOCK_STREAM**, počet zapsaných bajtů může být v rozmezí 1 a požadovaná délka, v závislosti na dostupnosti vyrovnávací paměti na místní a cizí hostitelích.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAsyncSocket::OnSend](#onsend).  
  
##  <a name="sendto"></a>CAsyncSocket::SendTo  
 Volání této funkce člen k odesílání dat na určité cíle.  
  
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
 `lpBuf`  
 Vyrovnávací paměť obsahující data, která mají být odeslány.  
  
 `nBufLen`  
 Délka dat v `lpBuf` v bajtech.  
  
 `nHostPort`  
 Port identifikace aplikace soketu.  
  
 `lpszHostAddress`  
 Síťová adresa soketu, k němuž je připojen tento objekt: název počítače, jako je například "ftp.microsoft.com" nebo desítkovém číslo jako je například "128.56.22.8".  
  
 `nFlags`  
 Určuje způsob, jak při volání. Sémantika této funkce jsou závisí na možnostech soketu a `nFlags` parametr. Je vytvořený kombinací některý z následujících hodnot C++ `OR` operátor:  
  
- **MSG_DONTROUTE** Určuje, že data by neměl být předmětem směrování. Windows Sockets dodavatele můžete ignorovat tento příznak.  
  
- **MSG_OOB** odesílat data out-of-band ( **SOCK_STREAM** pouze).  
  
 `lpSockAddr`  
 Ukazatel [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura, která obsahuje adresu soket cíle.  
  
 `nSockAddrLen`  
 Délka adresu v `lpSockAddr` v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nedojde k žádné chybě `SendTo` vrátí celkový počet odeslaných znaků. (Všimněte si, že to může být menší než číslo indikován `nBufLen`.) Jinak hodnota **SOCKET_ERROR** se vrátí, a určitý kód chyby nelze získat voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEACCES** požadovaná adresa je adresa všesměrového vysílání, ale odpovídající příznak nebyla nastavena.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAEFAULT** `lpBuf` nebo `lpSockAddr` parametry nejsou součástí adresního prostoru uživatele, nebo `lpSockAddr` argument je příliš malý (menší než velikost [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura).  
  
- **WSAEINVAL** název hostitele je neplatný.  
  
- **WSAENETRESET** připojení, musí se obnovit, protože implementace rozhraní Windows Sockets ho vyřadit.  
  
- `WSAENOBUFS`Implementace rozhraní Windows Sockets hlásí zablokování vyrovnávací paměti.  
  
- **WSAENOTCONN** soket není připojen ( **SOCK_STREAM** pouze).  
  
- **WSAENOTSOCK** popisovač není soket.  
  
- **WSAEOPNOTSUPP MSG_OOB** byla zadána, ale soket není typu **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** byla vypnuta soket; není možné volat `SendTo` na soket po `ShutDown` metoda byla volána s `nHow` nastavena na hodnotu 1 nebo 2.  
  
- **WSAEWOULDBLOCK** soketu je označen jako neblokový a bude blokovat požadovanou operaci.  
  
- **WSAEMSGSIZE** soketu je typu **SOCK_DGRAM**, a je větší než maximální počet podporovaný implementací rozhraní Windows Sockets datagram.  
  
- **WSAECONNABORTED** virtuální okruh byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
- **WSAECONNRESET** virtuální okruh bylo resetováno na vzdálené straně.  
  
- **WSAEADDRNOTAVAIL** zadaná adresa není k dispozici z místního počítače.  
  
- **WSAEAFNOSUPPORT** adresy zadaný řady nelze použít s Tento soketu.  
  
- **WSAEDESTADDRREQ** cílové adresa je povinná.  
  
- **WSAENETUNREACH** síti není dosažitelné z tohoto hostitele v tuto chvíli.  
  
### <a name="remarks"></a>Poznámky  
 `SendTo`se používá na sokety datagramů nebo datový proud a slouží k zápisu odchozích dat na soket. Pro sokety datagramu, se musí věnovat nepřesahující maximální velikost paketu IP základní podsítě, která je **iMaxUdpDg** element v [wsadata –](../../mfc/reference/wsadata-structure.md) struktura vyplňuje [ Afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit). Pokud data je příliš dlouhý a předáte atomicky základního protokolu chyba **WSAEMSGSIZE** se vrátí, a je odesláno žádná data.  
  
 Všimněte si, že úspěšné dokončení `SendTo` nevyplývá, že data byla úspěšně doručena.  
  
 `SendTo`používá se jenom na **SOCK_DGRAM** soketu odeslat datagram na konkrétní soket identifikovaný `lpSockAddr` parametr.  
  
 K odeslání vysílání (na **SOCK_DGRAM** pouze), adresu v `lpSockAddr` parametr by měl vytvořená pomocí speciální IP adresy **INADDR_BROADCAST** (definovanou v hlavičce Windows Sockets soubor rozhraní WINSOCK. H) společně s určený port číslo. Nebo, pokud `lpszHostAddress` parametr **NULL**, soketu je nakonfigurován pro všesměrové vysílání. Je obecně není vhodné pro všesměrového vysílání datagram překročení velikosti, kdy může docházet k fragmentace, což naznačuje, že data část datagram (s výjimkou hlavičky) by neměl být delší než 512 bajtů.  
  
 Chcete-li zpracovat adresy IPv6, použijte [CAsyncSocket::SendToEx](#sendtoex).  
  
##  <a name="sendtoex"></a>CAsyncSocket::SendToEx  
 Volání této funkce člen k odesílání dat na určité cílové místo (popisovačů adresy IPv6).  
  
```  
int SendToEx(
    const void* lpBuf,  
    int nBufLen,  
    UINT nHostPort,  
    LPCTSTR lpszHostAddress = NULL,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Vyrovnávací paměť obsahující data, která mají být odeslány.  
  
 `nBufLen`  
 Délka dat v `lpBuf` v bajtech.  
  
 `nHostPort`  
 Port identifikace aplikace soketu.  
  
 `lpszHostAddress`  
 Síťová adresa soketu, k němuž je připojen tento objekt: název počítače, jako je například "ftp.microsoft.com" nebo desítkovém číslo jako je například "128.56.22.8".  
  
 `nFlags`  
 Určuje způsob, jak při volání. Sémantika této funkce jsou závisí na možnostech soketu a `nFlags` parametr. Je vytvořený kombinací některý z následujících hodnot C++ `OR` operátor:  
  
- **MSG_DONTROUTE** Určuje, že data by neměl být předmětem směrování. Windows Sockets dodavatele můžete ignorovat tento příznak.  
  
- **MSG_OOB** odesílat data out-of-band ( **SOCK_STREAM** pouze).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nedojde k žádné chybě `SendToEx` vrátí celkový počet odeslaných znaků. (Všimněte si, že to může být menší než číslo indikován `nBufLen`.) Jinak hodnota **SOCKET_ERROR** se vrátí, a určitý kód chyby nelze získat voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEACCES** požadovaná adresa je adresa všesměrového vysílání, ale odpovídající příznak nebyla nastavena.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAEFAULT** `lpBuf` nebo `lpSockAddr` parametry nejsou součástí adresního prostoru uživatele, nebo `lpSockAddr` argument je příliš malý (menší než velikost [sockaddr –](../../mfc/reference/sockaddr-structure.md) struktura).  
  
- **WSAEINVAL** název hostitele je neplatný.  
  
- **WSAENETRESET** připojení, musí se obnovit, protože implementace rozhraní Windows Sockets ho vyřadit.  
  
- `WSAENOBUFS`Implementace rozhraní Windows Sockets hlásí zablokování vyrovnávací paměti.  
  
- **WSAENOTCONN** soket není připojen ( **SOCK_STREAM** pouze).  
  
- **WSAENOTSOCK** popisovač není soket.  
  
- **WSAEOPNOTSUPP MSG_OOB** byla zadána, ale soket není typu **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** byla vypnuta soket; není možné volat `SendToEx` na soket po `ShutDown` metoda byla volána s `nHow` nastavena na hodnotu 1 nebo 2.  
  
- **WSAEWOULDBLOCK** soketu je označen jako neblokový a bude blokovat požadovanou operaci.  
  
- **WSAEMSGSIZE** soketu je typu **SOCK_DGRAM**, a je větší než maximální počet podporovaný implementací rozhraní Windows Sockets datagram.  
  
- **WSAECONNABORTED** virtuální okruh byla přerušena z důvodu vypršení časového limitu nebo jiné chyby.  
  
- **WSAECONNRESET** virtuální okruh bylo resetováno na vzdálené straně.  
  
- **WSAEADDRNOTAVAIL** zadaná adresa není k dispozici z místního počítače.  
  
- **WSAEAFNOSUPPORT** adresy zadaný řady nelze použít s Tento soketu.  
  
- **WSAEDESTADDRREQ** cílové adresa je povinná.  
  
- **WSAENETUNREACH** síti není dosažitelné z tohoto hostitele v tuto chvíli.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je stejný jako [CAsyncSocket::SendTo](#sendto) s tím rozdílem, že zpracovává IPv6 adres i starší protokoly.  
  
 `SendToEx`se používá na sokety datagramů nebo datový proud a slouží k zápisu odchozích dat na soket. Pro sokety datagramu, se musí věnovat nepřesahující maximální velikost paketu IP základní podsítě, která je **iMaxUdpDg** element v [wsadata –](../../mfc/reference/wsadata-structure.md) struktura vyplňuje [ Afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit). Pokud data je příliš dlouhý a předáte atomicky základního protokolu chyba **WSAEMSGSIZE** se vrátí, a je odesláno žádná data.  
  
 Všimněte si, že úspěšné dokončení `SendToEx` nevyplývá, že data byla úspěšně doručena.  
  
 `SendToEx`používá se jenom na **SOCK_DGRAM** soketu odeslat datagram na konkrétní soket identifikovaný `lpSockAddr` parametr.  
  
 K odeslání vysílání (na **SOCK_DGRAM** pouze), adresu v `lpSockAddr` parametr by měl vytvořená pomocí speciální IP adresy **INADDR_BROADCAST** (definovanou v hlavičce Windows Sockets soubor rozhraní WINSOCK. H) společně s určený port číslo. Nebo, pokud `lpszHostAddress` parametr **NULL**, soketu je nakonfigurován pro všesměrové vysílání. Je obecně není vhodné pro všesměrového vysílání datagram překročení velikosti, kdy může docházet k fragmentace, což naznačuje, že data část datagram (s výjimkou hlavičky) by neměl být delší než 512 bajtů.  
  
##  <a name="setsockopt"></a>CAsyncSocket::SetSockOpt  
 Volání této funkce člen nastavit možnost soketu.  
  
```  
BOOL SetSockOpt(
    int nOptionName,  
    const void* lpOptionValue,  
    int nOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>Parametry  
 `nOptionName`  
 Možnost soketu pro kterou má být nastavena hodnotu.  
  
 `lpOptionValue`  
 Ukazatel do vyrovnávací paměti, ve kterém je zadána hodnota pro požadovanou možnost.  
  
 `nOptionLen`  
 Velikost `lpOptionValue` vyrovnávací paměti v bajtech.  
  
 `nLevel`  
 Úroveň, ve kterém je definována možnost; jsou pouze podporované úrovně **SOL_SOCKET** a **IPPROTO_TCP**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEFAULT** `lpOptionValue` není platný část adresní prostor procesu.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAEINVAL** `nLevel` není platný, nebo informace v `lpOptionValue` není platný.  
  
- **WSAENETRESET** připojení došlo k vypršení časového limitu při **SO_KEEPALIVE** nastavena.  
  
- **WSAENOPROTOOPT** možnost je neznámý nebo nepodporovaný. Konkrétně **SO_BROADCAST** nepodporuje sockets typu **SOCK_STREAM**, zatímco **SO_DONTLINGER**, **SO_KEEPALIVE**,  **SO_LINGER**, a **SO_OOBINLINE** nejsou podporovány na sockets typu **SOCK_DGRAM**.  
  
- **WSAENOTCONN** připojení bylo při resetování **SO_KEEPALIVE** nastavena.  
  
- **WSAENOTSOCK** popisovač není soket.  
  
### <a name="remarks"></a>Poznámky  
 `SetSockOpt`Nastaví aktuální hodnotu pro možnost soketu, přidružená k soketu libovolného typu, v libovolném stavu. I když možnosti může existovat na více úrovních protokol, definuje tato specifikace pouze možnosti, které existují na úrovni nejvyšší "soketu". Možnosti ovlivňují soketů operace, např. zda rychlé přijatá data v normálním datový proud, zda lze odesílat na soket zprávy všesměrového vysílání a tak dále.  
  
 Existují dva typy možností soketu: logická hodnota možnosti, které povolí nebo zakáže funkce nebo chování a možnosti, které vyžadují celočíselná hodnota nebo struktura. Logická hodnota možnost, povolit `lpOptionValue` odkazuje na nenulové hodnoty v celé číslo. Chcete-li zakázat možnost `lpOptionValue` odkazuje na celé číslo, která je rovna hodnotě nula. `nOptionLen`musí být roven **sizeof(BOOL)** logická hodnota možnosti. Pro další možnosti `lpOptionValue` odkazuje na celé číslo nebo struktura, která obsahuje požadovanou hodnotu pro možnost a `nOptionLen` je délka celé číslo nebo strukturu.  
  
 **SO_LINGER** ovládací prvky akce při unsent data je do fronty na soket a **zavřete** funkce je volána, zavřete soketu.  
  
 Ve výchozím nastavení, nemůže být vázán k soketu (najdete v části [vazby](#bind)) na místní adresu, která je již používán. V některých případech ale může být žádoucí "opakovaně použít" adresu tímto způsobem. Vzhledem k tomu, že každé připojení je jedinečně identifikovaný kombinací místní a vzdálené adresy, neexistuje žádný problém s má dva sokety vázaný se stejnou místní adresou tak dlouho, dokud vzdálené adresy se liší.  
  
 K informování implementace rozhraní Windows Sockets, **vazby** volání na soket nesmí povoleny, protože požadovaná adresa je již používán jinou soketu, aplikace by měla nastavena **SO_REUSEADDR**soketu možnost pro soket před vydáním **vazby** volání. Všimněte si, že je možnost interpretovat pouze v době **vazby** volání: je proto zbytečné (ale neškodné) Chcete-li nastavit možnost v soketů, které nesmějí být vázána na existující adresu a nebo obnovení nastavení možnost po **Vazby** volání nemá žádný vliv na to nebo jiných soketu.  
  
 Aplikace můžou požadovat, aby implementace rozhraní Windows Sockets povolit použití "keep-alive" paketů na připojení protokolu TCP (Transmission Control) zapnutím **SO_KEEPALIVE** soketu možnost. Implementace rozhraní Windows Sockets nemusí podporovat použití otevřených: Pokud ano, jsou specifické pro implementaci přesné sémantiku, ale musí být v souladu sekci 4.2.3.6 RFC 1122: "požadavky na hostiteli v síti Internet – komunikační vrstvy." Pokud připojení se ukončí v důsledku "otevřených" kód chyby **WSAENETRESET** je vrácen do jakékoli volání v průběhu na soket, a následných volání selže s **WSAENOTCONN**.  
  
 **TCP_NODELAY** možnost zakáže Nagle algoritmus. Nagle algoritmus se používá a snížit počet malých paketů odeslaných hostitel pomocí ukládání do vyrovnávací paměti nepotvrzených odeslal data, dokud plné velikosti paket odeslat. Ale některé aplikace tento algoritmus může mít dopad na výkon, a **TCP_NODELAY** je možné ho vypnout. Aplikace zapisovače by neměl nastavený **TCP_NODELAY** pokud dopad díky tomu je dobře srozumitelné a požadovaným způsobem, protože nastavení **TCP_NODELAY** může mít významný negativní dopad na výkon sítě . **TCP_NODELAY** je jedinou podporované možnosti soketu, která používá úroveň **IPPROTO_TCP**; všechny ostatní možnosti použít úroveň **SOL_SOCKET**.  
  
 Některé implementace rozhraní Windows Sockets napájení výstup informace o ladění, pokud **SO_DEBUG** je možnost nastavena jiná aplikace.  
  
 Jsou podporovány následující možnosti pro `SetSockOpt`. Typ jsou uvedeny typy dat používala `lpOptionValue`.  
  
|Hodnota|Typ|Význam|  
|-----------|----------|-------------|  
|**SO_BROADCAST**|**BOOL**|Povolit přenos zpráv všesměrového vysílání na soketu.|  
|**SO_DEBUG**|**BOOL**|Záznam ladicí informace.|  
|**SO_DONTLINGER**|**BOOL**|Nedošlo k blokování **Zavřít** čekání neodeslaných dat k odeslání. Nastavení této možnosti je ekvivalentní nastavení **SO_LINGER** s **l_onoff** nastavit na nulu.|  
|**SO_DONTROUTE**|**BOOL**|Nemáte směrovat: odeslání přímo na rozhraní.|  
|**SO_KEEPALIVE**|**BOOL**|Odešlete udržování otevřených připojení.|  
|**SO_LINGER**|**linger – struktura**|Linger – **Zavřít** Pokud unsent data nachází.|  
|**SO_OOBINLINE**|**BOOL**|Přijímat data out-of-band v normálním datový proud.|  
|**ASYNCHRONNÍ**|`int`|Zadejte velikost vyrovnávací paměti pro přijetí.|  
|**SO_REUSEADDR**|**BOOL**|Povolit soketu bylo vázané na adresu, která je již používán. (Viz [vazby](#bind).)|  
|**SO_SNDBUF**|`int`|Zadejte velikost vyrovnávací paměti pro odešle.|  
|**TCP_NODELAY**|**BOOL**|Zakáže algoritmus Nagle pro odeslání slučování.|  
  
 Možnosti Berkeley Software Distribution (BSD) není podporován pro `SetSockOpt` jsou:  
  
|Hodnota|Typ|Význam|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|Socket naslouchá.|  
|**SO_ERROR**|`int`|Získat stav chyby a zrušte.|  
|**SO_RCVLOWAT**|`int`|Zobrazí dolní meze.|  
|**SO_RCVTIMEO**|`int`|Přijímat vypršení časového limitu|  
|**SO_SNDLOWAT**|`int`|Odešlete dolní meze.|  
|**SO_SNDTIMEO**|`int`|Časového limitu odesílání.|  
|**SO_TYPE**|`int`|Typ soketu.|  
|**IP_OPTIONS**||Nastavte možnosti pole v hlavičce protokolu IP.|  
  
##  <a name="shutdown"></a>CAsyncSocket::ShutDown  
 Volání odešle tento – členská funkce zakázat, obdrží, nebo obojí na soketu.  
  
```  
BOOL ShutDown(int nHow = sends);
```  
  
### <a name="parameters"></a>Parametry  
 `nHow`  
 Příznak, který popisuje, jaké typy operací se již nebude povoleno, pomocí následujících výčtové hodnoty:  
  
- **obdrží = 0**  
  
- **Odešle = 1**  
  
- **jak = 2**  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním [GetLastError](#getlasterror). Následující chyby uplatní pro tento člen funkce:  
  
- **WSANOTINITIALISED** úspěšně [afxsocketinit –](../../mfc/reference/application-information-and-management.md#afxsocketinit) musí nastat před použitím toto rozhraní API.  
  
- **WSAENETDOWN** implementace rozhraní Windows Sockets zjistil, že síti podsystému došlo k chybě.  
  
- **WSAEINVAL** `nHow` není platný.  
  
- **WSAEINPROGRESS** blokování Windows Sockets operace probíhá.  
  
- **WSAENOTCONN** soket není připojen ( **SOCK_STREAM** pouze).  
  
- **WSAENOTSOCK** popisovač není soket.  
  
### <a name="remarks"></a>Poznámky  
 `ShutDown`se používá na všech typech sockets zakázat příjem, přenos nebo obojí. Pokud `nHow` je 0, následných obdrží na soket bude zakázán. Tato akce nemá vliv na nižších vrstvách protokolu.  
  
 Změnit není okno TCP pro protokol TCP (Transmission Control), a příchozích dat bude přijato (ale ne potvrzené) až do vyčerpání okna. Pro protokol UDP (User Datagram), příchozí datagramy jsou přijaty a zařazených do fronty. V žádném případě bude paketu ICMP chybě vygenerována. Pokud `nHow` je 1, následných zasílá nejsou povoleny. Sokety TCP bude odeslána najít. Nastavení `nHow` 2 zakáže oba odešle a přijme, jak je popsáno výše.  
  
 Všimněte si, že `ShutDown` nemá zavřete soketu a prostředky, které jsou připojené k soketu využívalo dokud **zavřete** je volána. Aplikace neměli spoléhat na se mohli znovu použít soket poté, co byl vypnut. Na konkrétní implementace rozhraní Windows Sockets není vyžadován pro podporu použití **Connect** na takové soketu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAsyncSocket::OnReceive](#onreceive).  
  
##  <a name="socket"></a>CASyncSocket::Socket  
 Přiděluje popisovač soketu.  
  
```  
BOOL Socket(
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    int nProtocolType = 0,  
    int nAddressFormat = PF_INET);
```  
  
### <a name="parameters"></a>Parametry  
 `nSocketType`  
 Určuje `SOCK_STREAM` nebo `SOCK_DGRAM`.  
  
 `lEvent`  
 Bitová maska, která určuje kombinaci události sítě, ve kterých je zájmu aplikace.  
  
- `FD_READ`: Chcete dostávat oznámení o připravenosti pro čtení.  
  
- `FD_WRITE`: Chcete dostávat oznámení o připravenosti pro zápis.  
  
- `FD_OOB`: Chcete dostávat oznámení o doručení out-of-band data.  
  
- `FD_ACCEPT`: Chcete dostávat oznámení o příchozích připojení.  
  
- `FD_CONNECT`: Chcete dostávat oznámení o dokončené připojení.  
  
- `FD_CLOSE`: Chcete dostávat oznámení o uzavření soketu.  
  
 `nProtocolType`  
 Protokol pro použití s soketů, které jsou specifické pro rodina uvedených adres.  
  
 `nAddressFormat`  
 Specifikace rodiny adres.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` v případě úspěchu `FALSE` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přiděluje popisovač soketu. Nevolá [CAsyncSocket::Bind](#bind) k vytvoření vazby soketu zadaná adresa, je třeba volat `Bind` později k vytvoření vazby soketu. Zadaná adresa. Můžete použít [CAsyncSocket::SetSockOpt](#setsockopt) nastavit možnost soketu předtím, než je vázána.  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CSocket – třída](../../mfc/reference/csocket-class.md)   
 [CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
