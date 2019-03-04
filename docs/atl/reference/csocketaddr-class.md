---
title: Csocketaddr – třída
ms.date: 10/22/2018
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
ms.openlocfilehash: e94d92b11a7f200edb1815a0b384d0fc0428001f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280326"
---
# <a name="csocketaddr-class"></a>Csocketaddr – třída

Tato třída poskytuje metody pro převod názvy hostitelů na hostitelské adresy podporující formáty IPv4 a IPV6.

## <a name="syntax"></a>Syntaxe

```
class CSocketAddr
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSocketAddr::CSocketAddr](#csocketaddr)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|Voláním této metody lze převést zadaný název hostitele na adresu hostitele.|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Volání této metody k převodu názvu hostitele IPv4 adresa hostitele.|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Voláním této metody lze převést název hostitele IPv6 adresa hostitele.|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Voláním této metody vrátí ukazatel na konkrétní element v `addrinfo` seznamu.|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Voláním této metody vrátí ukazatel `addrinfo` seznamu.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje verzi protokolu IP, že bez přístupu pro vyhledávání síťových adres pro použití se službou Windows sockets – funkce rozhraní API a obálky soketu v knihovnách.

Členové této třídy, které se používají k vyhledání síťové adresy používat funkce rozhraní Win32 API [getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo). ANSI nebo UNICODE verze funkce je volána v závislosti na tom, jestli váš kód je zkompilován pro ANSI nebo UNICODE.

Tato třída podporuje obě adresy IPv4 andIPv6 sítě.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsocket.h

##  <a name="csocketaddr"></a>  CSocketAddr::CSocketAddr

Konstruktor

```
CSocketAddr();
```

### <a name="remarks"></a>Poznámky

Vytvoří novou `CSocketAddr` objektu a inicializuje propojený seznam, který obsahuje odpověď informace o hostiteli.

##  <a name="findaddr"></a>  CSocketAddr::FindAddr

Voláním této metody lze převést zadaný název hostitele na adresu hostitele.

```
int FindAddr(
    const TCHAR *szHost,
    const TCHAR *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const TCHAR *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```

### <a name="parameters"></a>Parametry

*szHost*<br/>
Název hostitele nebo tečkovaná IP adresu.

*szPortOrServiceName*<br/>
Číslo portu nebo názvu služby na hostiteli.

*nPortNo*<br/>
Číslo portu.

*příznaky*<br/>
0 nebo kombinaci AI_PASSIVE, AI_CANONNAME nebo AI_NUMERICHOST.

*addr_family*<br/>
Rodina (například PF_INET) adres.

*sock_type*<br/>
Typ soketu (například SOCK_STREAM).

*ai_proto*<br/>
Protokol (například IPPROTO_IP nebo IPPROTO_IPV6).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula, pokud se úspěšně počítá adresu. Vrátí nenulový kód chyby soketu Windows při selhání. Pokud úspěšné, adresu počítané je uložen v propojeném seznamu, který může být odkazováno pomocí `CSocketAddr::GetAddrInfoList` a `CSocketAddr::GetAddrInfo`.

### <a name="remarks"></a>Poznámky

Parametr název hostitele může být ve formátu IPv4 nebo IPv6. Tato metoda volá funkci Win32 API [getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) k provedení převodu.

##  <a name="findinet4addr"></a>  CSocketAddr::FindINET4Addr

Volání této metody k převodu názvu hostitele IPv4 adresa hostitele.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parametry

*szHost*<br/>
Název hostitele nebo tečkovaná IP adresu.

*nPortNo*<br/>
Číslo portu.

*příznaky*<br/>
0 nebo kombinaci AI_PASSIVE, AI_CANONNAME nebo AI_NUMERICHOST.

*sock_type*<br/>
Typ soketu (například SOCK_STREAM).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula, pokud se úspěšně počítá adresu. Vrátí nenulový kód chyby soketu Windows při selhání. Pokud úspěšné, adresu počítané je uložen v propojeném seznamu, který může být odkazováno pomocí `CSocketAddr::GetAddrInfoList` a `CSocketAddr::GetAddrInfo`.

### <a name="remarks"></a>Poznámky

Tato metoda volá funkci Win32 API [getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) k provedení převodu.

##  <a name="findinet6addr"></a>  CSocketAddr::FindINET6Addr

Voláním této metody lze převést název hostitele IPv6 adresa hostitele.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parametry

*szHost*<br/>
Název hostitele nebo tečkovaná IP adresu.

*nPortNo*<br/>
Číslo portu.

*příznaky*<br/>
0 nebo kombinaci AI_PASSIVE, AI_CANONNAME nebo AI_NUMERICHOST.

*sock_type*<br/>
Typ soketu (například SOCK_STREAM).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula, pokud se úspěšně počítá adresu. Vrátí nenulový kód chyby soketu Windows při selhání. Pokud úspěšné, adresu počítané je uložen v propojeném seznamu, který může být odkazováno pomocí `CSocketAddr::GetAddrInfoList` a `CSocketAddr::GetAddrInfo`.

### <a name="remarks"></a>Poznámky

Tato metoda volá funkci Win32 API [getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) k provedení převodu.

##  <a name="getaddrinfo"></a>  CSocketAddr::GetAddrInfo

Voláním této metody vrátí ukazatel na konkrétní element v `addrinfo` seznamu.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Odkaz na konkrétní elementu v [addrinfo](/windows/desktop/api/ws2def/ns-ws2def-addrinfoa) seznamu.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel `addrinfo` struktura odkazuje *nIndex* v propojeném seznamu, který obsahuje odpověď informace o hostiteli.

##  <a name="getaddrinfolist"></a>  CSocketAddr::GetAddrInfoList

Voláním této metody vrátí ukazatel `addrinfo` seznamu.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na propojený seznam jednoho nebo více `addrinfo` struktury obsahující odpovědi informace o hostiteli. Další informace najdete v tématu [addrinfo struktura](/windows/desktop/api/ws2def/ns-ws2def-addrinfoa).

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
