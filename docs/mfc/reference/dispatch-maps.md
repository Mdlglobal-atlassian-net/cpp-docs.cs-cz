---
title: "Mapy odesílání | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros.maps
dev_langs: C++
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3112c092a4e1d6eb970fb50153c543baa98ee853
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dispatch-maps"></a>Expediční mapy
OLE – automatizace poskytuje způsobů, jak volat metody a pro přístup k vlastnostem napříč aplikacemi. Tento mechanismus poskytl knihovny Microsoft Foundation Class pro odeslání tyto požadavky je "mapy odesílání," což znamená, že názvy interních a externích objekt funkce a vlastnosti, jakož i datové typy vlastností sami nebo argumenty funkce.  
  
### <a name="dispatch-maps"></a>Expediční mapy  
  
|||  
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
  
##  <a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP –  
 Pokud `CCmdTarget`-odvozené třídy v programu podporuje automatizace OLE, že třída musí poskytnout mapy odesílání vystavit její metody a vlastnosti.  
  
```   
DECLARE_DISPATCH_MAP()  
```  
  
### <a name="remarks"></a>Poznámky  
 Použití `DECLARE_DISPATCH_MAP` makro na konci deklarace třídy. Pak na. Funkce CPP souboru, který definuje člena pro třídu, použijte `BEGIN_DISPATCH_MAP` makro. Potom zahrnovat makro položky pro každý z vaší třídy je vystavený metody a vlastnosti ( `DISP_FUNCTION`, `DISP_PROPERTY`a tak dále). Nakonec použijte `END_DISPATCH_MAP` makro.  
  
