---
title: Třída CPropExchange | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPropExchange
- AFXCTL/CPropExchange
- AFXCTL/CPropExchange::ExchangeBlobProp
- AFXCTL/CPropExchange::ExchangeFontProp
- AFXCTL/CPropExchange::ExchangePersistentProp
- AFXCTL/CPropExchange::ExchangeProp
- AFXCTL/CPropExchange::ExchangeVersion
- AFXCTL/CPropExchange::GetVersion
- AFXCTL/CPropExchange::IsAsynchronous
- AFXCTL/CPropExchange::IsLoading
dev_langs:
- C++
helpviewer_keywords:
- CPropExchange [MFC], ExchangeBlobProp
- CPropExchange [MFC], ExchangeFontProp
- CPropExchange [MFC], ExchangePersistentProp
- CPropExchange [MFC], ExchangeProp
- CPropExchange [MFC], ExchangeVersion
- CPropExchange [MFC], GetVersion
- CPropExchange [MFC], IsAsynchronous
- CPropExchange [MFC], IsLoading
ms.assetid: ed872180-e770-4942-892a-92139d501fab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f234b3f06e22308a31e8e5694648fd5664b448a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377337"
---
# <a name="cpropexchange-class"></a>CPropExchange – třída
Podporuje provádění trvalosti pro vaše ovládací prvky OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class AFX_NOVTABLE CPropExchange  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Výměny vlastnost binární rozsáhlý objekt (binární rozsáhlý OBJEKT).|  
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Výměny vlastnost písma.|  
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Výměny vlastnost mezi ovládacího prvku a soubor.|  
|[CPropExchange::ExchangeProp](#exchangeprop)|Výměnu vlastnosti všech předdefinovaných typů.|  
|[CPropExchange::ExchangeVersion](#exchangeversion)|Výměny číslo verze ovládacího prvku OLE.|  
|[CPropExchange::GetVersion](#getversion)|Načte číslo verze ovládacího prvku OLE.|  
|[CPropExchange::IsAsynchronous](#isasynchronous)|Určuje, pokud vlastnost výměnu hotovi asynchronně.|  
|[CPropExchange::IsLoading](#isloading)|Určuje, zda vlastnosti bude načten do ovládacího prvku nebo uložit z něj.|  
  
## <a name="remarks"></a>Poznámky  
 `CPropExchange` nemá základní třídu.  
  
 Určuje kontextu a směr vlastnost exchange.  
  
 Trvalost je exchange informace o stavu ovládacího prvku, obvykle reprezentován jeho vlastnosti, mezi samotném ovládacím prvku a střední.  
  
 Rozhraní framework vytvoří objekt odvozené z `CPropExchange` uložené do trvalého úložiště nebo když je oznámeno, že vlastnosti ovládacího prvku OLE mají být načteny z.  
  
 Rozhraní framework předá ukazatel to `CPropExchange` objekt ovládacího prvku `DoPropExchange` funkce. Pokud jste použili průvodce k vytvoření počáteční soubory pro vaše ovládacího prvku, vlastní ovládací prvek `DoPropExchange` volání funkce `COleControl::DoPropExchange`. Základní třída verze výměny uložených vlastností ovládacího prvku; můžete upravit odvozené třídy verze na vlastnosti serveru exchange, že jste přidali do vlastního ovládacího prvku.  
  
 `CPropExchange` slouží k serializaci vlastností ovládacího prvku nebo inicializace vlastností ovládacího prvku při zatížení nebo vytvoření ovládacího prvku. `ExchangeProp` a `ExchangeFontProp` členské funkce `CPropExchange` dokážou a uložit vlastnosti, které chcete je načíst z různých média.  
  
 Další informace o používání `CPropExchange`, najdete v článku [MFC – ovládací prvky ActiveX: stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CPropExchange`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h  
  
##  <a name="exchangeblobprop"></a>  CPropExchange::ExchangeBlobProp  
 Serializuje vlastnost, která ukládá data binární rozsáhlý objekt (binární rozsáhlý OBJEKT).  
  
```  
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,  
    HGLOBAL* phBlob,  
    HGLOBAL hBlobDefault = NULL) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `phBlob`  
 Ukazatel na proměnnou ukazující na uložení vlastnost (proměnné je obvykle členem třídě).  
  
 `hBlobDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst z nebo zapisovat do, jak je to vhodné, proměnná odkazuje `phBlob`. Pokud `hBlobDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže serializace ovládacího prvku.  
  
 Funkce **CArchivePropExchange::ExchangeBlobProp**, **CResetPropExchange::ExchangeBlobProp**, a **CPropsetPropExchange::ExchangeBlobProp** přepsání Tato čistý virtuální funkce.  
  
##  <a name="exchangefontprop"></a>  CPropExchange::ExchangeFontProp  
 Výměny vlastnost písma mezi střední úložiště a ovládacího prvku.  
  
```  
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,  
    CFontHolder& font,  
    const FONTDESC* pFontDesc,  
    LPFONTDISP pFontDispAmbient) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `font`  
 Odkaz na [CFontHolder](../../mfc/reference/cfontholder-class.md) objekt, který obsahuje vlastnost písma.  
  
 `pFontDesc`  
 Ukazatel na [FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782) struktura obsahující hodnoty pro inicializaci výchozí stav vlastnost písmo při `pFontDispAmbient` je **NULL**.  
  
 `pFontDispAmbient`  
 Ukazatel **IFontDisp** rozhraní písma, který se má použít pro inicializaci vlastnosti písmo výchozího stavu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se vlastnost font je právě načítán z média do ovládacího prvku, charakteristiky písma jsou načteny z média a `CFontHolder` odkazuje objekt `font` je inicializován s nimi. Pokud vlastnost písma ukládají, zapíšou se do médium vlastnosti v objektu písma.  
  
 Funkce **CArchivePropExchange::ExchangeFontProp**, **CResetPropExchange::ExchangeFontProp**, a **CPropsetPropExchange::ExchangeFontProp** přepsání Tato čistý virtuální funkce.  
  
##  <a name="exchangepersistentprop"></a>  CPropExchange::ExchangePersistentProp  
 Výměny vlastnost mezi ovládacího prvku a soubor.  
  
```  
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,  
    LPUNKNOWN* ppUnk,  
    REFIID iid,  
    LPUNKNOWN pUnkDefault) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `ppUnk`  
 Ukazatel na proměnné obsahující ukazatel na vlastnosti **IUnknown** rozhraní (Tato proměnná je obvykle členem třídě).  
  
 `iid`  
 ID rozhraní rozhraní u vlastnosti, který bude používat ovládací prvek.  
  
 `pUnkDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vlastnost se načítá ze souboru do ovládacího prvku, vlastnost je vytvořen a inicializován ze souboru. Pokud vlastnost ukládají, jeho hodnota je zapsán do souboru.  
  
 Funkce **CArchivePropExchange::ExchangePersistentProp**, **CResetPropExchange::ExchangePersistentProp**, a **CPropsetPropExchange::ExchangePersistentProp** čistý virtuální funkci přepsat.  
  
##  <a name="exchangeprop"></a>  CPropExchange::ExchangeProp  
 Výměny vlastnost mezi střední úložiště a ovládacího prvku.  
  
```  
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,  
    VARTYPE vtProp,  
    void* pvProp,  
    const void* pvDefault = NULL) = 0 ;  
```  
  
### <a name="parameters"></a>Parametry  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `vtProp`  
 Symbol určení typu vlastnosti během výměny. Možné hodnoty jsou:  
  
|Symbol|Typ vlastnosti|  
|------------|-------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_BOOL`|**BOOL**|  
|`VT_BSTR`|`CString`|  
|`VT_CY`|**CY**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
  
 `pvProp`  
 Ukazatel na hodnotu vlastnosti.  
  
 *pvDefault*  
 Ukazatel na výchozí hodnotu pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vlastnost je právě načítán z média do ovládacího prvku, hodnota vlastnosti je načtena z média a uložené v objektu, na kterou odkazuje `pvProp`. Pokud je vlastnost je uložen na médium, hodnota objektu, na kterou odkazuje `pvProp` je zapsán do média.  
  
 Funkce **CArchivePropExchange::ExchangeProp**, **CResetPropExchange::ExchangeProp**, a **CPropsetPropExchange::ExchangeProp** přepsat tuto čisté virtuální funkce.  
  
##  <a name="exchangeversion"></a>  CPropExchange::ExchangeVersion  
 Voláno rámcem pro zpracování trvalost číslo verze.  
  
```  
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,  
    DWORD dwVersionDefault,  
    BOOL bConvert);
```  
  
### <a name="parameters"></a>Parametry  
 *dwVersionLoaded*  
 Odkaz na proměnnou, kde bude uložena číslo verze trvalé načítaná data.  
  
 `dwVersionDefault`  
 Aktuální číslo verze ovládacího prvku.  
  
 `bConvert`  
 Označuje, zda trvalá data převést do aktuální verze nebo jej zachovat na stejnou verzi, která byla načtena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se funkce úspěšně; jinak 0.  
  
##  <a name="getversion"></a>  CPropExchange::GetVersion  
 Volání této funkce načíst číslo verze ovládacího prvku.  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo verze ovládacího prvku.  
  
##  <a name="isasynchronous"></a>  CPropExchange::IsAsynchronous  
 Určuje, pokud vlastnost výměnu hotovi asynchronně.  
  
```  
BOOL IsAsynchronous();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud jsou vlastnosti vyměňují asynchronně, jinak hodnota FALSE.  
  
##  <a name="isloading"></a>  CPropExchange::IsLoading  
 Volání této funkce k určení, zda vlastnosti bude načten do ovládacího prvku nebo uložit z něj.  
  
```  
BOOL IsLoading();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud vlastnosti jsou načítány; jinak 0.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)



