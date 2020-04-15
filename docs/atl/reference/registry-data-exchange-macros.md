---
title: Makra výměny dat registru
ms.date: 11/04/2016
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
ms.openlocfilehash: a7d580e4907cec40f97c0cead616665fff7b8a01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326073"
---
# <a name="registry-data-exchange-macros"></a>Makra výměny dat registru

Tato makra provádějí operace výměny dat registru.

|||
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|Označuje začátek mapy výměny dat registru.|
|[END_RDX_MAP](#end_rdx_map)|Označuje konec mapy výměny dat registru.|
|[RDX_BINARY](#rdx_binary)|Přidruží zadanou položku registru k zadané členské proměnné typu BYTE.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Přidruží zadanou položku registru k zadané členské proměnné typu CString.|
|[RDX_DWORD](#rdx_dword)|Přidruží zadanou položku registru k zadané členské proměnné typu DWORD.|
|[RDX_TEXT](#rdx_text)|Přidruží zadanou položku registru k zadané členské proměnné typu TCHAR.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlplus.h

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a>BEGIN_RDX_MAP

Označuje začátek mapy výměny dat registru.

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>Poznámky

Následující makra se používají v rámci mapy Výměny dat registru ke čtení a zápisu položek v systémovém registru:

|Makro|Popis|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|Přidruží zadanou položku registru k zadané členské proměnné typu BYTE.|
|[RDX_DWORD](#rdx_dword)|Přidruží zadanou položku registru k zadané členské proměnné typu DWORD.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Přidruží zadanou položku registru k zadané členské proměnné typu CString.|
|[RDX_TEXT](#rdx_text)|Přidruží zadanou položku registru k zadané členské proměnné typu TCHAR.|

Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)nebo členská funkce se stejným názvem vytvořená BEGIN_RDX_MAP a END_RDX_MAP makra by měly být použity vždy, když váš kód potřebuje výměnu dat mezi systémovým registrem a proměnnými zadanými v mapě RDX.

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a>END_RDX_MAP

Označuje konec mapy výměny dat registru.

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a>RDX_BINARY

Přidruží zadanou položku registru k zadané členské proměnné typu BYTE.

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*kořenový klíč*<br/>
Kořenový klíč registru.

*Podklíč*<br/>
Podklíč registru.

*Valuename*<br/>
Klíč registru.

*Členské*<br/>
Proměnná člena, kterou chcete přidružit k zadané položce registru.

*member_size*<br/>
Velikost proměnné člena v bajtech.

### <a name="remarks"></a>Poznámky

Toto makro se používá ve spojení s BEGIN_RDX_MAP a END_RDX_MAP makra k přidružení členské proměnné k dané položce registru. Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)nebo členská funkce se stejným názvem vytvořená makrami BEGIN_RDX_MAP a END_RDX_MAP by měly být použity k provádění výměny dat mezi systémovým registrem a členskými proměnnými v mapě RDX.

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT

Přidruží zadanou položku registru k zadané členské proměnné typu CString.

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*kořenový klíč*<br/>
Kořenový klíč registru.

*Podklíč*<br/>
Podklíč registru.

*Valuename*<br/>
Klíč registru.

*Členské*<br/>
Proměnná člena, kterou chcete přidružit k zadané položce registru.

*member_size*<br/>
Velikost proměnné člena v bajtech.

### <a name="remarks"></a>Poznámky

Toto makro se používá ve spojení s BEGIN_RDX_MAP a END_RDX_MAP makra k přidružení členské proměnné k dané položce registru. Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)nebo členská funkce se stejným názvem vytvořená makrami BEGIN_RDX_MAP a END_RDX_MAP by měly být použity k provádění výměny dat mezi systémovým registrem a členskými proměnnými v mapě RDX.

## <a name="rdx_dword"></a><a name="rdx_dword"></a>RDX_DWORD

Přidruží zadanou položku registru k zadané členské proměnné typu DWORD.

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*kořenový klíč*<br/>
Kořenový klíč registru.

*Podklíč*<br/>
Podklíč registru.

*Valuename*<br/>
Klíč registru.

*Členské*<br/>
Proměnná člena, kterou chcete přidružit k zadané položce registru.

*member_size*<br/>
Velikost proměnné člena v bajtech.

### <a name="remarks"></a>Poznámky

Toto makro se používá ve spojení s BEGIN_RDX_MAP a END_RDX_MAP makra k přidružení členské proměnné k dané položce registru. Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)nebo členská funkce se stejným názvem vytvořená makrami BEGIN_RDX_MAP a END_RDX_MAP by měly být použity k provádění výměny dat mezi systémovým registrem a členskými proměnnými v mapě RDX.

## <a name="rdx_text"></a><a name="rdx_text"></a>RDX_TEXT

Přidruží zadanou položku registru k zadané členské proměnné typu TCHAR.

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*kořenový klíč*<br/>
Kořenový klíč registru.

*Podklíč*<br/>
Podklíč registru.

*Valuename*<br/>
Klíč registru.

*Členské*<br/>
Proměnná člena, kterou chcete přidružit k zadané položce registru.

*member_size*<br/>
Velikost proměnné člena v bajtech.

### <a name="remarks"></a>Poznámky

Toto makro se používá ve spojení s BEGIN_RDX_MAP a END_RDX_MAP makra k přidružení členské proměnné k dané položce registru. Globální funkce [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)nebo členská funkce se stejným názvem vytvořená makrami BEGIN_RDX_MAP a END_RDX_MAP by měly být použity k provádění výměny dat mezi systémovým registrem a členskými proměnnými v mapě RDX.

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