> [!NOTE]
>  Pokud je deklarovat žádné členy po `DECLARE_DISPATCH_MAP`, je nutné zadat nový typ přístupu ( **veřejné**, `private`, nebo `protected`) pro ně.  
  
 Průvodce vytvořením aplikace a kód průvodců pomáhat při vytváření třídy automatizace a zachování expediční mapy. Další informace o expediční mapy, najdete v části [automatizační servery](../../mfc/automation-servers.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  

##  <a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP –  
 Deklaruje definici expediční mapy.  
  
```  
BEGIN_DISPATCH_MAP(theClass, baseClass)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Určuje název třídy, který vlastní toto odesílání mapování.  
  
 `baseClass`  
 Určuje název základní třídy `theClass`.  
  
### <a name="remarks"></a>Poznámky  
 V souboru implementace (sada), který definuje členské funkce pro třídu, spusťte mapa odesílání s `BEGIN_DISPATCH_MAP` makro, přidejte makro položky pro každý odesílání funkcí a vlastností a dokončení odesílání mapa s `END_DISPATCH_MAP` makro.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  

##  <a name="end_dispatch_map"></a>END_DISPATCH_MAP –  
 Ukončí definici expediční mapy.  
  
```   
END_DISPATCH_MAP()  
```  
  
### <a name="remarks"></a>Poznámky  
 Musíte ho použít ve spojení s `BEGIN_DISPATCH_MAP`.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  

##  <a name="disp_function"></a>DISP_FUNCTION –  
 Definuje funkci automatizace OLE v mapě odesílání.  
  
```   
DISP_FUNCTION(
  theClass, 
  pszName, 
  pfnMember, 
  vtRetVal, 
  vtsParams)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Název třídy.  
  
 `pszName`  
 Externí název funkce.  
  
 `pfnMember`  
 Název členské funkce.  
  
 `vtRetVal`  
 Hodnota, zadat návratový typ funkce.  
  
 `vtsParams`  
 Seznam jedné nebo více konstant určující seznam parametrů pro funkci oddělených mezerami.  
  
### <a name="remarks"></a>Poznámky  
 `vtRetVal` Argument je typu **VARTYPE**. Z následujících možných hodnot pro tento argument, která `VARENUM` výčtu:  
  
|Symbol|Návratový typ|  
|------------|-----------------|  
|`VT_EMPTY`|`void`|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**DATUM**|  
|`VT_BSTR`|`BSTR`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT**|  
|**HODNOTA VT_UNKNOWN**|`LPUNKNOWN`|  
  
 `vtsParams` Argument je seznam hodnot oddělených mezerami **VTS_** konstanty. Jeden nebo více z těchto hodnot oddělených mezerami (ne čárkami) určuje seznam parametrů funkce. Například 
  
 [!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]  
  
 Určuje seznam obsahující krátké celé číslo následuje ukazatel na krátké celé číslo.  
  
 **VTS_** konstanty a jejich významy jsou následující:  
  
|Symbol|Typ parametru|  
|------------|--------------------|  
|**VTS_I2**|`Short`|  
|**VTS_I4**|`Long`|  
|**VTS_R4**|**Plovoucí desetinná čárka**|  
|**VTS_R8**|`Double`|  
|**VTS_CY**|**Const CY** nebo **CY\***|  
|**VTS_DATE**|**DATUM**|  
|**VTS_BSTR**|`LPCSTR`|  
|**VTS_DISPATCH**|`LPDISPATCH`|  
|**VTS_SCODE**|`SCODE`|  
|**VTS_BOOL**|**BOOL**|  
|**VTS_VARIANT**|**Const VARIANT\***  nebo **VARIANT &**|  
|**VTS_UNKNOWN**|`LPUNKNOWN`|  
|**VTS_PI2**|**krátký\***|  
|**VTS_PI4**|**dlouhá\***|  
|**VTS_PR4**|**plovoucí desetinná čárka\***|  
|**VTS_PR8**|**Double\***|  
|**VTS_PCY**|**CY\***|  
|**VTS_PDATE**|**DATUM\***|  
|**VTS_PBSTR**|**BSTR\***|  
|**VTS_PDISPATCH**|**LPDISPATCH\***|  
|**VTS_PSCODE**|**KÓD SCODE\***|  
|**VTS_PBOOL**|**BOOL\***|  
|**VTS_PVARIANT**|**VARIANT\***|  
|**VTS_PUNKNOWN**|**LPUNKNOWN\***|  
|**VTS_NONE**|Žádné parametry|  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h 

##  <a name="disp_property"></a>DISP_PROPERTY –  
 Definuje vlastnost automatizace OLE v mapě odesílání.  
  
```   
DISP_PROPERTY(
  theClass, 
  pszName, 
  memberName, 
  vtPropType)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Název třídy.  
  
 `pszName`  
 Externí název vlastnosti.  
  
 `memberName`  
 Název členské proměnné, ve kterém je uložený vlastnost.  
  
 `vtPropType`  
 Hodnota určující typ vlastnosti.  
  
### <a name="remarks"></a>Poznámky  
 `vtPropType` Argument je typu **VARTYPE**. Z možných hodnot pro tento argument, která `VARENUM` výčtu:  
  
|Symbol|**Typ vlastnosti**|  
|------------|-----------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**DATUM**|  
|`VT_BSTR`|`CString`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT**|  
|**HODNOTA VT_UNKNOWN**|`LPUNKNOWN`|  
  
 Až se změní hodnota členské proměnné určeného vlastnosti externích klientských `memberName` změní; nejsou žádná oznámení změny.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h 

##  <a name="disp_property_ex"></a>DISP_PROPERTY_EX –  
 Definuje vlastnosti automatizace OLE a název funkce, které slouží k získání a nastavení vlastnosti na hodnotu v mapě odesílání.  
  
```   
DISP_PROPERTY_EX(
  theClass, 
  pszName, 
  memberGet, 
  memberSet, 
  vtPropType)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Název třídy.  
  
 `pszName`  
 Externí název vlastnosti.  
  
 `memberGet`  
 Název členské funkce používá GET pro vlastnost.  
  
 `memberSet`  
 Název členské funkce lze nastavit vlastnost.  
  
 `vtPropType`  
 Hodnota určující typ vlastnosti.  
  
### <a name="remarks"></a>Poznámky  
 `memberGet` a `memberSet` funkce mají podpisy dáno `vtPropType` argument. `memberGet` Funkce nezadávaly žádné argumenty a vrátí hodnotu typu zadaném pomocí `vtPropType`. `memberSet` Funkce přebírá argument v typu zadaném pomocí `vtPropType` a nic.  
  
 `vtPropType` Argument je typu **VARTYPE**. Z možných hodnot pro tento argument, která `VARENUM` výčtu. Seznam těchto hodnot, najdete v části poznámky pro `vtRetVal` parametr v [disp_function –](#disp_function). Všimněte si, že `VT_EMPTY`, uvedené v `DISP_FUNCTION` remarks, není povolen jako datový typ vlastnosti.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h 

##  <a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY –  
 Definuje vlastnost automatizace OLE s oznámení v mapě odesílání.  
  
```   
DISP_PROPERTY_NOTIFY(
  theClass, 
  szExternalName, 
  memberName, 
  pfnAfterSet, 
  vtPropType)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Název třídy.  
  
 `szExternalName`  
 Externí název vlastnosti.  
  
 `memberName`  
 Název členské proměnné, ve kterém je uložený vlastnost.  
  
 `pfnAfterSet`  
 Název funkce oznámení pro `szExternalName`.  
  
 `vtPropType`  
 Hodnota určující typ vlastnosti.  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od vlastnosti definované s `DISP_PROPERTY`, vlastnost definovanou s `DISP_PROPERTY_NOTIFY` automaticky zavolá funkci určeného `pfnAfterSet` při změně vlastnosti.  
  
 `vtPropType` Argument je typu **VARTYPE**. Z možných hodnot pro tento argument, která `VARENUM` výčtu:  
  
|Symbol|**Typ vlastnosti**|  
|------------|-----------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**DATUM**|  
|`VT_BSTR`|`CString`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT**|  
|**HODNOTA VT_UNKNOWN**|`LPUNKNOWN`|  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h 

##  <a name="disp_property_param"></a>DISP_PROPERTY_PARAM –  
 Definuje vlastnost přístupný pomocí samostatné **získat** a `Set` členské funkce.  
  
```   
DISP_PROPERTY_PARAM(
  theClass, 
  pszExternalName, 
  pfnGet, 
  pfnSet, 
  vtPropType,
  vtsParams)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Název třídy.  
  
 *pszExternalName*  
 Externí název vlastnosti.  
  
 `pfnGet`  
 Název členské funkce používá GET pro vlastnost.  
  
 `pfnSet`  
 Název členské funkce lze nastavit vlastnost.  
  
 `vtPropType`  
 Hodnota určující typ vlastnosti.  
  
 `vtsParams`  
 Řetězec oddělených mezerami **VTS_** typy variant parametr, jednu pro každý parametr.  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od `DISP_PROPERTY_EX` makro, toto makro umožňuje určit seznam parametrů pro vlastnost. To je užitečné pro implementaci vlastnosti, které jsou indexované nebo parametry.  
  
### <a name="example"></a>Příklad  
 Vezměte v úvahu následující deklaraci get a nastavte členské funkce, které umožňují uživateli požadovat konkrétní řádků a sloupců při přístupu k vlastnosti:  
  
 [!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]  
  
 Tyto odpovídají následující `DISP_PROPERTY_PARAM` makro v odesílání mapy ovládacího prvku:  
  
 [!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]  
  
 Další příklad zvažte následující get a nastavte členské funkce:  
  
 [!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]  
  
 Tyto odpovídají následující `DISP_PROPERTY_PARAM` makro v odesílání mapy ovládacího prvku:  
  
 [!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h 

##  <a name="disp_defvalue"></a>DISP_DEFVALUE –  
 Díky existující vlastnost Výchozí hodnota objektu.  
  
```   
DISP_DEFVALUE(theClass, pszName)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Název třídy.  
  
 `pszName`  
 Externí název vlastnosti, která představuje "hodnota" objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí výchozí hodnotu můžete nastavit programování objektu automatizace jednodušší pro aplikace Visual Basic.  
  
 "Výchozí hodnota" objektu je vlastnost, která je načíst nebo nastavit odkaz na objekt neurčuje vlastnost nebo člen funkce.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h 

## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
