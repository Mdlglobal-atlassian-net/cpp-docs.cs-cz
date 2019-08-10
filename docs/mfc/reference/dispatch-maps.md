---
title: Expediční mapy
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: f1afa95d7c20d54f2015255a7e4e0d7ad9ae9c2b
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916513"
---
# <a name="dispatch-maps"></a>Expediční mapy

Automatizace OLE poskytuje způsob volání metod a přístup k vlastnostem napříč aplikacemi. Mechanismus dodaný knihovna Microsoft Foundation Class pro odesílání těchto požadavků je "mapa odeslání", která určuje interní a externí názvy funkcí a vlastností objektů a také datové typy samotných vlastností a argumenty funkce.

|Makro mapy odeslání|Popis|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Deklaruje, že mapa odeslání bude použita k vystavení metod a vlastností třídy (musí být použity v deklaraci třídy).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Spustí definici mapy odeslání.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Ukončí definici mapy odeslání.|
|[DISP_FUNCTION](#disp_function)|Používá se v mapě odeslání k definování funkce automatizace OLE.|
|[DISP_PROPERTY](#disp_property)|Definuje vlastnost automatizace OLE.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Definuje vlastnost automatizace OLE a názvy funkcí get a set.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Definuje vlastnost automatizace OLE s oznámením.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Definuje vlastnost automatizace OLE, která přebírá parametry a názvů funkcí get a set.|
|[DISP_DEFVALUE](#disp_defvalue)|Vytvoří existující vlastnost jako výchozí hodnotu objektu.|

## <a name="declare_dispatch_map"></a>  DECLARE_DISPATCH_MAP

`CCmdTarget`Pokud třída odvozená v programu podporuje automatizaci OLE, musí tato třída poskytnout mapu odeslání k vystavení metod a vlastností.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Poznámky

Použijte makro DECLARE_DISPATCH_MAP na konci deklarace třídy. Potom v. Soubor CPP, který definuje členské funkce pro třídu, použijte makro BEGIN_DISPATCH_MAP. Pak zahrňte položky makra pro všechny metody a vlastnosti vystavené vaší třídě (DISP_FUNCTION, DISP_PROPERTY a tak dále). Nakonec použijte makro END_DISPATCH_MAP.

> [!NOTE]
> Pokud deklarujete členy po DECLARE_DISPATCH_MAP, musíte pro ně zadat nový typ přístupu ( **Public**, **Private**nebo Protected).

Průvodce aplikací a průvodci kódem pomáhají při vytváření tříd automatizace a při údržbě map odesílání. Další informace o mapách odesílání najdete v tématu [automatizační servery](../../mfc/automation-servers.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

## <a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

Deklaruje definici mapy odeslání.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy, která vlastní tuto mapu odeslání.

*baseClass*<br/>
Určuje název základní třídy *theclass*.

### <a name="remarks"></a>Poznámky

V souboru implementace (. cpp), který definuje členské funkce pro vaši třídu, spusťte mapu odeslání pomocí makra BEGIN_DISPATCH_MAP, přidejte položky makra pro každou ze svých funkcí a vlastností odeslání a dokončete mapu odeslání pomocí END_DISPATCH_ MAPOVÁNÍ makra

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

## <a name="end_dispatch_map"></a>  END_DISPATCH_MAP

Ukončí definici mapy odeslání.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Poznámky

Musí se používat ve spojení s BEGIN_DISPATCH_MAP.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

## <a name="disp_function"></a>DISP_FUNCTION

Definuje funkci automatizace OLE v mapě odeslání.

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy

*pszName*<br/>
Externí název funkce

*pfnMember*<br/>
Název členské funkce

*vtRetVal*<br/>
Hodnota určující návratový typ funkce.

*vtsParams*<br/>
Mezerou oddělený seznam jedné nebo více konstant určujících seznam parametrů funkce.

### <a name="remarks"></a>Poznámky

Argument *vtRetVal* je typu VARTYPE. Následující možné hodnoty pro tento argument jsou pořízeny z `VARENUM` výčtu:

|Písmeno|Návratový typ|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|LOGICK|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Argument *vtsParams* je seznam hodnot oddělených mezerami z `VTS_*` konstant. Jedna nebo více z těchto hodnot oddělených mezerami (nejedná se o čárky) určuje seznam parametrů funkce. Například

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

Určuje seznam obsahující krátké celé číslo následované ukazatelem na krátké celé číslo.

`VTS_` Konstanty a jejich významy jsou následující:

|Písmeno|Typ parametru|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` Nebo `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|LOGICK|
|VTS_VARIANT|`const VARIANT*` Nebo `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__dostatečná\*__|
|VTS_PI4|__dlouhou\*__|
|VTS_PR4|__Plovák\*__|
|VTS_PR8|__klepat\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|Žádné parametry|

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

## <a name="disp_property"></a>DISP_PROPERTY

Definuje vlastnost automatizace OLE v mapě odeslání.

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy

*pszName*<br/>
Externí název vlastnosti

*memberName*<br/>
Název členské proměnné, ve které je vlastnost uložená.

*vtPropType*<br/>
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

Argument *vtPropType* je typu **VARTYPE**. Možné hodnoty pro tento argument jsou pořízeny z výčtu VARENUM:

|Písmeno|Typ vlastnosti|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|LOGICK|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Změní-li se v externím klientovi vlastnost, změní se hodnota členské proměnné určené vlastností *Member* ; Tato změna není nijak oznámena.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

## <a name="disp_property_ex"></a>DISP_PROPERTY_EX

Definuje vlastnost a název automatizace OLE, které funkce slouží k získání a nastavení hodnoty vlastnosti v mapě odeslání.

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy

*pszName*<br/>
Externí název vlastnosti

*memberGet*<br/>
Název členské funkce, která se používá k získání vlastnosti

*memberSet*<br/>
Název členské funkce použité k nastavení vlastnosti.

*vtPropType*<br/>
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

Funkce *memberGet* a *memberSet* mají signatury určené argumentem *vtPropType* . Funkce *memberGet* nepřebírá žádné argumenty a vrací hodnotu typu určenou parametrem *vtPropType*. Funkce *memberSet* přebírá argument typu určený parametrem *vtPropType* a nevrací hodnotu Nothing.

Argument *vtPropType* je typu VARTYPE. Možné hodnoty pro tento argument jsou pořízeny z výčtu VARENUM. Seznam těchto hodnot naleznete v tématu poznámky k parametru *vtRetVal* v [DISP_FUNCTION](#disp_function). Všimněte si, že VT_EMPTY, který je uvedený v DISP_FUNCTION – poznámky, není povolen jako datový typ vlastnosti.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

## <a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

Definuje vlastnost automatizace OLE s oznámením v mapě odeslání.

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy

*szExternalName*<br/>
Externí název vlastnosti

*memberName*<br/>
Název členské proměnné, ve které je vlastnost uložená.

*pfnAfterSet*<br/>
Název funkce oznámení pro *szExternalName*.

*vtPropType*<br/>
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

Na rozdíl od vlastností definovaných pomocí DISP_PROPERTY bude vlastnost definovaná s DISP_PROPERTY_NOTIFY automaticky volat funkci určenou funkcí *pfnAfterSet* při změně vlastnosti.

Argument *vtPropType* je typu VARTYPE. Možné hodnoty pro tento argument jsou pořízeny z výčtu VARENUM:

|Písmeno|Typ vlastnosti|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|LOGICK|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

## <a name="disp_property_param"></a>DISP_PROPERTY_PARAM

Definuje vlastnost přistupovaná pomocí `Get` samostatných `Set` a členských funkcí.

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszExternalName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy

*pszExternalName*<br/>
Externí název vlastnosti

*pfnGet*<br/>
Název členské funkce, která se používá k získání vlastnosti

*pfnSet*<br/>
Název členské funkce použité k nastavení vlastnosti.

*vtPropType*<br/>
Hodnota určující typ vlastnosti.

*vtsParams*<br/>
Řetězec typů parametrů variant oddělených `VTS_*` mezerami, jeden pro každý parametr.

### <a name="remarks"></a>Poznámky

Na rozdíl od makra DISP_PROPERTY_EX vám toto makro umožní určit seznam parametrů pro vlastnost. To je užitečné pro implementaci vlastností, které jsou indexované nebo parametrizované.

### <a name="example"></a>Příklad

Zvažte následující deklaraci funkcí get a set pro členské funkce, které uživateli umožňují požádat o konkrétní řádek a sloupec při přístupu k vlastnosti:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Odpovídají následujícímu DISP_PROPERTY_PARAM makru v mapě odesílání ovládacího prvku:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Jako jiný příklad zvažte následující funkce Get a set pro členské funkce:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Odpovídají následujícímu DISP_PROPERTY_PARAM makru v mapě odesílání ovládacího prvku:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

## <a name="disp_defvalue"></a>  DISP_DEFVALUE

Vytvoří existující vlastnost jako výchozí hodnotu objektu.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy

*pszName*<br/>
Externí název vlastnosti, která představuje hodnotu objektu.

### <a name="remarks"></a>Poznámky

Použití výchozí hodnoty může zjednodušit programování automatizačních objektů pro Visual Basic aplikace.

Výchozí hodnota objektu je vlastnost, která je načtena nebo nastavena, když odkaz na objekt neurčuje vlastnost nebo členskou funkci.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
