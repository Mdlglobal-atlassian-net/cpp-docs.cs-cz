---
title: Expediční mapy
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: a1baa5274dbd33bb1e88b57ccfab2b5ed2085f6d
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611304"
---
# <a name="dispatch-maps"></a>Expediční mapy

Automatizace OLE způsoby volání metod a získat přístup k vlastnostem napříč aplikacemi. Mechanismus poskytnutých knihovny Microsoft Foundation Class pro odesílání tyto žádosti je "Mapa odeslání,", která označuje interní a externí názvy objektů funkce a vlastnosti, jakož i datové typy vlastností sami nebo argumenty funkce.

|Makra mapy odeslání|Popis|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Deklaruje, že mapa odeslání se použije k vystavení metody třídy a vlastnosti (musí se použít v deklaraci třídy).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Spustí definice mapa odeslání.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Ukončí definici mapa odeslání.|
|[DISP_FUNCTION](#disp_function)|Použít v objektu map odeslání definice funkce automatizace OLE.|
|[DISP_PROPERTY](#disp_property)|Definuje vlastnost automatizace OLE.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Definuje vlastnost automatizace OLE a názvy funkce Get a Set.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Definuje vlastnost automatizace OLE s oznámením.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Definuje vlastnosti automatizace OLE, který přebírá názvy a parametry funkce Get a Set.|
|[DISP_DEFVALUE](#disp_defvalue)|Díky existující vlastnost výchozí hodnotu objektu.|

## <a name="declare_dispatch_map"></a>  DECLARE_DISPATCH_MAP

Pokud `CCmdTarget`-odvozené třídy ve svém programu podporuje automatizace OLE, že třída musí poskytovat mapa odeslání ke zveřejnění jejím metodám a vlastnostem.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Poznámky

Použití DECLARE_DISPATCH_MAP – makro na konec deklarace třídy. Potom v. Soubor CPP, který definuje členské funkce třídy, použijte BEGIN_DISPATCH_MAP – makro. Potom zahrnovat – makro položky pro každou z metod vystavených vaší třídy a vlastnosti (DISP_FUNCTION DISP_PROPERTY a tak dále). Nakonec použijte END_DISPATCH_MAP – makro.

> [!NOTE]
> Pokud deklarujete po DECLARE_DISPATCH_MAP žádné členy, je nutné zadat nový typ přístupu ( **veřejné**, **privátní**, nebo **chráněné**) pro ně.

Průvodci Průvodce aplikací a kódu pomáhají při vytváření třídy automatizace a zachování expediční mapy. Další informace o expediční mapy, naleznete v tématu [automatizační servery](../../mfc/automation-servers.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="begin_dispatch_map"></a>  BEGIN_DISPATCH_MAP

Deklaruje definici mapy odeslání.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy, která je vlastníkem této mapy odeslání.

*baseClass*<br/>
Určuje název základní třídy *theClass*.

### <a name="remarks"></a>Poznámky

V souboru implementace (.cpp), který definuje členské funkce třídy mapa odeslání začínat BEGIN_DISPATCH_MAP – makro, přidat makro položky pro každý z odeslání funkce a vlastnosti a dokončete odeslání mapování END_DISPATCH_ Makra MAPY.

### <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

## <a name="end_dispatch_map"></a>  END_DISPATCH_MAP

Ukončí definici mapy odeslání.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Poznámky

Je možné použít ve spojení s BEGIN_DISPATCH_MAP.

### <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

## <a name="disp_function"></a>  DISP_FUNCTION

Definuje funkci automatizace OLE v mapa odeslání.

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

*pfnMember*<br/>
Název členské funkce.

*vtRetVal*<br/>
Hodnota určující návratový typ funkce.

*vtsParams*<br/>
Místo oddělený seznam jednoho nebo více konstant určující seznam parametrů funkce.

### <a name="remarks"></a>Poznámky

*VtRetVal* argument je typu VARTYPE. Následující možné hodnoty pro tento argument pocházejí ze `VARENUM` výčtu:

|Symbol|Návratový typ|
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
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

*VtsParams* argument je místo oddělený seznam hodnot z `VTS_*` konstanty. Jeden nebo více z těchto hodnot oddělených mezerami (ne čárky) určuje seznam parametrů funkce. Například

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

Určuje seznam obsahující krátké celé číslo, za nímž následuje ukazatel na krátké celé číslo.

`VTS_` Konstanty a jejich význam, jsou následující:

|Symbol|Typ parametru|
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
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` Nebo `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__short\*__|
|VTS_PI4|__Long\*__|
|VTS_PR4|__plovoucí desetinnou čárkou\*__|
|VTS_PR8|__Double\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|Žádné parametry.|

### <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

## <a name="disp_property"></a>  DISP_PROPERTY

Definuje vlastnost automatizace OLE v mapa odeslání.

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

*memberName*<br/>
Název členské proměnné, ve kterém je uložené vlastnosti.

*vtPropType*<br/>
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

*VtPropType* argument je typu **VARTYPE**. Možné hodnoty pro tento argument pocházejí ze výčet VARENUM:

|Symbol|Typ vlastnosti|
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
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Při změně vlastností, je hodnota členské proměnné určené externího klienta *memberName* změní; neexistuje žádná upozornění na změnu.

### <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

## <a name="disp_property_ex"></a>  DISP_PROPERTY_EX

Definuje vlastnosti automatizace OLE a služby název funkce, které slouží k získání a nastavení hodnoty vlastnosti v objektu map odeslání.

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
Název členské funkce použít k získání vlastnosti.

*memberSet*<br/>
Název členské funkce lze nastavit vlastnost.

*vtPropType*<br/>
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

*MemberGet* a *členů* funkce mají podpisy, které jsou určeny *vtPropType* argument. *MemberGet* funkce nepřijímá žádné argumenty a vrátí hodnotu typu určeného *vtPropType*. *Členů* funkce přijímá argument tohoto typu určeného *vtPropType* a nic nespouští.

*VtPropType* argument je typu VARTYPE. Možné hodnoty pro tento argument pocházejí ze výčet VARENUM. Seznam těchto hodnot najdete v tématu poznámky pro *vtRetVal* parametr [DISP_FUNCTION](#disp_function). Všimněte si, že VT_EMPTY uvedených v poznámkách DISP_FUNCTION není povolená jako datový typ vlastnosti.

### <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

## <a name="disp_property_notify"></a>  DISP_PROPERTY_NOTIFY

Definuje vlastnost automatizace OLE s oznámením v mapa odeslání.

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

*szExternalName*<br/>
Externí název vlastnosti.

*memberName*<br/>
Název členské proměnné, ve kterém je uložené vlastnosti.

*pfnAfterSet*<br/>
Název funkce oznámení pro *szExternalName*.

*vtPropType*<br/>
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

Na rozdíl od vlastnosti definované s DISP_PROPERTY vlastnosti definované pomocí DISP_PROPERTY_NOTIFY automaticky zavolá funkci zadanou na základě *pfnAfterSet* když je změněna vlastnost.

*VtPropType* argument je typu VARTYPE. Možné hodnoty pro tento argument pocházejí ze výčet VARENUM:

|Symbol|Typ vlastnosti|
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
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

## <a name="disp_property_param"></a>  DISP_PROPERTY_PARAM

Definuje vlastnost k němu přistupovat pomocí samostatného `Get` a `Set` členské funkce.

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

*pszExternalName*<br/>
Externí název vlastnosti.

*pfnGet*<br/>
Název členské funkce použít k získání vlastnosti.

*pfnSet*<br/>
Název členské funkce lze nastavit vlastnost.

*vtPropType*<br/>
Hodnota určující typ vlastnosti.

*vtsParams*<br/>
Řetězec oddělených mezerami `VTS_*` typy parametr typu variant, jeden pro každý parametr.

### <a name="remarks"></a>Poznámky

Na rozdíl od DISP_PROPERTY_EX – makro toto makro umožňuje určit seznam parametrů pro vlastnost. To je užitečné pro implementaci vlastnosti, které jsou indexována nebo s parametry.

### <a name="example"></a>Příklad

Zvažte následující deklaraci get a nastavte členské funkce, které uživateli umožňují požadovat konkrétní řádek a sloupec při přístupu k vlastnosti:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Tyto weby odpovídají na následující DISP_PROPERTY_PARAM – makro v mapování ovládacího prvku odeslání:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Další příklad zvažte následující get a nastavte členské funkce:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Tyto weby odpovídají na následující DISP_PROPERTY_PARAM – makro v mapování ovládacího prvku odeslání:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

## <a name="disp_defvalue"></a>  DISP_DEFVALUE

Díky existující vlastnost výchozí hodnotu objektu.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy.

*pszName*<br/>
Externí název vlastnosti, která představuje "value" objekt.

### <a name="remarks"></a>Poznámky

Programování objektu automatizace jednodušší pro aplikace Visual Basic můžete nastavit s výchozí hodnotou.

"Výchozí hodnota" objektu je vlastnost, která je načíst nebo nastavit, pokud odkaz na objekt neurčuje vlastnost nebo členským funkcím.

### <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
