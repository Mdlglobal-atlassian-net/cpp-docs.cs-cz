---
title: Trvalost ovládacích prvků OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 42e70f9e48339eddb2a5af4fa288400cce01f490
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502030"
---
# <a name="persistence-of-ole-controls"></a>Trvalost ovládacích prvků OLE

Jedna z možností ovládacích prvků OLE je trvalá vlastnost (neboli serializace), která umožňuje ovládacímu prvku OLE číst nebo zapisovat hodnoty vlastností do souboru nebo datového proudu. Aplikace typu kontejner může pomocí serializace ukládat hodnoty vlastností ovládacího prvku, i když aplikace zničí ovládací prvek. Hodnoty vlastností ovládacího prvku OLE lze následně číst ze souboru nebo datového proudu, pokud je nová instance ovládacího prvku vytvořena později.

### <a name="persistence-of-ole-controls"></a>Trvalost ovládacích prvků OLE

|||
|-|-|
|[PX_Blob](#px_blob)|Vyměňuje vlastnost ovládacího prvku, která ukládá data binárního rozsáhlého objektu (BLOB).|
|[PX_Bool](#px_bool)|Vyměňuje vlastnost ovládacího prvku typu **bool**.|
|[PX_Color](#px_color)|Vyměňuje vlastnost Color ovládacího prvku.|
|[PX_Currency](#px_currency)|Vyměňuje vlastnost ovládacího prvku typu **CY**.|
|[PX_DataPath](#px_datapath)|Vyměňuje vlastnost ovládacího prvku typu `CDataPathProperty`.|
|[PX_Double](#px_double)|Vyměňuje vlastnost ovládacího prvku typu **Double**.|
|[PX_Font](#px_font)|Vyměňuje vlastnost písma ovládacího prvku.|
|[PX_Float](#px_float)|Vyměňuje vlastnost ovládacího prvku typu **float**.|
|[PX_IUnknown](#px_iunknown)|Vyměňuje vlastnost ovládacího prvku nedefinovaného typu.|
|[PX_Long](#px_long)|Vyměňuje vlastnost ovládacího prvku typu **Long**.|
|[PX_Picture](#px_picture)|Vyměňuje vlastnost obrázku ovládacího prvku.|
|[PX_Short](#px_short)|Vyměňuje vlastnost ovládacího prvku typu **short**.|
|[PX_ULong](#px_ulong)|Vyměňuje vlastnost ovládacího prvku typu **ulong**.|
|[PX_UShort](#px_ushort)|Vyměňuje vlastnost ovládacího prvku typu **UShort**.|
|[PXstring](#px_string)|Vyměňuje vlastnost ovládacího prvku řetězce znaků.|
|[PX_VBXFontConvert](#px_vbxfontconvert)|Vyměňuje vlastnosti související se písemou ovládacího prvku VBX do vlastnosti písma ovládacího prvku OLE.|

Kromě toho `AfxOleTypeMatchGuid` je k dispozici globální funkce pro testování shody mezi TYPEDESC a daným identifikátorem GUID.

##  <a name="px_blob"></a>  PX_Blob

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost, která ukládá binární data rozsáhlých objektů (BLOB).

```
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*hBlob*<br/>
Odkaz na proměnnou, kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

*hBlobDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti bude načtena z nebo zapsána do proměnné, na kterou odkazuje *hBlob*, podle potřeby. Tato proměnná by měla být inicializována na hodnotu null `PX_Blob` před prvním voláním metody First (obvykle to lze provést v konstruktoru ovládacího prvku). Je-li zadán parametr *hBlobDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu dojde k chybě inicializace nebo procesu serializace ovládacího prvku.

Obslužné rutiny *hBlob* a *hBlobDefault* odkazují na blok paměti, který obsahuje následující:

- Hodnota DWORD obsahující délku binárních dat (v bajtech), za kterým následuje

- Blok paměti obsahující skutečná binární data.

Počítejte s `PX_Blob` tím, že při načítání vlastností typu objektu BLOB přidělí paměť pomocí rozhraní API pro Windows [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) . Zodpovídáte za uvolnění této paměti. Proto by destruktor vašeho ovládacího prvku měl volat [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) na jakékoli obslužné rutiny vlastností typu BLOB, aby uvolnila veškerou paměť přidělenou vašemu ovládacímu prvku.

##  <a name="px_bool"></a>  PX_Bool

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost typu bool.

```
BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue);

BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue,
    BOOL bDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*bValue*<br/>
Odkaz na proměnnou, kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

*bDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti bude načtena z nebo zapsána do proměnné, na kterou odkazuje *bValue*, podle potřeby. Je-li zadán parametr *bDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku.

##  <a name="px_color"></a>PX_Color

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost typu OLE_COLOR.

```
BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue,
    OLE_COLOR clrDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*clrValue*<br/>
Odkaz na proměnnou, kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

*clrDefault*<br/>
Výchozí hodnota vlastnosti, jak je definována vývojářem ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti bude načtena z nebo zapsána do proměnné, na kterou odkazuje *clrValue*, podle potřeby. Je-li zadán parametr *clrDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku.

##  <a name="px_currency"></a>PX_Currency

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost typu **Currency**.

```
BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue);

BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue,
    CY cyDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*cyValue*<br/>
Odkaz na proměnnou, kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

*cyDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti bude načtena z nebo zapsána do proměnné, na kterou odkazuje *cyValue*, podle potřeby. Je-li zadán parametr *cyDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku.

##  <a name="px_datapath"></a>  PX_DataPath

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost cesty dat typu [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).

```
BOOL PX_DataPath(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CDataPathProperty& dataPathProperty);

BOOL PX_DataPath(
    CPropExchange* pPX,
    CDataPathProperty& dataPathProperty);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*dataPathProperty*<br/>
Odkaz na proměnnou, kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Vlastnosti cesty k datům implementují vlastnosti asynchronního řízení. Hodnota vlastnosti bude načtena z nebo zapsána do proměnné, na kterou odkazuje *dataPathProperty*, podle potřeby.

##  <a name="px_double"></a>PX_Double

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost typu **Double**.

```
BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue);

BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue,
    double doubleDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*doubleValue*<br/>
Odkaz na proměnnou, kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

*doubleDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je čtena nebo zapsána do proměnné, na kterou odkazuje *doubleValue*, podle potřeby. Je-li zadán parametr *doubleDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku.

##  <a name="px_font"></a>PX_Font

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost typu Font.

```
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*písma*<br/>
Odkaz na `CFontHolder` objekt, který obsahuje vlastnost font.

*pFontDesc*<br/>
Ukazatel na `FONTDESC` strukturu obsahující hodnoty, které mají být použity při inicializaci výchozího stavu vlastnosti Font, v případě, že *pFontDispAmbient* má hodnotu null.

*pFontDispAmbient*<br/>
Ukazatel na `IFontDisp` rozhraní písma, které má být použito při inicializaci výchozího stavu vlastnosti Font.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je přečtena nebo zapsána na `font` `CFontHolder` odkaz, pokud je to vhodné. Pokud jsou zadány *pFontDesc* a *pFontDispAmbient* , používají se k inicializaci výchozí hodnoty vlastnosti v případě potřeby. Tyto hodnoty se používají, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku. Obvykle předáte null pro *pFontDesc* a okolní hodnotu vrácenou `COleControl::AmbientFont` pro *pFontDispAmbient*. Všimněte si, že objekt Font vrácený `COleControl::AmbientFont` musí být vydán voláním `IFontDisp::Release` členské funkce.

##  <a name="px_float"></a>PX_Float

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost typu **float**.

```
BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue);

BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue,
    float floatDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*floatValue*<br/>
Odkaz na proměnnou, kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

*floatDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je čtena nebo zapsána do proměnné, na kterou odkazuje *floatValue*, podle potřeby. Je-li zadán parametr *floatDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku.

##  <a name="px_iunknown"></a>PX_IUnknown

Volání této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku k serializaci nebo inicializaci vlastnosti reprezentované objektem, který `IUnknown`má odvozené rozhraní.

```
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*pUnk*<br/>
Odkaz na proměnnou obsahující rozhraní objektu, který představuje hodnotu vlastnosti.

*iid*<br/>
ID rozhraní, které určuje, které rozhraní objektu vlastnosti je používáno ovládacím prvkem.

*pUnkDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je čtena nebo zapsána do proměnné, na kterou odkazuje *punk*, podle potřeby. Je-li zadán parametr *pUnkDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku.

##  <a name="px_long"></a>PX_Long

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost typu **Long**.

```
BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue);

BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue,
    long lDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*Hodnotou*<br/>
Odkaz na proměnnou, kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

*lDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je čtena nebo zapsána do proměnné, na kterou odkazuje hodnota *lValue*, podle potřeby. Je-li zadán parametr *lDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku.

##  <a name="px_picture"></a>PX_Picture

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost obrázku vašeho ovládacího prvku.

```
BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict);

BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict,
    CPictureHolder& pictDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*PICT*<br/>
Odkaz na objekt [CPictureHolder](../../mfc/reference/cpictureholder-class.md) , kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

*pictDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je čtena nebo zapsána do proměnné, na kterou odkazuje *PICT*, podle potřeby. Je-li zadán parametr *pictDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku.

##  <a name="px_short"></a>PX_Short

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost typu **short**.

```
BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue);

BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue,
    short sDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*sValue*<br/>
Odkaz na proměnnou, kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

*sDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je čtena nebo zapsána do proměnné, na kterou odkazuje *sValue*, podle potřeby. Je-li zadán parametr *sDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku.

##  <a name="px_ulong"></a>  PX_ULong

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost typu **ulong**.

```
BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue);

BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue,
    long ulDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*ulValue*<br/>
Odkaz na proměnnou, kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

*ulDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je čtena nebo zapsána do proměnné, na kterou odkazuje *ulValue*, podle potřeby. Je-li zadán parametr *ulDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku.

##  <a name="px_ushort"></a>  PX_UShort

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost typu **short bez znaménka**.

```
BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue);

BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue,
    USHORT usDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*usValue*<br/>
Odkaz na proměnnou, kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

*usDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je čtena nebo zapsána do proměnné, na kterou odkazuje *usValue*, podle potřeby. Je-li zadán parametr *usDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku.

##  <a name="px_string"></a>PXstring

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete serializovat nebo inicializovat vlastnost řetězce znaků.

```
BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue);

BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue,
    CString strDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Název vyměněné vlastnosti.

*strValue*<br/>
Odkaz na proměnnou, kde je vlastnost uložena (obvykle členská proměnná vaší třídy).

*strDefault*<br/>
Výchozí hodnota vlastnosti

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je čtena nebo zapsána do proměnné, na kterou odkazuje *strValue*, podle potřeby. Je-li zadán parametr *strDefault* , bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z jakéhokoli důvodu neproběhne proces serializace ovládacího prvku.

##  <a name="px_vbxfontconvert"></a>PX_VBXFontConvert

Voláním této funkce v rámci `DoPropExchange` členské funkce ovládacího prvku můžete inicializovat vlastnost písma převedením vlastností souvisejících s písmem ovládacího prvku VBX.

```
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na objekt [CPropExchange](../../mfc/reference/cpropexchange-class.md) (obvykle předaný jako parametr do `DoPropExchange`).

*písma*<br/>
Vlastnost font ovládacího prvku OLE, který bude obsahovat převedené vlastnosti týkající se písma VBX

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo Exchange úspěšné; 0, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být používána pouze ovládacím prvkem OLE, který je navržen jako přímá náhrada pro ovládací prvek VBX. Když Visual Basic vývojové prostředí převede formulář obsahující ovládací prvek VBX tak, aby používal odpovídající náhradní ovládací prvek OLE, vyvolá `IDataObject::SetData` funkci ovládacího prvku, která předává sadu vlastností, která obsahuje data vlastnosti ovládacího prvku VBX. Tato operace zase způsobí vyvolání `DoPropExchange` funkce ovládacího prvku. `DoPropExchange`může zavolat `PX_VBXFontConvert` , aby se převedly vlastnosti související se fonty ovládacího prvku VBX (například "font", "FontSize" atd.) do odpovídajících komponent vlastnosti Font ovládacího prvku OLE.

`PX_VBXFontConvert`by měla být volána pouze v případě, že je ovládací prvek skutečně převáděn z aplikace VBX Form. Příklad:

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
