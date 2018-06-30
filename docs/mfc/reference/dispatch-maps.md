---
title: Mapy odesílání | Microsoft Docs
ms.custom: ''
ms.date: 06/20/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 107dba503c11d3810f75dcd4ee6e6f5af47008fc
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122977"
---
# <a name="dispatch-maps"></a>Expediční mapy

OLE – automatizace poskytuje způsobů, jak volat metody a pro přístup k vlastnostem napříč aplikacemi. Tento mechanismus poskytl knihovny Microsoft Foundation Class pro odeslání tyto požadavky je "mapy odesílání," což znamená, že názvy interních a externích objekt funkce a vlastnosti, jakož i datové typy vlastností sami nebo argumenty funkce.

|Makra mapy odeslání|Popis|
|-|-|
|[DECLARE_DISPATCH_MAP –](#declare_dispatch_map)|Deklaruje, že mapy odesílání bude použit ke zveřejnění třídy a metody a vlastnosti (musí používat v deklaraci třídy).|
|[BEGIN_DISPATCH_MAP –](#begin_dispatch_map)|Spustí definici expediční mapy.|
|[END_DISPATCH_MAP –](#end_dispatch_map)|Ukončí definici expediční mapy.|
|[DISP_FUNCTION –](#disp_function)|Používá se v mapě odesílání k definování funkce automatizace OLE.|
|[DISP_PROPERTY –](#disp_property)|Definuje vlastnost automatizace OLE.|
|[DISP_PROPERTY_EX –](#disp_property_ex)|Definuje vlastnost automatizace OLE a názvy funkce Get a Set.|
|[DISP_PROPERTY_NOTIFY –](#disp_property_notify)|Definuje vlastnost automatizace OLE s oznámení.|
|[DISP_PROPERTY_PARAM –](#disp_property_param)|Definuje vlastnosti automatizace OLE, která přebírá názvy a parametry funkce Get a Set.|
|[DISP_DEFVALUE –](#disp_defvalue)|Díky existující vlastnost Výchozí hodnota objektu.|

## <a name="declare_dispatch_map"></a>  DECLARE_DISPATCH_MAP –

Pokud `CCmdTarget`-odvozené třídy v programu podporuje automatizace OLE, že třída musí poskytnout mapy odesílání vystavit její metody a vlastnosti.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Poznámky

Použijte declare_dispatch_map – makro na konci deklarace třídy. Pak na. CPP soubor, který definuje členské funkce pro třídu, použijte begin_dispatch_map – makro. Potom zahrňte makro položky pro každý vlastní třídy zveřejněné metod a vlastností (disp_function – disp_property – a tak dále). Nakonec použijte end_dispatch_map – makro.

> [!NOTE]
> Pokud je po declare_dispatch_map – deklarovat žádné členy, je nutné zadat nový typ přístupu ( **veřejné**, **privátní**, nebo **chráněné**) pro ně.

Průvodce vytvořením aplikace a kód průvodců pomáhat při vytváření třídy automatizace a zachování expediční mapy. Další informace o expediční mapy, najdete v části [automatizační servery](../../mfc/automation-servers.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="begin_dispatch_map"></a>  BEGIN_DISPATCH_MAP –

Deklaruje definici expediční mapy.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*  
Určuje název třídy, který vlastní toto odesílání mapování.

*baseclass –*  
Určuje název základní třídy *theClass*.

### <a name="remarks"></a>Poznámky

V souboru implementace (sada), který definuje členské funkce pro třídu začínat begin_dispatch_map – makro mapy odesílání, přidejte makro položky pro každý odesílání funkcí a vlastností a dokončení odesílání mapa s END_DISPATCH_ Makra MAPY.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="end_dispatch_map"></a>  END_DISPATCH_MAP –

Ukončí definici expediční mapy.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Poznámky

Musíte ho použít ve spojení s begin_dispatch_map –.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="disp_function"></a>  DISP_FUNCTION –

Definuje funkci automatizace OLE v mapě odesílání.

```cpp
DISP_FUNCTION(
  theClass,
  pszName,
  pfnMember,
  vtRetVal,
  vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*  
Název třídy.

*pszName*  
Externí název funkce.

*pfnMember*  
Název členské funkce.

*vtRetVal*  
Hodnota, zadat návratový typ funkce.

*vtsParams*  
Seznam jedné nebo více konstant určující seznam parametrů pro funkci oddělených mezerami.

### <a name="remarks"></a>Poznámky

*VtRetVal* argument je typu VARTYPE. Z následujících možných hodnot pro tento argument, která `VARENUM` výčtu:

|Symbol|Návratový typ|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE –|DATUM|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|HODNOTA VT_UNKNOWN|LPUNKNOWN|

*VtsParams* argument je seznam hodnot oddělených mezerami `VTS_*` konstanty. Jeden nebo více z těchto hodnot oddělených mezerami (ne čárkami) určuje seznam parametrů funkce. Například

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

Určuje seznam obsahující krátké celé číslo následuje ukazatel na krátké celé číslo.

`VTS_` Konstanty a jejich významy jsou následující:

|Symbol|Typ parametru|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` nebo `CY*`|
|VTS_DATE|DATUM|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` nebo `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__krátký\*__|
|VTS_PI4|__dlouhá\*__|
|VTS_PR4|__plovoucí desetinná čárka\*__|
|VTS_PR8|__Double\*__|
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

## <a name="disp_property"></a>  DISP_PROPERTY –

Definuje vlastnost automatizace OLE v mapě odesílání.

```cpp
DISP_PROPERTY(
  theClass,
  pszName,
  memberName,
  vtPropType)
```

### <a name="parameters"></a>Parametry

*theClass*  
Název třídy.

*pszName*  
Externí název vlastnosti.

*Členské jméno*  
Název členské proměnné, ve kterém je uložený vlastnost.

*vtPropType*  
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

*VtPropType* argument je typu **VARTYPE**. Možné hodnoty pro tento argument jsou převzaty z výčtu VARENUM:

|Symbol|Typ vlastnosti|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE –|DATUM|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|HODNOTA VT_UNKNOWN|LPUNKNOWN|

Až se změní hodnota členské proměnné určeného vlastnosti externích klientských *memberName* změní; nejsou žádná oznámení změny.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="disp_property_ex"></a>  DISP_PROPERTY_EX –

Definuje vlastnosti automatizace OLE a název funkce, které slouží k získání a nastavení vlastnosti na hodnotu v mapě odesílání.

```cpp
DISP_PROPERTY_EX(
  theClass,
  pszName,
  memberGet,
  memberSet,
  vtPropType)
```

### <a name="parameters"></a>Parametry

*theClass*  
Název třídy.

*pszName*  
Externí název vlastnosti.

*memberGet*  
Název členské funkce používá GET pro vlastnost.

*Sada členů*  
Název členské funkce lze nastavit vlastnost.

*vtPropType*  
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

*MemberGet* a *sada členů* funkce mají podpisy dáno *vtPropType* argument. *MemberGet* funkce nezadávaly žádné argumenty a vrátí hodnotu typu zadaném pomocí *vtPropType*. *Sada členů* funkce přebírá argument v typu zadaném pomocí *vtPropType* a nic.

*VtPropType* argument je typu VARTYPE. Možné hodnoty pro tento argument jsou převzaty z výčtu VARENUM. Seznam těchto hodnot, najdete v části poznámky pro *vtRetVal* parametr v [disp_function –](#disp_function). Všimněte si, že VT_EMPTY, uvedené v disp_function – poznámky, není povolen jako datový typ vlastnosti.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="disp_property_notify"></a>  DISP_PROPERTY_NOTIFY –

Definuje vlastnost automatizace OLE s oznámení v mapě odesílání.

```cpp
DISP_PROPERTY_NOTIFY(
  theClass,
  szExternalName,
  memberName,
  pfnAfterSet,
  vtPropType)
```

### <a name="parameters"></a>Parametry

*theClass*  
Název třídy.

*szExternalName*  
Externí název vlastnosti.

*Členské jméno*  
Název členské proměnné, ve kterém je uložený vlastnost.

*pfnAfterSet*  
Název funkce oznámení pro *szExternalName*.

*vtPropType*  
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

Na rozdíl od vlastnosti definované s disp_property –, bude vlastnost definovanou s disp_property_notify – automaticky volání funkce určeného *pfnAfterSet* při změně vlastnosti.

*VtPropType* argument je typu VARTYPE. Možné hodnoty pro tento argument jsou převzaty z výčtu VARENUM:

|Symbol|Typ vlastnosti|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE –|DATUM|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|HODNOTA VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="disp_property_param"></a>  DISP_PROPERTY_PARAM –

Definuje vlastnost přístupný pomocí samostatné `Get` a `Set` členské funkce.

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

*theClass*  
Název třídy.

*pszExternalName*  
Externí název vlastnosti.

*pfnGet*  
Název členské funkce používá GET pro vlastnost.

*pfnSet*  
Název členské funkce lze nastavit vlastnost.

*vtPropType*  
Hodnota určující typ vlastnosti.

*vtsParams*  
Řetězec oddělených mezerami `VTS_*` typy variant parametr, jednu pro každý parametr.

### <a name="remarks"></a>Poznámky

Na rozdíl od disp_property_ex – makro toto makro umožňuje určit seznam parametrů pro vlastnost. To je užitečné pro implementaci vlastnosti, které jsou indexované nebo parametry.

### <a name="example"></a>Příklad

Vezměte v úvahu následující deklaraci get a nastavte členské funkce, které umožňují uživateli požadovat konkrétní řádků a sloupců při přístupu k vlastnosti:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Tyto hodnoty odpovídají následující disp_property_param – makro v odesílání mapy ovládacího prvku:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Další příklad zvažte následující get a nastavte členské funkce:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Tyto hodnoty odpovídají následující disp_property_param – makro v odesílání mapy ovládacího prvku:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="disp_defvalue"></a>  DISP_DEFVALUE –

Díky existující vlastnost Výchozí hodnota objektu.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parametry

*theClass*  
Název třídy.

*pszName*  
Externí název vlastnosti, která představuje "hodnota" objektu.

### <a name="remarks"></a>Poznámky

Pomocí výchozí hodnotu můžete nastavit programování objektu automatizace jednodušší pro aplikace Visual Basic.

"Výchozí hodnota" objektu je vlastnost, která je načíst nebo nastavit odkaz na objekt neurčuje vlastnost nebo člen funkce.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)  
