---
title: "Třída CSocketAddr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
dev_langs:
- C++
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cadd771e6c3a9e7addb6893b4427183cfff293c9
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="csocketaddr-class"></a>CSocketAddr – třída
Tato třída poskytuje metody pro převod názvy hostitelů na hostitelské adresy, podpora formátů oba protokoly IPv4 a IPV6.  
  
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
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Voláním této metody lze převést název hostitele IPv4 adresu hostitele.|  
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Voláním této metody lze převést název hostitele IPv6 adresa hostitele.|  
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Volání této metody vrátit ukazatel na konkrétní prvek, **addrinfo** seznamu.|  
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Volání této metody vrátit ukazatel **addrinfo** seznamu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje IP verze lhostejné přístup pro vyhledávání síťových adres pro použití v systému Windows sockets – funkce rozhraní API a soketu obálky v knihovnách.  
  
 Členy této třídy, které se používají k vyhledání síťové adresy pomocí funkce rozhraní API Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520).  
  
 Tato třída podporuje obě adresy IPv4 andIPv6 sítě.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsocket.h  
  
##  <a name="csocketaddr"></a>CSocketAddr::CSocketAddr  
 Konstruktor  
  
```
CSocketAddr();
```  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří nový `CSocketAddr` objektu a inicializuje odkazovaného seznamu obsahující odpovědi informace o hostiteli.  
  
##  <a name="findaddr"></a>CSocketAddr::FindAddr  
 Voláním této metody lze převést zadaný název hostitele na adresu hostitele.  
  
```
int FindAddr(
    const char *szHost,
    const char *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const char *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```  
  
### <a name="parameters"></a>Parametry  
 `szHost`  
 Název hostitele nebo desítkovém IP adresu.  
  
 *szPortOrServiceName*  
 Číslo portu nebo názvu služby na hostiteli.  
  
 `nPortNo`  
 Číslo portu.  
  
 `flags`  
 0 nebo kombinaci AI_PASSIVE, AI_CANONNAME nebo AI_NUMERICHOST.  
  
 *addr_family*  
 Rodina (například PF_INET) adres.  
  
 `sock_type`  
 Typ soketu (například SOCK_STREAM).  
  
 *ai_proto*  
 Protokol (například IPPROTO_IP nebo IPPROTO_IPV6).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu adresu se vypočítává úspěšně. Vrátí nenulový kód chyby systému Windows soketu při selhání. Pokud úspěšné, adresu počítané je uložen v odkazovaného seznamu, který se dá odkazovat pomocí `CSocketAddr::GetAddrInfoList` a `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Poznámky  
 Parametr název hostitele může být ve formátu protokolu IPv4 nebo IPv6. Tato metoda volá funkce rozhraní Win32 API [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) provést převod.  
  
##  <a name="findinet4addr"></a>CSocketAddr::FindINET4Addr  
 Voláním této metody lze převést název hostitele IPv4 adresu hostitele.  
  
```
int FindINET4Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>Parametry  
 `szHost`  
 Název hostitele nebo desítkovém IP adresu.  
  
 `nPortNo`  
 Číslo portu.  
  
 `flags`  
 0 nebo kombinaci AI_PASSIVE, AI_CANONNAME nebo AI_NUMERICHOST.  
  
 `sock_type`  
 Typ soketu (například SOCK_STREAM).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu adresu se vypočítává úspěšně. Vrátí nenulový kód chyby systému Windows soketu při selhání. Pokud úspěšné, adresu počítané je uložen v odkazovaného seznamu, který se dá odkazovat pomocí `CSocketAddr::GetAddrInfoList` a `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá funkce rozhraní Win32 API [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) provést převod.  
  
##  <a name="findinet6addr"></a>CSocketAddr::FindINET6Addr  
 Voláním této metody lze převést název hostitele IPv6 adresa hostitele.  
  
```
int FindINET6Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>Parametry  
 `szHost`  
 Název hostitele nebo desítkovém IP adresu.  
  
 `nPortNo`  
 Číslo portu.  
  
 `flags`  
 0 nebo kombinaci AI_PASSIVE, AI_CANONNAME nebo AI_NUMERICHOST.  
  
 `sock_type`  
 Typ soketu (například SOCK_STREAM).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu adresu se vypočítává úspěšně. Vrátí nenulový kód chyby systému Windows soketu při selhání. Pokud úspěšné, adresu počítané je uložen v odkazovaného seznamu, který se dá odkazovat pomocí `CSocketAddr::GetAddrInfoList` a `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá funkce rozhraní Win32 API [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) provést převod.  
  
##  <a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo  
 Volání této metody vrátit ukazatel na konkrétní prvek, **addrinfo** seznamu.  
  
```
addrinfo* const GetAddrInfoint nIndex = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Odkaz na konkrétní prvek, [addrinfo](http://msdn.microsoft.com/library/windows/desktop/ms737530) seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel **addrinfo** struktura odkazuje `nIndex` v seznamu propojené obsahující odpovědi informace o hostiteli.  
  
##  <a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList  
 Volání této metody vrátit ukazatel **addrinfo** seznamu.  
  
```
addrinfo* const GetAddrInfoList() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na odkazovaného seznamu jednoho nebo více `addrinfo` struktury obsahující odpovědi informace o hostiteli. Další informace najdete v tématu [addrinfo struktura](https://msdn.microsoft.com/library/windows/desktop/ms737530).
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
