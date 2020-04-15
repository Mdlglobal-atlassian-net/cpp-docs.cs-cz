---
title: Trvalost ovládacích prvků OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 88707da503b1d1cdc809827dc4d1bac0ccad9b5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373001"
---
# <a name="persistence-of-ole-controls"></a>Trvalost ovládacích prvků OLE

Jednou z možností ovládacích prvků OLE je trvalost vlastností (nebo serializace), která umožňuje ovládacímu prvku OLE číst nebo zapisovat hodnoty vlastností do a ze souboru nebo datového proudu. Aplikace kontejneru můžete použít serializace k uložení hodnoty vlastností ovládacího prvku i poté, co aplikace zničila ovládací prvek. Hodnoty vlastností ovládacího prvku OLE lze pak číst ze souboru nebo datového proudu při vytvoření nové instance ovládacího prvku později.

### <a name="persistence-of-ole-controls"></a>Trvalost ovládacích prvků OLE

|||
|-|-|
|[PX_Blob](#px_blob)|Vyměňuje vlastnost ovládacího prvku, která ukládá binární data velkých objektů (BLOB).|
|[PX_Bool](#px_bool)|Vyměňuje řídicí vlastnost typu **BOOL**.|
|[PX_Color](#px_color)|Vymění vlastnost color ovládacího prvku.|
|[PX_Currency](#px_currency)|Vyměňuje kontrolní vlastnost typu **CY**.|
|[PX_DataPath](#px_datapath)|Vyměňuje vlastnost ovládacího prvku typu `CDataPathProperty`.|
|[PX_Double](#px_double)|Vyměňuje vlastnost ovládacího prvku typu **double**.|
|[PX_Font](#px_font)|Vymění vlastnost písma ovládacího prvku.|
|[PX_Float](#px_float)|Vyměňuje vlastnost ovládacího prvku typu **float**.|
|[PX_IUnknown](#px_iunknown)|Vyměňuje vlastnost ovládacího prvku nedefinovaného typu.|
|[PX_Long](#px_long)|Vyměňuje vlastnost ovládacího prvku typu **long**.|
|[PX_Picture](#px_picture)|Vymění vlastnost obrázku ovládacího prvku.|
|[PX_Short](#px_short)|Vyměňuje vlastnost ovládacího prvku typu **short**.|
|[PX_ULong](#px_ulong)|Vyměňuje vlastnost ovládacího prvku typu **ULONG**.|
|[PX_UShort](#px_ushort)|Vyměňuje vlastnost ovládacího prvku typu **USHORT**.|
|[PXstring](#px_string)|Vymění vlastnost ovládacího prvku řetězce znaků.|
|[PX_VBXFontConvert](#px_vbxfontconvert)|Vymění vlastnosti ovládacího prvku VBX související s písmem do vlastnosti písma ovládacího prvku OLE.|

Kromě toho `AfxOleTypeMatchGuid` je k dispozici globální funkce pro testování shody mezi TYPEDESC a dané GUID.

## <a name="px_blob"></a><a name="px_blob"></a>PX_Blob

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost, která ukládá binární data velkých objektů (BLOB).

```cpp
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*hBlob*<br/>
Odkaz na proměnnou, kde je uložena vlastnost (obvykle členproměnné vaší třídy).

*hBlobVýchozí*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti bude číst nebo zapisovat do proměnné odkazuje *hBlob*, podle potřeby. Tato proměnná by měla být `PX_Blob` inicializována na hodnotu NULL před prvním voláním (obvykle to lze provést v konstruktoru ovládacího prvku). Pokud je zadán *hBlobDefault,* bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces inicializace nebo serializace ovládacího prvku.

Úchyty *hBlob* a *hBlobDefault* odkazují na blok paměti, který obsahuje následující:

- DWORD, který obsahuje délku binárních dat, která následují, v bajtech, za nimiž bezprostředně následuje

- Blok paměti obsahující skutečná binární data.

Všimněte `PX_Blob` si, že bude přidělovat paměť, pomocí rozhraní API Windows [GlobalAlloc,](/windows/win32/api/winbase/nf-winbase-globalalloc) při načítání vlastností typu BLOB. Jste zodpovědní za uvolnění této paměti. Proto destruktor ovládacího prvku by měl volat [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) na všechny popisovače typu BLOB uvolnit paměť přidělenou ovládacímu prvku.

## <a name="px_bool"></a><a name="px_bool"></a>PX_Bool

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost typu BOOL.

```cpp
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
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*bHodnota*<br/>
Odkaz na proměnnou, kde je uložena vlastnost (obvykle členproměnné vaší třídy).

*bVýchozí*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti bude číst nebo zapisovat do proměnné odkazuje *bValue*, podle potřeby. Pokud je *zadáno bDefault,* bude použito jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu proces serializace ovládacího prvku selže.

## <a name="px_color"></a><a name="px_color"></a>PX_Color

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost typu OLE_COLOR.

```cpp
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
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*clrValue*<br/>
Odkaz na proměnnou, kde je uložena vlastnost (obvykle členproměnné vaší třídy).

*clrVýchozí*<br/>
Výchozí hodnota vlastnosti, jak je definována vývojářem ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti bude číst nebo zapisovat do proměnné odkazuje *clrValue*, podle potřeby. Pokud je *zadána hodnota clrDefault,* bude použita jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu proces serializace ovládacího prvku selže.

## <a name="px_currency"></a><a name="px_currency"></a>PX_Currency

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost typu **měny**.

```cpp
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
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*cyValue*<br/>
Odkaz na proměnnou, kde je uložena vlastnost (obvykle členproměnné vaší třídy).

*cyDefault*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti bude číst nebo zapisovat do proměnné, na kterou odkazuje *cyValue*, podle potřeby. Pokud *cyDefault* je zadán, bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu proces serializace ovládacího prvku selže.

## <a name="px_datapath"></a><a name="px_datapath"></a>PX_DataPath

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost datové cesty typu [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).

```cpp
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
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*vlastnost dataPathProperty*<br/>
Odkaz na proměnnou, kde je uložena vlastnost (obvykle členproměnné vaší třídy).

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Vlastnosti datové cesty implementují vlastnosti asynchronního ovládacího prvku. Hodnota vlastnosti bude číst nebo zapisovat do proměnné odkazované *dataPathProperty*podle potřeby.

## <a name="px_double"></a><a name="px_double"></a>PX_Double

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost typu **double**.

```cpp
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
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*doubleValue*<br/>
Odkaz na proměnnou, kde je uložena vlastnost (obvykle členproměnné vaší třídy).

*doubleDefault*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je číst nebo zapisovat do proměnné odkazuje *doubleValue*, podle potřeby. Pokud je *zadándoubleDefault,* bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu proces serializace ovládacího prvku selže.

## <a name="px_font"></a><a name="px_font"></a>PX_Font

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost písma typu.

```cpp
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*Písma*<br/>
Odkaz na `CFontHolder` objekt, který obsahuje vlastnost font.

*pFontDesc*<br/>
Ukazatel na `FONTDESC` strukturu obsahující hodnoty, které mají být používány při inicializaci výchozího stavu vlastnosti font, v případě, kdy je hodnota null *pFontDispAmbient.*

*pFontDispAmbient*<br/>
Ukazatel na `IFontDisp` rozhraní písma, které má být používáno při inicializaci výchozího stavu vlastnosti písma.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je číst nebo `font`zapisovat do , `CFontHolder` odkaz, v případě potřeby. Pokud *jsou zadány pFontDesc* a *pFontDispAmbient,* v případě potřeby se používají k inicializaci výchozí hodnoty vlastnosti. Tyto hodnoty se používají, pokud z nějakého důvodu proces serializace ovládacího prvku selže. Obvykle předáte HODNOTU NULL pro *pFontDesc* a hodnotu okolí vrácenou `COleControl::AmbientFont` pro *pFontDispAmbient*. Všimněte si, že `COleControl::AmbientFont` objekt písma vrácený `IFontDisp::Release` musí být uvolněnvolání členské funkce.

## <a name="px_float"></a><a name="px_float"></a>PX_Float

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost typu **float**.

```cpp
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
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*floatValue*<br/>
Odkaz na proměnnou, kde je uložena vlastnost (obvykle členproměnné vaší třídy).

*floatDefault*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je číst nebo zapisovat do proměnné odkazuje *floatValue*, podle potřeby. Pokud je *zadána hodnota floatDefault,* bude použita jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu proces serializace ovládacího prvku selže.

## <a name="px_iunknown"></a><a name="px_iunknown"></a>PX_IUnknown

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost reprezentovanou objektem s rozhraním `IUnknown`-derived.

```cpp
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*Punk*<br/>
Odkaz na proměnnou obsahující rozhraní objektu, který představuje hodnotu vlastnosti.

*Iid*<br/>
ID rozhraní označující, které rozhraní objektu vlastnosti je používán ovládacíprvek.

*pUnkVýchozí*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je číst nebo zapisovat do proměnné odkazuje *pUnk*, podle potřeby. Pokud je *zadánpUnkDefault,* bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu proces serializace ovládacího prvku selže.

## <a name="px_long"></a><a name="px_long"></a>PX_Long

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost typu **long**.

```cpp
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
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*lHodnota*<br/>
Odkaz na proměnnou, kde je uložena vlastnost (obvykle členproměnné vaší třídy).

*lVýchozí hodnota*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je číst nebo zapisovat do proměnné odkazuje *lValue*, podle potřeby. Pokud je *zadáno lDefault,* bude použito jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu proces serializace ovládacího prvku selže.

## <a name="px_picture"></a><a name="px_picture"></a>PX_Picture

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost obrázku ovládacího prvku.

```cpp
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
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*Pict*<br/>
Odkaz na [CPictureHolder](../../mfc/reference/cpictureholder-class.md) objektu, kde je uložena vlastnost (obvykle členské proměnné vaší třídy).

*pictDefault*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je čtena nebo zapsána do proměnné, na kterou odkazuje *obrázek*, podle potřeby. Pokud je zadán a zadán *parametr pictDefault,* bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu proces serializace ovládacího prvku selže.

## <a name="px_short"></a><a name="px_short"></a>PX_Short

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost typu **krátké**.

```cpp
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
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*sHodnota*<br/>
Odkaz na proměnnou, kde je uložena vlastnost (obvykle členproměnné vaší třídy).

*sVýchozí hodnota*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je číst nebo zapisovat do proměnné odkazuje *sValue*, podle potřeby. Pokud je *zadánsDefault,* bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu proces serializace ovládacího prvku selže.

## <a name="px_ulong"></a><a name="px_ulong"></a>PX_ULong

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost typu **ULONG**.

```cpp
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
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*ulHodnota*<br/>
Odkaz na proměnnou, kde je uložena vlastnost (obvykle členproměnné vaší třídy).

*ulVýchozí*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je přečtena nebo zapsána do proměnné, na kterou odkazuje *ulValue*, podle potřeby. Pokud je *zadána hodnota ulDefault,* bude použita jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu proces serializace ovládacího prvku selže.

## <a name="px_ushort"></a><a name="px_ushort"></a>PX_UShort

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost typu **nepodepsané krátké**.

```cpp
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
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*usHodnota*<br/>
Odkaz na proměnnou, kde je uložena vlastnost (obvykle členproměnné vaší třídy).

*usVýchozí*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je číst nebo zapisovat do proměnné, na kterou odkazuje *usValue*, podle potřeby. Pokud je *zadáno usDefault,* bude použito jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu proces serializace ovládacího prvku selže.

## <a name="pxstring"></a><a name="px_string"></a>PXstring

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku serializovat nebo inicializovat vlastnost řetězce znaků.

```cpp
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
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*pszPropName*<br/>
Název nemovitosti, která je vyměňována.

*strValue*<br/>
Odkaz na proměnnou, kde je uložena vlastnost (obvykle členproměnné vaší třídy).

*strDefault*<br/>
Výchozí hodnota vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je číst nebo zapisovat do proměnné odkazuje *strValue*, podle potřeby. Pokud *strDefault* je zadán, bude použit jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu proces serializace ovládacího prvku selže.

## <a name="px_vbxfontconvert"></a><a name="px_vbxfontconvert"></a>PX_VBXFontConvert

Volání této funkce v `DoPropExchange` rámci členské funkce ovládacího prvku k inicializaci vlastnosti písma převodem vlastností souvisejících s písmem ovládacího prvku VBX.

```cpp
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Ukazatel na [cPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán `DoPropExchange`jako parametr).

*Písma*<br/>
Vlastnost písma ovládacího prvku OLE, který bude obsahovat převedené vlastnosti související s písmem VBX.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla výměna úspěšná; 0 v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být používána pouze ovládacím prvkem OLE, který je navržen jako přímá náhrada ovládacího prvku VBX. Když vývojové prostředí jazyka převede formulář obsahující ovládací prvek VBX použít odpovídající náhradní ovládací prvek `IDataObject::SetData` OLE, bude volat funkci ovládacího prvku, předávání v sadě vlastností, která obsahuje data vlastností ovládacího prvku VBX. Tato operace zase způsobí, že `DoPropExchange` funkce ovládacího prvku, které mají být vyvolány. `DoPropExchange`můžete `PX_VBXFontConvert` volat převést vlastnosti ovládacího prvku VBX (například "FontName", "FontSize" a tak dále) do odpovídající součásti vlastnosti písma ovládacího prvku OLE.

`PX_VBXFontConvert`by měla být volána pouze v případě, že ovládací prvek je skutečně převáděn z aplikace formuláře VBX. Příklad:

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
