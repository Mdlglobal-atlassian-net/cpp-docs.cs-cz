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
ms.openlocfilehash: 7818b15e502bb32640d6b9dbfe1a6e4927c70650
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363974"
---
# <a name="cpropexchange-class"></a>CPropExchange – třída

Podporuje implementaci trvalosti pro ovládací prvky OLE.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Vyměňuje binární velký objekt (BLOB) vlastnost.|
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Vyměňuje vlastnost písma.|
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Vyměňuje vlastnost mezi ovládacím prvkem a souborem.|
|[CPropExchange::ExchangeProp](#exchangeprop)|Vyměňuje vlastnosti jakéhokoli vestavěného typu.|
|[CPropExchange::ExchangeVersion](#exchangeversion)|Vymění číslo verze ovládacího prvku OLE.|
|[CPropExchange::GetVersion](#getversion)|Načte číslo verze ovládacího prvku OLE.|
|[CPropExchange::IsAsynchronní](#isasynchronous)|Určuje, zda jsou výměny vlastností prováděny asynchronně.|
|[CPropExchange::Načítání](#isloading)|Označuje, zda jsou vlastnosti načteny do ovládacího prvku nebo z něj uloženy.|

## <a name="remarks"></a>Poznámky

`CPropExchange`nemá základní třídu.

Stanoví kontext a směr výměny vlastností.

Trvalost je výměna informací o stavu ovládacího prvku, obvykle reprezentované jeho vlastnosti, mezi samotným ovládacím prvkem a médium.

Rozhraní framework vytvoří objekt odvozený od `CPropExchange` když je upozorněn, že vlastnosti ovládacího prvku OLE mají být načteny z nebo uloženy do trvalého úložiště.

Rozhraní framework předá `CPropExchange` ukazatel na tento `DoPropExchange` objekt na funkci ovládacího prvku. Pokud jste k vytvoření počátečních souborů ovládacího prvku `DoPropExchange` použili `COleControl::DoPropExchange`průvodce, volání funkce ovládacího prvku . Verze základní třídy vyměňuje vlastnosti skladu ovládacího prvku; upravíte verzi odvozené třídy tak, aby si vyměňovala vlastnosti, které jste přidali do ovládacího prvku.

`CPropExchange`lze použít k serializaci vlastností ovládacího prvku nebo inicializaci vlastností ovládacího prvku při zatížení nebo vytvoření ovládacího prvku. A `ExchangeProp` `ExchangeFontProp` členské funkce `CPropExchange` jsou schopny ukládat vlastnosti a načíst je z různých médií.

Další informace o `CPropExchange`použití naleznete v článku [Ovládací prvky ActiveX knihovny MFC: Stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CPropExchange`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a>CPropExchange::ExchangeBlobProp

Serializuje vlastnost, která ukládá binární data velkých objektů (BLOB).

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*phBlob*<br/>
Ukazatel na proměnnou ukazující na místo, kde je uložena vlastnost (proměnná je obvykle členem vaší třídy).

*hBlobVýchozí*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je přečtena nebo zapsána do proměnné, na kterou odkazuje *phBlob*. Pokud je zadán *hBlobDefault,* bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selhání serializace ovládacího prvku.

Funkce `CArchivePropExchange::ExchangeBlobProp`, `CResetPropExchange::ExchangeBlobProp`a `CPropsetPropExchange::ExchangeBlobProp` přepsat tuto čistou virtuální funkci.

## <a name="cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp

Vyměňuje vlastnost písma mezi paměťovým médiem a ovládacím prvkem.

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*Písma*<br/>
Odkaz na [CFontHolder](../../mfc/reference/cfontholder-class.md) objekt, který obsahuje vlastnost font.

*pFontDesc*<br/>
Ukazatel na strukturu [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc) obsahující hodnoty pro inicializaci výchozího stavu vlastnosti písma, když je *hodnota null pFontDispAmbient.*

*pFontDispAmbient*<br/>
Ukazatel na `IFontDisp` rozhraní písma, které má být použito pro inicializaci výchozího stavu vlastnosti písma.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Pokud je vlastnost písma načítána z média do ovládacího prvku, vlastnosti `CFontHolder` písma jsou načteny z média a objekt odkazovaný *písmem* je inicializován s nimi. Pokud je vlastnost písma ukládat, vlastnosti v objektu písma jsou zapsány na médium.

Funkce `CArchivePropExchange::ExchangeFontProp`, `CResetPropExchange::ExchangeFontProp`a `CPropsetPropExchange::ExchangeFontProp` přepsat tuto čistou virtuální funkci.

## <a name="cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a>CPropExchange::ExchangePersistentProp

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
Název nemovitosti, která je vyměňována.

*ppUnk*<br/>
Ukazatel na proměnnou obsahující ukazatel na `IUnknown` rozhraní vlastnosti (tato proměnná je obvykle členem vaší třídy).

*Iid*<br/>
ID rozhraní rozhraní na vlastnost, která bude používat ovládací prvek.

*pUnkVýchozí*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Pokud je vlastnost načítána ze souboru do ovládacího prvku, vlastnost je vytvořena a inicializována ze souboru. Pokud je vlastnost uložena, její hodnota je zapsána do souboru.

Funkce `CArchivePropExchange::ExchangePersistentProp`, `CResetPropExchange::ExchangePersistentProp`a `CPropsetPropExchange::ExchangePersistentProp` přepsat tuto čistou virtuální funkci.

## <a name="cpropexchangeexchangeprop"></a><a name="exchangeprop"></a>CPropExchange::ExchangeProp

Vyměňuje vlastnost mezi paměťovým médiem a ovládacím prvkem.

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*vtProp*<br/>
Symbol určující typ vyměňované vlastnosti. Možné hodnoty:

|Symbol|Typ vlastnosti|
|------------|-------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_BOOL|**Bool**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**float**|
|VT_R8|**double**|

*pvProp*<br/>
Ukazatel na hodnotu vlastnosti.

*pvVýchozí*<br/>
Ukazatel na výchozí hodnotu vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Pokud je vlastnost načtena z média do ovládacího prvku, hodnota vlastnosti je načtena z média a uložena v objektu, na který se vztahuje *pvProp*. Pokud je vlastnost uložena na médium, hodnota objektu, na který *pvProp* je zapsána na médium.

Funkce `CArchivePropExchange::ExchangeProp`, `CResetPropExchange::ExchangeProp`a `CPropsetPropExchange::ExchangeProp` přepsat tuto čistou virtuální funkci.

## <a name="cpropexchangeexchangeversion"></a><a name="exchangeversion"></a>CPropExchange::ExchangeVersion

Volat rámci pro zpracování trvalost číslo verze.

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>Parametry

*dwVersionLoaded*<br/>
Odkaz na proměnnou, kde bude uloženo číslo verze načítaných dat.

*dwVersionDefault*<br/>
Aktuální číslo verze ovládacího prvku.

*bPřevést*<br/>
Označuje, zda chcete převést trvalá data na aktuální verzi nebo ji zachovat ve stejné verzi, která byla načtena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná; 0 jinak.

## <a name="cpropexchangegetversion"></a><a name="getversion"></a>CPropExchange::GetVersion

Volání této funkce načíst číslo verze ovládacího prvku.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Návratová hodnota

Číslo verze ovládacího prvku.

## <a name="cpropexchangeisasynchronous"></a><a name="isasynchronous"></a>CPropExchange::IsAsynchronní

Určuje, zda jsou výměny vlastností prováděny asynchronně.

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud jsou vlastnosti vyměňovány asynchronně, jinak NEPRAVDA.

## <a name="cpropexchangeisloading"></a><a name="isloading"></a>CPropExchange::Načítání

Volání této funkce k určení, zda vlastnosti jsou načteny do ovládacího prvku nebo uloženy z něj.

```
BOOL IsLoading();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou načítány vlastnosti; jinak 0.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
