---
title: Expediční mapy
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: 59dd8c7a7b0b930ffdb68fd96410fd73aeb02e81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365759"
---
# <a name="dispatch-maps"></a>Expediční mapy

Ole Automation poskytuje způsoby volání metod a přístupu k vlastnostem napříč aplikacemi. Mechanismus dodaný knihovnou tříd Microsoft Foundation pro odesílání těchto požadavků je "odeslání mapy", která označuje vnitřní a externí názvy vlastností objektu a vlastnosti, jakož i datové typy vlastností samotných a argumentů funkce.

|Makro mapy odeslání|Popis|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Deklaruje, že mapování odeslání bude použito k vystavení metod a vlastností třídy (musí být použito v deklaraci třídy).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Spustí definici mapy odeslání.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Ukončí definici mapy odeslání.|
|[DISP_FUNCTION](#disp_function)|Používá se v mapě odeslání k definování funkce automatizace OLE.|
|[DISP_PROPERTY](#disp_property)|Definuje vlastnost automatizace OLE.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Definuje vlastnost automatizace OLE a pojmenuje funkce Get a Set.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Definuje vlastnost automatizace OLE s oznámením.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Definuje vlastnost automatizace OLE, která přebírá parametry a pojmenuje funkce Get a Set.|
|[DISP_DEFVALUE](#disp_defvalue)|Vytvoří existující vlastnost jako výchozí hodnotu objektu.|

## <a name="declare_dispatch_map"></a><a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

`CCmdTarget`Pokud odvozené třídy v programu podporuje automatizaci OLE, tato třída musí poskytnout mapování odeslání vystavit své metody a vlastnosti.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Poznámky

Použijte makro DECLARE_DISPATCH_MAP na konci deklarace třídy. Potom v . CPP, který definuje členské funkce pro třídu, použijte BEGIN_DISPATCH_MAP makro. Pak zahrňte položky maker pro každou z exponovaných metod a vlastností vaší třídy (DISP_FUNCTION, DISP_PROPERTY a tak dále). Nakonec použijte makro END_DISPATCH_MAP.

> [!NOTE]
> Pokud po DECLARE_DISPATCH_MAP deklarujete všechny členy, musíte pro ně zadat nový typ přístupu **(veřejný**, **soukromý**nebo **chráněný).**

Průvodce aplikací a průvodci kódem pomáhají při vytváření tříd automatizace a při údržbě expedičních map. Další informace o mapách odeslání naleznete v [tématu Automation Servers](../../mfc/automation-servers.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="begin_dispatch_map"></a><a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

Deklaruje definici mapy odeslání.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy, která vlastní tuto mapu odeslání.

*Baseclass*<br/>
Určuje název základní třídy *class*.

### <a name="remarks"></a>Poznámky

V souboru implementace (.cpp), který definuje členské funkce pro vaši třídu, spusťte mapu odeslání pomocí BEGIN_DISPATCH_MAP makra, přidejte položky maker pro každou z expedičních funkcí a vlastností a dokončete mapu odeslání pomocí END_DISPATCH_MAP makru.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="end_dispatch_map"></a><a name="end_dispatch_map"></a>END_DISPATCH_MAP

Ukončí definici mapy odeslání.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Poznámky

Musí být používán ve spojení s BEGIN_DISPATCH_MAP.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="disp_function"></a><a name="disp_function"></a>DISP_FUNCTION

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
Název třídy.

*pszName*<br/>
Externí název funkce.

*pfnČlen*<br/>
Název členské funkce.

*vtRetVal*<br/>
Hodnota určující návratový typ funkce.

*vtsParams*<br/>
Mezerou oddělený seznam jedné nebo více konstant určujících seznam parametrů funkce.

### <a name="remarks"></a>Poznámky

Argument *vtRetVal* je typu VARTYPE. Z výčtu jsou převzaty `VARENUM` následující možné hodnoty pro tento argument:

|Symbol|Návratový typ|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE (Datum)|
|VT_BSTR|Bstr|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|Bool|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Argument *vtsParams* je mezerou oddělený seznam `VTS_*` hodnot od konstant. Jedna nebo více těchto hodnot oddělených mezerami (nikoli čárkami) určuje seznam parametrů funkce. Například:

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

určuje seznam obsahující krátké celé číslo následované ukazatelem na krátké celé číslo.

Konstanty `VTS_` a jejich významy jsou následující:

|Symbol|Typ parametru|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` nebo `CY*`|
|VTS_DATE|DATE (Datum)|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|Bool|
|VTS_VARIANT|`const VARIANT*` nebo `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__Krátké\*__|
|VTS_PI4|__Dlouhé\*__|
|VTS_PR4|__float\*__|
|VTS_PR8|__double\*__|
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

**Záhlaví:** afxdisp.h

## <a name="disp_property"></a><a name="disp_property"></a>DISP_PROPERTY

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
Název třídy.

*pszName*<br/>
Externí název vlastnosti.

*název_člena*<br/>
Název členské proměnné, ve které je vlastnost uložena.

*vtPropTyp*<br/>
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

Argument *vtPropType* je typu **VARTYPE**. Možné hodnoty pro tento argument jsou převzaty z výčtu VARENUM:

|Symbol|Typ vlastnosti|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE (Datum)|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|Bool|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Když externí klient změní vlastnost, změní se hodnota členské proměnné určené *memberName;* neexistuje žádné oznámení o změně.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="disp_property_ex"></a><a name="disp_property_ex"></a>DISP_PROPERTY_EX

Definuje vlastnost automatizace OLE a pojmenuje funkce používané k získání a nastavení hodnoty vlastnosti v mapě odeslání.

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
Název třídy.

*pszName*<br/>
Externí název vlastnosti.

*memberGet*<br/>
Název členské funkce použité k získání vlastnosti.

*Memberset*<br/>
Název členské funkce použité k nastavení vlastnosti.

*vtPropTyp*<br/>
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

Funkce *memberGet* a *memberSet* mají podpisy určené argumentem *vtPropType.* Funkce *memberGet* nepřebírá žádné argumenty a vrací hodnotu typu určeného *parametrem vtPropType*. Funkce *memberSet* přebírá argument typu určeného *vtPropType* a vrátí nic.

Argument *vtPropType* je typu VARTYPE. Možné hodnoty pro tento argument jsou převzaty z výčtu VARENUM. Seznam těchto hodnot naleznete v poznámkách pro parametr *vtRetVal* v [DISP_FUNCTION](#disp_function). Všimněte si, že VT_EMPTY, uvedené v DISP_FUNCTION poznámky, není povoleno jako datový typ vlastnosti.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="disp_property_notify"></a><a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

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
Název třídy.

*szExterní název*<br/>
Externí název vlastnosti.

*název_člena*<br/>
Název členské proměnné, ve které je vlastnost uložena.

*pfnAfterSet*<br/>
Název funkce oznámení pro *szExternalName*.

*vtPropTyp*<br/>
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

Na rozdíl od vlastností definovaných s DISP_PROPERTY, vlastnost definovaná DISP_PROPERTY_NOTIFY bude automaticky volat funkci určenou *pfnAfterSet* při změně vlastnosti.

Argument *vtPropType* je typu VARTYPE. Možné hodnoty pro tento argument jsou převzaty z výčtu VARENUM:

|Symbol|Typ vlastnosti|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE (Datum)|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|Bool|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="disp_property_param"></a><a name="disp_property_param"></a>DISP_PROPERTY_PARAM

Definuje vlastnost přistupovat s `Get` `Set` samostatné a členské funkce.

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
Název třídy.

*pszExternínázev*<br/>
Externí název vlastnosti.

*pfnGet*<br/>
Název členské funkce použité k získání vlastnosti.

*pfnSet*<br/>
Název členské funkce použité k nastavení vlastnosti.

*vtPropTyp*<br/>
Hodnota určující typ vlastnosti.

*vtsParams*<br/>
Řetězec prostorově oddělených `VTS_*` typů parametrů variant, jeden pro každý parametr.

### <a name="remarks"></a>Poznámky

Na rozdíl od DISP_PROPERTY_EX makra umožňuje toto makro zadat seznam parametrů pro vlastnost. To je užitečné pro implementaci vlastností, které jsou indexovány nebo parametrizovány.

### <a name="example"></a>Příklad

Zvažte následující deklaraci get a set členské funkce, které umožňují uživateli požádat o konkrétní řádek a sloupec při přístupu k vlastnosti:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Tyto odpovídají následující DISP_PROPERTY_PARAM makro v mapě dispečinku ovládacího prvku:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Jako další příklad zvažte následující get a set členské funkce:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Tyto odpovídají následující DISP_PROPERTY_PARAM makro v mapě dispečinku ovládacího prvku:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="disp_defvalue"></a><a name="disp_defvalue"></a>DISP_DEFVALUE

Vytvoří existující vlastnost jako výchozí hodnotu objektu.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy.

*pszName*<br/>
Externí název vlastnosti, která představuje "hodnotu" objektu.

### <a name="remarks"></a>Poznámky

Použití výchozí hodnoty může usnadnit programování objektu automatizace pro aplikace jazyka Visual Basic.

"Výchozí hodnota" objektu je vlastnost, která je načtena nebo nastavena, když odkaz na objekt neurčuje vlastnost nebo člennou funkci.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
