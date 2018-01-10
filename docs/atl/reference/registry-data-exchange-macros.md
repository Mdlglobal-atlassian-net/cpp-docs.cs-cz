---
title: "Výměna dat registru makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
dev_langs: C++
helpviewer_keywords: RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0bc12c48ef628a42c309c44ce0fc37abda9b6690
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="registry-data-exchange-macros"></a>Makra Exchange dat registru
Tyto makra provádět operace výměny dat registru.  
  
|||  
|-|-|  
|[BEGIN_RDX_MAP](#begin_rdx_map)|Označuje začátek mapy výměny dat registru.|  
|[END_RDX_MAP](#end_rdx_map)|Označuje konec mapy výměny dat registru.|  
|[RDX_BINARY](#rdx_binary)|Zadaná položka registru přidruží zadané členské proměnné typu BAJTŮ.|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Zadaná položka registru přidruží proměnné typu CString zadaného člena.|  
|[RDX_DWORD](#rdx_dword)|Přidruží zadaná položka registru typu DWORD s hodnotou proměnné zadaného člena.|  
|[RDX_TEXT](#rdx_text)|Zadaná položka registru přidruží proměnné typu TCHAR – zadaného člena.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlplus.h  
   
##  <a name="begin_rdx_map"></a>BEGIN_RDX_MAP  
 Označuje začátek mapy výměny dat registru.  
  
```
BEGIN_RDX_MAP
```  
  
### <a name="remarks"></a>Poznámky  
 Následující makra se používají v rámci mapy výměny dat registru ke čtení a zápisu položky systémového registru:  
  
|– Makro|Popis|  
|-----------|-----------------|  
|[RDX_BINARY](#rdx_binary)|Zadaná položka registru přidruží zadané členské proměnné typu BAJTŮ.|  
|[RDX_DWORD](#rdx_dword)|Přidruží zadaná položka registru typu DWORD s hodnotou proměnné zadaného člena.|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Zadaná položka registru přidruží proměnné typu CString zadaného člena.|  
|[RDX_TEXT](#rdx_text)|Zadaná položka registru přidruží proměnné typu TCHAR – zadaného člena.|  
  
 Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), nebo funkci člen se stejným názvem vytvořené `BEGIN_RDX_MAP` a `END_RDX_MAP` makra, se použije vždy, když je váš kód pro výměnu dat mezi systémového registru a proměnné určené v mapě RDX.  
  
##  <a name="end_rdx_map"></a>END_RDX_MAP  
 Označuje konec mapy výměny dat registru.  
  
```
END_RDX_MAP
```  
  
##  <a name="rdx_binary"></a>RDX_BINARY  
 Zadaná položka registru přidruží zadané členské proměnné typu BAJTŮ.  
  
```
RDX_BINARY(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parametry  
 `rootkey`  
 Kořen klíče registru.  
  
 `subkey`  
 Podklíč registru.  
  
 `valuename`  
 Klíč registru.  
  
 `member`  
 Členské proměnné přidružit zadaná položka registru.  
  
 `member_size`  
 Velikost v bajtech členské proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro se používá ve spojení s `BEGIN_RDX_MAP` a `END_RDX_MAP` makra přidružit členské proměnné s položkou daného registru. Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), nebo funkci člen se stejným názvem vytvořené `BEGIN_RDX_MAP` a `END_RDX_MAP` makra, se má použít k provést výměnu dat mezi systémového registru a člen proměnné v mapě RDX.  
  
##  <a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT  
 Zadaná položka registru přidruží proměnné typu CString zadaného člena.  
  
```
RDX_CSTRING_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parametry  
 `rootkey`  
 Kořen klíče registru.  
  
 `subkey`  
 Podklíč registru.  
  
 `valuename`  
 Klíč registru.  
  
 `member`  
 Členské proměnné přidružit zadaná položka registru.  
  
 `member_size`  
 Velikost v bajtech členské proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro se používá ve spojení s `BEGIN_RDX_MAP` a `END_RDX_MAP` makra přidružit členské proměnné s položkou daného registru. Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), nebo funkci člen se stejným názvem vytvořené `BEGIN_RDX_MAP` a `END_RDX_MAP` makra, se má použít k provést výměnu dat mezi systémového registru a člen proměnné v mapě RDX.  
  
##  <a name="rdx_dword"></a>RDX_DWORD  
 Přidruží zadaná položka registru typu DWORD s hodnotou proměnné zadaného člena.  
  
```
RDX_DWORD(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parametry  
 `rootkey`  
 Kořen klíče registru.  
  
 `subkey`  
 Podklíč registru.  
  
 `valuename`  
 Klíč registru.  
  
 `member`  
 Členské proměnné přidružit zadaná položka registru.  
  
 `member_size`  
 Velikost v bajtech členské proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro se používá ve spojení s `BEGIN_RDX_MAP` a `END_RDX_MAP` makra přidružit členské proměnné s položkou daného registru. Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), nebo funkci člen se stejným názvem vytvořené `BEGIN_RDX_MAP` a `END_RDX_MAP` makra, se má použít k provést výměnu dat mezi systémového registru a člen proměnné v mapě RDX.  
  
##  <a name="rdx_text"></a>RDX_TEXT  
 Zadaná položka registru přidruží proměnné typu TCHAR – zadaného člena.  
  
```
RDX_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parametry  
 `rootkey`  
 Kořen klíče registru.  
  
 `subkey`  
 Podklíč registru.  
  
 `valuename`  
 Klíč registru.  
  
 `member`  
 Členské proměnné přidružit zadaná položka registru.  
  
 `member_size`  
 Velikost v bajtech členské proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro se používá ve spojení s `BEGIN_RDX_MAP` a `END_RDX_MAP` makra přidružit členské proměnné s položkou daného registru. Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), nebo funkci člen se stejným názvem vytvořené `BEGIN_RDX_MAP` a `END_RDX_MAP` makra, se má použít k provést výměnu dat mezi systémového registru a člen proměnné v mapě RDX.  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)   
 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)







