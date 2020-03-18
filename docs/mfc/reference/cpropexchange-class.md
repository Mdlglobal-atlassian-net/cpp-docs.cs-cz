---
title: CPropExchange – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: e9ad7c363f2580200af20baeb0acd7a93c1f603b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420993"
---
# <a name="cpropexchange-class"></a>CPropExchange – třída

Podporuje implementaci trvalosti pro ovládací prvky OLE.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Vyměňuje vlastnost binárního rozsáhlého objektu (BLOB).|
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Vyměňuje vlastnost písma.|
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Vyměňuje vlastnost mezi ovládacím prvkem a souborem.|
|[CPropExchange::ExchangeProp](#exchangeprop)|Vyměňuje vlastnosti libovolného předdefinovaného typu.|
|[CPropExchange::ExchangeVersion](#exchangeversion)|Vyměňuje číslo verze ovládacího prvku OLE.|
|[CPropExchange:: GetVersion](#getversion)|Načte číslo verze ovládacího prvku OLE.|
|[CPropExchange::-Asynchronous](#isasynchronous)|Určuje, jestli se výměny vlastností provádějí asynchronně.|
|[CPropExchange:: IsLoaded](#isloading)|Určuje, zda jsou vlastnosti načítány do ovládacího prvku nebo z něj uloženy.|

## <a name="remarks"></a>Poznámky

`CPropExchange` nemá základní třídu.

Vytvoří kontext a směr výměny vlastností.

Trvalost je výměna informací o stavu ovládacího prvku, obvykle reprezentovaných jeho vlastnostmi, mezi samotným ovládacím prvkem a médiem.

Rozhraní vytvoří objekt odvozený z `CPropExchange`, když je informován o tom, že vlastnosti ovládacího prvku OLE mají být načteny nebo uloženy do trvalého úložiště.

Rozhraní předá ukazatel na tento objekt `CPropExchange` do funkce `DoPropExchange` ovládacího prvku. Pokud jste použili Průvodce pro vytvoření počátečních souborů pro ovládací prvek, funkce `DoPropExchange` ovládacího prvku zavolá `COleControl::DoPropExchange`. Verze základní třídy vyměňuje základní vlastnosti ovládacího prvku; můžete změnit verzi odvozené třídy na vlastnosti serveru Exchange, které jste přidali do ovládacího prvku.

`CPropExchange` lze použít k serializaci vlastností ovládacího prvku nebo inicializaci vlastností ovládacího prvku na základě zatížení nebo vytvoření ovládacího prvku. Členské funkce `CPropExchange` `ExchangeProp` a `ExchangeFontProp` mohou ukládat vlastnosti do a načíst je z různých médií.

Další informace o použití `CPropExchange`naleznete v článku [ovládací prvky ActiveX knihovny MFC: stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CPropExchange`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXCTL. h

##  <a name="exchangeblobprop"></a>CPropExchange::ExchangeBlobProp

Zaserializace vlastnost, která ukládá binární data rozsáhlých objektů (BLOB).

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Název vyměněné vlastnosti.

*phBlob*<br/>
Ukazatel na proměnnou odkazující na místo, kde je vlastnost uložena (proměnná je obvykle členem vaší třídy).

*hBlobDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je v případě potřeby čtena z nebo zapsána do proměnné, na kterou odkazuje *phBlob*. Je-li zadán parametr *hBlobDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu dojde k chybě serializace ovládacího prvku.

Tato čistě virtuální funkce se přepíší funkcemi `CArchivePropExchange::ExchangeBlobProp`, `CResetPropExchange::ExchangeBlobProp`a `CPropsetPropExchange::ExchangeBlobProp`.

##  <a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp

Vyměňuje vlastnost font mezi úložným médiem a ovládacím prvkem.

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Název vyměněné vlastnosti.

*písma*<br/>
Odkaz na objekt [CFontHolder](../../mfc/reference/cfontholder-class.md) , který obsahuje vlastnost font.

*pFontDesc*<br/>
Ukazatel na strukturu [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc) obsahující hodnoty pro inicializaci výchozího stavu vlastnosti Font, když má *pFontDispAmbient* hodnotu null.

*pFontDispAmbient*<br/>
Ukazatel na `IFontDisp` rozhraní písma, které se má použít k inicializaci výchozího stavu vlastnosti Font.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Pokud je vlastnost font načítána ze středníku do ovládacího prvku, charakteristiky písma jsou načteny ze střední a objekt `CFontHolder`, na který je odkazováno pomocí *písma* , je inicializován s nimi. Pokud je vlastnost font ukládána, jsou charakteristiky v objektu Font zapisovány do středníku.

Tato čistě virtuální funkce se přepíší funkcemi `CArchivePropExchange::ExchangeFontProp`, `CResetPropExchange::ExchangeFontProp`a `CPropsetPropExchange::ExchangeFontProp`.

##  <a name="exchangepersistentprop"></a>CPropExchange::ExchangePersistentProp

Vyměňuje vlastnost mezi ovládacím prvkem a souborem.

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Název vyměněné vlastnosti.

*ppUnk*<br/>
Ukazatel na proměnnou obsahující ukazatel na rozhraní `IUnknown` vlastnosti (Tato proměnná je obvykle členem vaší třídy).

*identifikátor*<br/>
ID rozhraní u vlastnosti, kterou bude ovládací prvek používat.

*pUnkDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Pokud je vlastnost načítána ze souboru do ovládacího prvku, je vlastnost vytvořena a inicializována ze souboru. Pokud je vlastnost ukládána, její hodnota je zapsána do souboru.

Tato čistě virtuální funkce se přepíší funkcemi `CArchivePropExchange::ExchangePersistentProp`, `CResetPropExchange::ExchangePersistentProp`a `CPropsetPropExchange::ExchangePersistentProp`.

##  <a name="exchangeprop"></a>CPropExchange::ExchangeProp

Vyměňuje vlastnost mezi úložným médiem a ovládacím prvkem.

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Název vyměněné vlastnosti.

*vtProp*<br/>
Symbol určující typ vyměňovaných vlastností. Možné hodnoty:

|Písmeno|Typ vlastnosti|
|------------|-------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_BOOL|**LOGICK**|
|VT_BSTR|`CString`|
|VT_CY|**KR**|
|VT_R4|**float**|
|VT_R8|**double**|

*pvProp*<br/>
Ukazatel na hodnotu vlastnosti.

*pvDefault*<br/>
Ukazatel na výchozí hodnotu pro vlastnost.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Pokud je vlastnost načítána ze střední hodnoty do ovládacího prvku, je hodnota vlastnosti načtena z média a uložena v objektu, na který odkazuje *pvProp*. Pokud je vlastnost ukládána na střední hodnotu, hodnota objektu, na kterou ukazuje *pvProp* , je zapsána do středníku.

Tato čistě virtuální funkce se přepíší funkcemi `CArchivePropExchange::ExchangeProp`, `CResetPropExchange::ExchangeProp`a `CPropsetPropExchange::ExchangeProp`.

##  <a name="exchangeversion"></a>CPropExchange::ExchangeVersion

Volá se rozhraním, aby se zpracovával trvalost čísla verze.

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>Parametry

*dwVersionLoaded*<br/>
Odkaz na proměnnou, kde bude uloženo číslo verze trvalých dat, která budou načtena.

*dwVersionDefault*<br/>
Aktuální číslo verze ovládacího prvku.

*bConvert*<br/>
Označuje, zda se mají převést trvalá data na aktuální verzi, nebo zachovat stejnou verzi, která byla načtena.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; 0, jinak.

##  <a name="getversion"></a>CPropExchange:: GetVersion

Voláním této funkce načtete číslo verze ovládacího prvku.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Návratová hodnota

Číslo verze ovládacího prvku.

##  <a name="isasynchronous"></a>CPropExchange::-Asynchronous

Určuje, jestli se výměny vlastností provádějí asynchronně.

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud jsou vlastnosti vyměněny asynchronně, jinak FALSE.

##  <a name="isloading"></a>CPropExchange:: IsLoaded

Voláním této funkce určíte, zda jsou vlastnosti načítány do ovládacího prvku nebo z něj uloženy.

```
BOOL IsLoading();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou vlastnosti načítány; v opačném případě 0.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleControl –::D oPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
