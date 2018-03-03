---
title: "Trvalost ovládacích prvků OLE | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3452bccd4bdf94c84e4549f99829aaa087e1803b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="persistence-of-ole-controls"></a>Trvalost ovládacích prvků OLE
Jedna možnost ovládací prvky OLE je vlastnost trvalost (nebo serializace), což umožňuje ovládacího prvku OLE pro čtení nebo zápis hodnot vlastností do a ze souboru nebo datový proud. Kontejner aplikace můžete použít serializace k ukládání hodnot vlastností ovládacího prvku i po aplikaci byl zničen ovládacího prvku. Hodnoty vlastností ovládacího prvku OLE lze poté číst ze souboru nebo datový proud při novou instanci ovládacího prvku se vytvoří na později.  
  
### <a name="persistence-of-ole-controls"></a>Trvalost ovládacích prvků OLE  
  
|||  
|-|-|  
|[Px_blob –](#px_blob)|Výměny řídicí vlastnost, která ukládá data binární rozsáhlý objekt (binární rozsáhlý OBJEKT).|  
|[Px_bool –](#px_bool)|Výměny vlastnost ovládacího prvku typu **BOOL**.|  
|[Px_color –](#px_color)|Výměny vlastnosti color ovládacího prvku.|  
|[Px_currency –](#px_currency)|Výměny vlastnost ovládacího prvku typu **CY**.|  
|[Px_datapath –](#px_datapath)|Výměny vlastnost ovládacího prvku typu `CDataPathProperty`.|  
|[Px_double –](#px_double)|Výměny vlastnost ovládacího prvku typu **dvojité**.|  
|[Px_font –](#px_font)|Výměny písma vlastností ovládacího prvku.|  
|[Px_float –](#px_float)|Výměny vlastnost ovládacího prvku typu **float**.|  
|[Px_iunknown –](#px_iunknown)|Výměny řízení vlastnost nedefinované typu.|  
|[Px_long –](#px_long)|Výměny vlastnost ovládacího prvku typu **dlouho**.|  
|[Px_picture –](#px_picture)|Výměny vlastnosti Obrázek ovládacího prvku.|  
|[Px_short –](#px_short)|Výměny vlastnost ovládacího prvku typu **krátké**.|  
|[Px_ulong –](#px_ulong)|Výměny vlastnost ovládacího prvku typu **ULONG**.|  
|[Px_ushort –](#px_ushort)|Výměny vlastnost ovládacího prvku typu **USHORT**.|  
|[PXstring](#px_string)|Výměny vlastnost řízení řetězec znaků.|  
|[Px_vbxfontconvert –](#px_vbxfontconvert)|Vlastnosti související s písma ovládacího prvku VBX výměny do OLE řízení font – vlastnost.|  
  
 Kromě toho `AfxOleTypeMatchGuid` globální funkce je k dispozici pro testování shody mezi `TYPEDESC` a zadaný identifikátor GUID.  
  
##  <a name="px_blob"></a>Px_blob –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnost, která ukládá data binární rozsáhlý objekt (binární rozsáhlý OBJEKT).  
  
```  
 
BOOL  
PX_Blob(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    HGLOBAL& 
hBlob  ,  
    HGLOBAL 
hBlobDefault  
= NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `hBlob`  
 Odkaz na proměnnou, kde je uložen vlastnost (obvykle členské proměnné vaší třídy).  
  
 `hBlobDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti bude číst z nebo zapisovat do proměnné odkazuje `hBlob`podle potřeby. Tato proměnná by měla být inicializována tak, aby **NULL** před voláním původně `PX_Blob` první (obvykle to lze provést v konstruktoru ovládacího prvku). Pokud `hBlobDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces inicializace nebo serializace ovládacího prvku.  
  
 Obslužné rutiny pro zpracování `hBlob` a `hBlobDefault` odkazovat na blok paměti, který obsahuje následující:  
  
-   A `DWORD` obsahující délka v bajtech, binární data, která následuje, a potom okamžitě nástrojem  
  
-   Blok paměť obsahující skutečná binární data.  
  
 Všimněte si, že `PX_Blob` se přidělit paměť, pomocí Windows [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) rozhraní API, při načítání vlastností typu BLOB. Jste zodpovědní za uvolnění tuto paměť. Proto by měly volat – destruktor ovládacího prvku [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) na žádnou vlastnost typu BLOB až popisovače uvolnit všechny paměť přidělená pro vlastní ovládací prvek.  
  
##  <a name="px_bool"></a>Px_bool –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnost typu **BOOL**.  
  
```  
 
BOOL  
PX_Bool(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    BOOL& bValue);

BOOL  
PX_Bool(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    BOOL& 
bValue  ,  
    BOOL bDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `bValue`  
 Odkaz na proměnnou, kde je uložen vlastnost (obvykle členské proměnné vaší třídy).  
  
 `bDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti bude číst z nebo zapisovat do proměnné odkazuje `bValue`podle potřeby. Pokud `bDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces serializace ovládacího prvku.  
  
##  <a name="px_color"></a>Px_color –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnost typu **OLE_COLOR**.  
  
```  
 
BOOL PX_Color(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    OLE_COLOR& 
clrValue  ,  
    OLE_COLOR 
clrDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `clrValue`  
 Odkaz na proměnnou, kde je uložen vlastnost (obvykle členské proměnné vaší třídy).  
  
 `clrDefault`  
 Výchozí hodnota pro vlastnost, podle definice vývojář ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti bude číst z nebo zapisovat do proměnné odkazuje `clrValue`podle potřeby. Pokud `clrDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces serializace ovládacího prvku.  
  
##  <a name="px_currency"></a>Px_currency –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnost typu **Měna**.  
  
```  
 
BOOL  
PX_Currency(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CY& cyValue);

BOOL  
PX_Currency(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CY& 
cyValue  ,  
    CY cyDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `cyValue`  
 Odkaz na proměnnou, kde je uložen vlastnost (obvykle členské proměnné vaší třídy).  
  
 `cyDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti bude číst z nebo zapisovat do proměnné odkazuje `cyValue`podle potřeby. Pokud `cyDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces serializace ovládacího prvku.  
  
##  <a name="px_datapath"></a>Px_datapath –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat data cesta vlastnost typu [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).  
  
```  
 
BOOL  
PX_DataPath(
    CPropExchange* 
pPX,  
    LPCTSTR 
pszPropName,  
    CDataPathProperty& dataPathProperty);

BOOL  
PX_DataPath(
    CPropExchange* 
pPX,  
    CDataPathProperty& dataPathProperty);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `dataPathProperty`  
 Odkaz na proměnnou, kde je uložen vlastnost (obvykle členské proměnné vaší třídy).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Cesta vlastnosti dat implementovat asynchronní řízení vlastnosti. Hodnota vlastnosti bude číst z nebo zapisovat do proměnné odkazuje `dataPathProperty`podle potřeby.  
  
##  <a name="px_double"></a>Px_double –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnost typu **dvojité**.  
  
```  
 
BOOL  
PX_Double(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    double& doubleValue);

BOOL  
PX_Double(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    double& 
doubleValue  ,  
    double doubleDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `doubleValue`  
 Odkaz na proměnnou, kde je uložen vlastnost (obvykle členské proměnné vaší třídy).  
  
 `doubleDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst z nebo zapisovat do proměnné odkazuje `doubleValue`podle potřeby. Pokud `doubleDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces serializace ovládacího prvku.  
  
##  <a name="px_font"></a>Px_font –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnost typ písma.  
  
```  
 
BOOL  
PX_Font(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CFontHolder& 
font  ,  
    const 
FONTDESC  
FAR* 
pFontDesc  
= 
NULL,  
    LPFONTDISP 
pFontDispAmbient  
= NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `font`  
 Odkaz na `CFontHolder` objekt, který obsahuje vlastnost písma.  
  
 `pFontDesc`  
 Ukazatel **FONTDESC** struktura obsahující hodnoty, které mají použít při inicializaci výchozí stav vlastnosti písma, v případě, kde `pFontDispAmbient` je **NULL**.  
  
 `pFontDispAmbient`  
 Ukazatel **IFontDisp** rozhraní písma pro použití v inicializaci výchozí stav vlastnost písma.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst z nebo zapisovat do `font`, `CFontHolder` odkazovat, když je potřeba. Pokud `pFontDesc` a `pFontDispAmbient` jsou nastaveny, používají se pro inicializaci vlastnosti na výchozí hodnotu, v případě potřeby. Tyto hodnoty se použijí, pokud z nějakého důvodu selže proces serializace ovládacího prvku. Obvykle je předat **NULL** pro `pFontDesc` a vedlejším hodnoty vrácené `COleControl::AmbientFont` pro `pFontDispAmbient`. Všimněte si, že vrácený objekt písma `COleControl::AmbientFont` musí být vydán volání **IFontDisp::Release** – členská funkce.  
  
##  <a name="px_float"></a>Px_float –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnost typu **float**.  
  
```  
 
BOOL  
PX_Float(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    float& floatValue);

BOOL  
PX_Float(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    float& 
floatValue  ,  
    float floatDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `floatValue`  
 Odkaz na proměnnou, kde je uložen vlastnost (obvykle členské proměnné vaší třídy).  
  
 `floatDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst z nebo zapisovat do proměnné odkazuje `floatValue`podle potřeby. Pokud `floatDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces serializace ovládacího prvku.  
  
##  <a name="px_iunknown"></a>Px_iunknown –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnost reprezentované tak, že k objektu **IUnknown**-odvozené rozhraní.  
  
```  
 
BOOL  
PX_IUnknown(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    LPUNKNOWN& 
pUnk  ,  
    REFIID 
iid  ,  
    LPUNKNOWN 
pUnkDefault  
= NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 *pUnk*  
 Odkaz na proměnnou obsahující rozhraní objektu, který představuje hodnotu vlastnosti.  
  
 `iid`  
 ID rozhraní označující, které rozhraní vlastnost objektu je používán ovládacího prvku.  
  
 `pUnkDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst z nebo zapisovat do proměnné odkazuje *pUnk*podle potřeby. Pokud `pUnkDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces serializace ovládacího prvku.  
  
##  <a name="px_long"></a>Px_long –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnost typu **dlouho**.  
  
```  
 
BOOL  
PX_Long(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    long& lValue);

BOOL  
PX_Long(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    long& 
lValue  ,  
    long lDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `lValue`  
 Odkaz na proměnnou, kde je uložen vlastnost (obvykle členské proměnné vaší třídy).  
  
 `lDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst z nebo zapisovat do proměnné odkazuje `lValue`podle potřeby. Pokud `lDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces serializace ovládacího prvku.  
  
##  <a name="px_picture"></a>Px_picture –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnosti Obrázek ovládacího prvku.  
  
```  
 
BOOL  
PX_Picture(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CPictureHolder& pict);

BOOL  
PX_Picture(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CPictureHolder& 
pict  ,  
    CPictureHolder& pictDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `pict`  
 Odkaz na [CPictureHolder](../../mfc/reference/cpictureholder-class.md) objekt se uloží vlastnost (obvykle členské proměnné vaší třídy).  
  
 `pictDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst z nebo zapisovat do proměnné odkazuje `pict`podle potřeby. Pokud `pictDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces serializace ovládacího prvku.  
  
##  <a name="px_short"></a>Px_short –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnost typu **krátké**.  
  
```  
 
BOOL  
PX_Short(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    short& sValue);

BOOL  
PX_Short(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    short& 
sValue  ,  
    short sDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `sValue`  
 Odkaz na proměnnou, kde je uložen vlastnost (obvykle členské proměnné vaší třídy).  
  
 `sDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst z nebo zapisovat do proměnné odkazuje `sValue`podle potřeby. Pokud `sDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces serializace ovládacího prvku.  
  
##  <a name="px_ulong"></a>Px_ulong –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnost typu **ULONG**.  
  
```  
 
BOOL  
PX_ULong(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    ULONG& ulValue);

BOOL  
PX_ULong(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    ULONG& 
ulValue  ,  
    long ulDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `ulValue`  
 Odkaz na proměnnou, kde je uložen vlastnost (obvykle členské proměnné vaší třídy).  
  
 `ulDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst z nebo zapisovat do proměnné odkazuje `ulValue`podle potřeby. Pokud `ulDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces serializace ovládacího prvku.  
  
##  <a name="px_ushort"></a>Px_ushort –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k serializaci nebo inicializovat vlastnost typu `unsigned` **krátké**.  
  
```  
 
BOOL  
PX_UShort(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    USHORT& usValue);

BOOL  
PX_UShort(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    USHORT& 
usValue  ,  
    USHORT usDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 *usValue*  
 Odkaz na proměnnou, kde je uložen vlastnost (obvykle členské proměnné vaší třídy).  
  
 *usDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst z nebo zapisovat do proměnné odkazuje *usValue*podle potřeby. Pokud *usDefault* je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces serializace ovládacího prvku.  
  
##  <a name="px_string"></a>PXstring  
 Volání této funkce v rámci ovládacího prvku **dopropexchange –** – členská funkce k serializaci nebo inicializovat ve vlastnosti string. znak.  
  
```  
 
BOOL  
PXstring(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CString& strValue);

BOOL  
PXstring(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CString& 
strValue  ,  
    CString strDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `pszPropName`  
 Název vlastnosti během výměny.  
  
 `strValue`  
 Odkaz na proměnnou, kde je uložen vlastnost (obvykle členské proměnné vaší třídy).  
  
 `strDefault`  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst z nebo zapisovat do proměnné odkazuje `strValue`podle potřeby. Pokud `strDefault` je zadán, použije se jako výchozí hodnotu vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces serializace ovládacího prvku.  
  
##  <a name="px_vbxfontconvert"></a>Px_vbxfontconvert –  
 Volání této funkce v rámci ovládacího prvku `DoPropExchange` – členská funkce k chybě při inicializaci vlastnost písma převedením vlastností souvisejících s písma VBX ovládacího prvku.  
  
```  
 
BOOL  
PX_VBXFontConvert(
    CPropExchange* 
pPX  ,  
    CFontHolder& font);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Ukazatel [CPropExchange](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předány jako parametr, který se `DoPropExchange`).  
  
 `font`  
 Vlastnost font OLE ovládací prvek, který bude obsahovat převedený VBX vlastnosti související s písma.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud exchange byla úspěšná. 0, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce má být používána pouze ovládací prvek OLE, který slouží k přímé nahrazení VBX ovládacího prvku. Když vývojového prostředí jazyka Visual Basic převede obsahující ovládacího prvku VBX používat odpovídající nahrazení OLE ovládacího prvku formuláře, zavolá ovládacího prvku **IDataObject::SetData** funkce, předávání vlastnost nastavena, který obsahuje data vlastnost VBX ovládacího prvku. Tuto operaci, způsobí, že ovládacího prvku `DoPropExchange` funkce, která má být volána. `DoPropExchange`můžete volat `PX_VBXFontConvert` převést vlastnosti související s písma VBX ovládacího prvku (například "název písma," "Velikost písma," a tak dále) do odpovídající součástí prvku OLE font – vlastnost.  
  
 `PX_VBXFontConvert`by měla být volána pouze při řízení je ve skutečnosti převáděn z formátu aplikace VBX. Příklad:  
  
 [!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]  
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
