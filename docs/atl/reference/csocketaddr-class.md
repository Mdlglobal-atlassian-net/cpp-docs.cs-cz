---
title: CSocketAddr – třída
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
ms.openlocfilehash: 2a131323e64b1bf67f76ec92e7a3e4fcba899661
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496350"
---
# <a name="csocketaddr-class"></a>CSocketAddr – třída

Tato třída poskytuje metody pro převod názvů hostitelů na adresy hostitelů, které podporují formáty IPv4 i IPV6.

## <a name="syntax"></a>Syntaxe

```
class CSocketAddr
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSocketAddr::CSocketAddr](#csocketaddr)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|Voláním této metody převedete zadaný název hostitele na adresu hostitele.|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Voláním této metody převedete název hostitele IPv4 na adresu hostitele.|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Voláním této metody převedete název hostitele IPv6 na adresu hostitele.|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Voláním této metody vrátíte ukazatel na konkrétní prvek v `addrinfo` seznamu.|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Voláním této metody vrátíte ukazatel na `addrinfo` seznam.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje přístup nezávislá verze protokolu IP pro vyhledávání síťových adres pro použití s funkcemi rozhraní Windows Sockets API a obálky soketů v knihovnách.

Členové této třídy, které se používají k vyhledání síťových adres, používají funkci Win32 API [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo). Verze funkce ANSI nebo UNICODE je volána v závislosti na tom, zda je kód zkompilován pro ANSI nebo UNICODE.

Tato třída podporuje jak síťové adresy IPv4 andIPv6.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atlsocket. h

##  <a name="csocketaddr"></a>CSocketAddr::CSocketAddr

Konstruktor

```
CSocketAddr();
```

### <a name="remarks"></a>Poznámky

Vytvoří nový `CSocketAddr` objekt a inicializuje propojený seznam obsahující informace o odezvě hostitele.

##  <a name="findaddr"></a>CSocketAddr::FindAddr

Voláním této metody převedete zadaný název hostitele na adresu hostitele.

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
Název hostitele nebo tečkovaná IP adresa.

*szPortOrServiceName*<br/>
Číslo portu nebo název služby na hostiteli.

*nPortNo*<br/>
Číslo portu.

*Flag*<br/>
0 nebo kombinace AI_PASSIVE, AI_CANONNAME nebo AI_NUMERICHOST.

*addr_family*<br/>
Rodina adres (například PF_INET).

*sock_type*<br/>
Typ soketu (například SOCK_STREAM).

*ai_proto*<br/>
Protokol (například IPPROTO_IP nebo IPPROTO_IPV6).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula, pokud je adresa úspěšně vypočítána. Vrátí nenulový kód chyby soketu Windows při selhání. V případě úspěchu je vypočítaná adresa uložena v propojeném seznamu, na který lze odkazovat `CSocketAddr::GetAddrInfoList` pomocí `CSocketAddr::GetAddrInfo`a.

### <a name="remarks"></a>Poznámky

Parametr názvu hostitele může být ve formátu IPv4 nebo IPv6. Tato metoda volá funkci Win32 API [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) k provedení převodu.

##  <a name="findinet4addr"></a>CSocketAddr::FindINET4Addr

Voláním této metody převedete název hostitele IPv4 na adresu hostitele.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parametry

*szHost*<br/>
Název hostitele nebo tečkovaná IP adresa.

*nPortNo*<br/>
Číslo portu.

*Flag*<br/>
0 nebo kombinace AI_PASSIVE, AI_CANONNAME nebo AI_NUMERICHOST.

*sock_type*<br/>
Typ soketu (například SOCK_STREAM).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula, pokud je adresa úspěšně vypočítána. Vrátí nenulový kód chyby soketu Windows při selhání. V případě úspěchu je vypočítaná adresa uložena v propojeném seznamu, na který lze odkazovat `CSocketAddr::GetAddrInfoList` pomocí `CSocketAddr::GetAddrInfo`a.

### <a name="remarks"></a>Poznámky

Tato metoda volá funkci Win32 API [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) k provedení převodu.

##  <a name="findinet6addr"></a>CSocketAddr::FindINET6Addr

Voláním této metody převedete název hostitele IPv6 na adresu hostitele.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parametry

*szHost*<br/>
Název hostitele nebo tečkovaná IP adresa.

*nPortNo*<br/>
Číslo portu.

*Flag*<br/>
0 nebo kombinace AI_PASSIVE, AI_CANONNAME nebo AI_NUMERICHOST.

*sock_type*<br/>
Typ soketu (například SOCK_STREAM).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula, pokud je adresa úspěšně vypočítána. Vrátí nenulový kód chyby soketu Windows při selhání. V případě úspěchu je vypočítaná adresa uložena v propojeném seznamu, na který lze odkazovat `CSocketAddr::GetAddrInfoList` pomocí `CSocketAddr::GetAddrInfo`a.

### <a name="remarks"></a>Poznámky

Tato metoda volá funkci Win32 API [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) k provedení převodu.

##  <a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo

Voláním této metody vrátíte ukazatel na konkrétní prvek v `addrinfo` seznamu.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Odkaz na konkrétní prvek v seznamu [addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow) .

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `addrinfo` strukturu, na kterou odkazuje *nIndex* v propojeném seznamu, který obsahuje informace o odpovědi hostitele.

##  <a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList

Voláním této metody vrátíte ukazatel na `addrinfo` seznam.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na propojený seznam jedné nebo více `addrinfo` struktur obsahující informace o odezvě hostitele. Další informace najdete v tématu [Struktura addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow).

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
