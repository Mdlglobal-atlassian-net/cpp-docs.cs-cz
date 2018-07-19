---
title: Makra výměny dat registru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7473bed5e4bf973dcea4d186e9b5b3367fb03ff1
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880356"
---
# <a name="registry-data-exchange-macros"></a>Makra výměny dat registru
Tato makra výměny dat registru operacím.  
  
|||  
|-|-|  
|[BEGIN_RDX_MAP](#begin_rdx_map)|Označuje začátek toho mapy výměny dat registru.|  
|[END_RDX_MAP](#end_rdx_map)|Označuje konec mapování výměny dat registru.|  
|[RDX_BINARY](#rdx_binary)|Zadaná položka registru se přidruží k zadané členské proměnné typu BYTE.|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Přidruží zadaný člen proměnné typu CString zadaná položka registru.|  
|[RDX_DWORD](#rdx_dword)|Přidruží zadaný člen proměnné typu DWORD zadaná položka registru.|  
|[RDX_TEXT](#rdx_text)|Přidruží zadaný člen proměnné typu TCHAR zadaná položka registru.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlplus.h  
   
##  <a name="begin_rdx_map"></a>  BEGIN_RDX_MAP  
 Označuje začátek toho mapy výměny dat registru.  
  
```
BEGIN_RDX_MAP
```  
  
### <a name="remarks"></a>Poznámky  
 Následující makra jsou používány ve výměny dat registru mapy čtení a zápis položky systémového registru:  
  
|– Makro|Popis|  
|-----------|-----------------|  
|[RDX_BINARY](#rdx_binary)|Zadaná položka registru se přidruží k zadané členské proměnné typu BYTE.|  
|[RDX_DWORD](#rdx_dword)|Přidruží zadaný člen proměnné typu DWORD zadaná položka registru.|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Přidruží zadaný člen proměnné typu CString zadaná položka registru.|  
|[RDX_TEXT](#rdx_text)|Přidruží zadaný člen proměnné typu TCHAR zadaná položka registru.|  
  
 Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), nebo členská funkce se stejným názvem, který vytvořil BEGIN_RDX_MAP a END_RDX_MAP makra, by měla sloužit vždy, když je váš kód pro výměnu dat mezi systémovým registrem a zadané v objektu map RDX proměnné.  
  
##  <a name="end_rdx_map"></a>  END_RDX_MAP  
 Označuje konec mapování výměny dat registru.  
  
```
END_RDX_MAP
```  
  
##  <a name="rdx_binary"></a>  RDX_BINARY  
 Zadaná položka registru se přidruží k zadané členské proměnné typu BYTE.  
  
```
RDX_BINARY(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parametry  
 *kořenovým klíčem*  
 Kořenový klíč registru.  
  
 *podklíč*  
 Podklíč registru.  
  
 *Název hodnoty*  
 Klíč registru.  
  
 *Člen*  
 Členské proměnné, které chcete přidružit k zadaná položka registru.  
  
 *member_size*  
 Velikost v bajtech, členské proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro se používá ve spojení s makry BEGIN_RDX_MAP a END_RDX_MAP Pokud chcete přidružit k členské proměnné položky daného registru. Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), nebo členská funkce se stejným názvem, který vytvořil BEGIN_RDX_MAP a END_RDX_MAP makra, by měla sloužit k provedení výměny dat mezi systémovým registrem a členské proměnné v RDX map.  
  
##  <a name="rdx_cstring_text"></a>  RDX_CSTRING_TEXT  
 Přidruží zadaný člen proměnné typu CString zadaná položka registru.  
  
```
RDX_CSTRING_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parametry  
 *kořenovým klíčem*  
 Kořenový klíč registru.  
  
 *podklíč*  
 Podklíč registru.  
  
 *Název hodnoty*  
 Klíč registru.  
  
 *Člen*  
 Členské proměnné, které chcete přidružit k zadaná položka registru.  
  
 *member_size*  
 Velikost v bajtech, členské proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro se používá ve spojení s makry BEGIN_RDX_MAP a END_RDX_MAP Pokud chcete přidružit k členské proměnné položky daného registru. Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), nebo členská funkce se stejným názvem, který vytvořil BEGIN_RDX_MAP a END_RDX_MAP makra, by měla sloužit k provedení výměny dat mezi systémovým registrem a členské proměnné v RDX map.  
  
##  <a name="rdx_dword"></a>  RDX_DWORD  
 Přidruží zadaný člen proměnné typu DWORD zadaná položka registru.  
  
```
RDX_DWORD(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parametry  
 *kořenovým klíčem*  
 Kořenový klíč registru.  
  
 *podklíč*  
 Podklíč registru.  
  
 *Název hodnoty*  
 Klíč registru.  
  
 *Člen*  
 Členské proměnné, které chcete přidružit k zadaná položka registru.  
  
 *member_size*  
 Velikost v bajtech, členské proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro se používá ve spojení s makry BEGIN_RDX_MAP a END_RDX_MAP Pokud chcete přidružit k členské proměnné položky daného registru. Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), nebo členská funkce se stejným názvem, který vytvořil BEGIN_RDX_MAP a END_RDX_MAP makra, by měla sloužit k provedení výměny dat mezi systémovým registrem a členské proměnné v RDX map.  
  
##  <a name="rdx_text"></a>  RDX_TEXT  
 Přidruží zadaný člen proměnné typu TCHAR zadaná položka registru.  
  
```
RDX_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parametry  
 *kořenovým klíčem*  
 Kořenový klíč registru.  
  
 *podklíč*  
 Podklíč registru.  
  
 *Název hodnoty*  
 Klíč registru.  
  
 *Člen*  
 Členské proměnné, které chcete přidružit k zadaná položka registru.  
  
 *member_size*  
 Velikost v bajtech, členské proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro se používá ve spojení s makry BEGIN_RDX_MAP a END_RDX_MAP Pokud chcete přidružit k členské proměnné položky daného registru. Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), nebo členská funkce se stejným názvem, který vytvořil BEGIN_RDX_MAP a END_RDX_MAP makra, by měla sloužit k provedení výměny dat mezi systémovým registrem a členské proměnné v RDX map.  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)   
 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)







