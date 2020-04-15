---
title: Třída CSocketAddr
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
ms.openlocfilehash: 66d33d62212389a2b0f318250c1c16a99167c6eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330682"
---
# <a name="csocketaddr-class"></a>Třída CSocketAddr

Tato třída poskytuje metody pro převod názvů hostitelů na adresy hostitelů, které podporují formáty IPv4 i IPV6.

## <a name="syntax"></a>Syntaxe

```
class CSocketAddr
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSocketAddr::CSocketAddr](#csocketaddr)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|Volání této metody převést zadaný název hostitele na adresu hostitele.|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Voláním této metody převeďte název hostitele IPv4 na adresu hostitele.|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Voláním této metody převeďte název hostitele IPv6 na adresu hostitele.|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Volání této metody vrátit ukazatel na určitý `addrinfo` prvek v seznamu.|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Volání této metody vrátit ukazatel `addrinfo` do seznamu.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje přístup agnostik verze IP pro vyhledávání síťových adres pro použití s funkcemi rozhraní API soketů systému Windows a obálky soketu v knihovnách.

Členové této třídy, které se používají k vyhledávání síťových adres, používají funkci [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)rozhraní API win32 . Ansi nebo UNICODE verze funkce je volána v závislosti na tom, zda je váš kód kompilován pro ANSI nebo UNICODE.

Tato třída podporuje síťové adresy IPv4 i IPv6.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsocket.h

## <a name="csocketaddrcsocketaddr"></a><a name="csocketaddr"></a>CSocketAddr::CSocketAddr

Konstruktor

```
CSocketAddr();
```

### <a name="remarks"></a>Poznámky

Vytvoří nový `CSocketAddr` objekt a inicializuje propojený seznam obsahující informace o odezvě o hostiteli.

## <a name="csocketaddrfindaddr"></a><a name="findaddr"></a>CSocketAddr::FindAddr

Volání této metody převést zadaný název hostitele na adresu hostitele.

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
Název hostitele nebo tečkovaná adresa IP.

*szPortOrServiceName*<br/>
Číslo portu nebo název služby na hostiteli.

*nPortNo*<br/>
Číslo portu

*příznaky*<br/>
0 nebo kombinace AI_PASSIVE, AI_CANONNAME nebo AI_NUMERICHOST.

*addr_family*<br/>
Rodina adres (například PF_INET).

*sock_type*<br/>
Typ soketu (například SOCK_STREAM).

*ai_proto*<br/>
protokolu (například IPPROTO_IP nebo IPPROTO_IPV6).

### <a name="return-value"></a>Návratová hodnota

Vrátí nulu, pokud je adresa úspěšně vypočtena. Vrátí nenulový kód chyby windows socket při selhání. V případě úspěchu je vypočtená adresa uložena v `CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo`propojeném seznamu, na který lze odkazovat pomocí a .

### <a name="remarks"></a>Poznámky

Parametr název hostitele může být ve formátu IPv4 nebo IPv6. Tato metoda volá win32 api funkce [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) k provedení převodu.

## <a name="csocketaddrfindinet4addr"></a><a name="findinet4addr"></a>CSocketAddr::FindINET4Addr

Voláním této metody převeďte název hostitele IPv4 na adresu hostitele.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parametry

*szHost*<br/>
Název hostitele nebo tečkovaná adresa IP.

*nPortNo*<br/>
Číslo portu

*příznaky*<br/>
0 nebo kombinace AI_PASSIVE, AI_CANONNAME nebo AI_NUMERICHOST.

*sock_type*<br/>
Typ soketu (například SOCK_STREAM).

### <a name="return-value"></a>Návratová hodnota

Vrátí nulu, pokud je adresa úspěšně vypočtena. Vrátí nenulový kód chyby windows socket při selhání. V případě úspěchu je vypočtená adresa uložena v `CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo`propojeném seznamu, na který lze odkazovat pomocí a .

### <a name="remarks"></a>Poznámky

Tato metoda volá win32 api funkce [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) k provedení převodu.

## <a name="csocketaddrfindinet6addr"></a><a name="findinet6addr"></a>CSocketAddr::FindINET6Addr

Voláním této metody převeďte název hostitele IPv6 na adresu hostitele.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parametry

*szHost*<br/>
Název hostitele nebo tečkovaná adresa IP.

*nPortNo*<br/>
Číslo portu

*příznaky*<br/>
0 nebo kombinace AI_PASSIVE, AI_CANONNAME nebo AI_NUMERICHOST.

*sock_type*<br/>
Typ soketu (například SOCK_STREAM).

### <a name="return-value"></a>Návratová hodnota

Vrátí nulu, pokud je adresa úspěšně vypočtena. Vrátí nenulový kód chyby windows socket při selhání. V případě úspěchu je vypočtená adresa uložena v `CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo`propojeném seznamu, na který lze odkazovat pomocí a .

### <a name="remarks"></a>Poznámky

Tato metoda volá win32 api funkce [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) k provedení převodu.

## <a name="csocketaddrgetaddrinfo"></a><a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo

Volání této metody vrátit ukazatel na určitý `addrinfo` prvek v seznamu.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Odkaz na konkrétní prvek v seznamu [addrinfo.](/windows/win32/api/ws2def/ns-ws2def-addrinfow)

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `addrinfo` strukturu, na kterou odkazuje *nIndex* v propojeném seznamu obsahujícím informace o odezvě o hostiteli.

## <a name="csocketaddrgetaddrinfolist"></a><a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList

Volání této metody vrátit ukazatel `addrinfo` do seznamu.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na propojený seznam jedné `addrinfo` nebo více struktur obsahujících informace o odezvě o hostiteli. Další informace naleznete v tématu [addrinfo structure](/windows/win32/api/ws2def/ns-ws2def-addrinfow).

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
