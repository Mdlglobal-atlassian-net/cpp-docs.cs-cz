---
title: Trvalost ovládacích prvků OLE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 661735e91084bad45553de71e80a599afd674028
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336823"
---
# <a name="persistence-of-ole-controls"></a>Trvalost ovládacích prvků OLE
Jeden funkční ovládací prvky OLE je vlastnost trvalost (nebo serializace), který umožňuje ovládacího prvku OLE pro čtení nebo zápis hodnot vlastností do a ze souboru nebo datového proudu. Aplikace typu kontejner pro slouží k ukládání hodnot vlastností ovládacího prvku i po aplikace byl zničen ovládacího prvku serializace. Hodnoty vlastností ovládacího prvku OLE pak může číst ze souboru nebo datový proud při novou instanci ovládacího prvku proběhne později.  
  
### <a name="persistence-of-ole-controls"></a>Trvalost ovládacích prvků OLE  
  
|||  
|-|-|  
|[Px_blob –](#px_blob)|Vymění vlastností ovládacího prvku, který ukládá data binárního rozsáhlého objektu (BLOB).|  
|[Px_bool –](#px_bool)|Vymění vlastnosti ovládacího prvku typu **BOOL**.|  
|[Px_color –](#px_color)|Vymění vlastnost barvu ovládacího prvku.|  
|[Px_currency –](#px_currency)|Vymění vlastnosti ovládacího prvku typu **CY**.|  
|[Px_datapath –](#px_datapath)|Vymění vlastnosti ovládacího prvku typu `CDataPathProperty`.|  
|[Px_double –](#px_double)|Vymění vlastnosti ovládacího prvku typu **double**.|  
|[Px_font –](#px_font)|Vymění vlastnosti font ovládacího prvku.|  
|[Px_float –](#px_float)|Vymění vlastnosti ovládacího prvku typu **float**.|  
|[Px_iunknown –](#px_iunknown)|Vymění vlastnosti ovládacího prvku nedefinovaného typu.|  
|[Px_long –](#px_long)|Vymění vlastnosti ovládacího prvku typu **dlouhé**.|  
|[Px_picture –](#px_picture)|Vymění vlastnost obrázek ovládacího prvku.|  
|[Px_short –](#px_short)|Vymění vlastnosti ovládacího prvku typu **krátký**.|  
|[Px_ulong –](#px_ulong)|Vymění vlastnosti ovládacího prvku typu **ULONG**.|  
|[Px_ushort –](#px_ushort)|Vymění vlastnosti ovládacího prvku typu **USHORT**.|  
|[PXstring](#px_string)|Vymění vlastností ovládacího prvku řetězec znaků.|  
|[Px_vbxfontconvert –](#px_vbxfontconvert)|Vymění vlastností písma související VBX ovládacího prvku do vlastnosti font ovládacího prvku OLE.|  
  
 Kromě toho `AfxOleTypeMatchGuid` globální funkce je k dispozici pro testování shodují TYPEDESC a daný identifikátor GUID.  
  
##  <a name="px_blob"></a>  Px_blob –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializovat vlastnost, která ukládá data binárního rozsáhlého objektu (BLOB).  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *hBlob*  
 Odkaz na proměnnou, kde je uložen vlastnosti (obvykle proměnné člena vaší třídy).  
  
 *hBlobDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti se číst nebo zapisovat do proměnná odkazuje *hBlob*podle potřeby. Tato proměnná je třeba inicializovat na hodnotu NULL před voláním zpočátku `PX_Blob` poprvé (obvykle to můžete udělat v konstruktoru ovládacího prvku). Pokud *hBlobDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže proces inicializace nebo serializace ovládacího prvku.  
  
 Úchyty *hBlob* a *hBlobDefault* odkazovat na blok paměti, který obsahuje následující:  
  
-   DWORD, který obsahuje délku v bajtech, binárních dat, který následuje, a potom hned za  
  
-   Blok paměti obsahující skutečná binární data.  
  
 Všimněte si, že `PX_Blob` přidělí paměť v Windows [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) rozhraní API, při načítání vlastností typ objektu BLOB. Zodpovídáte za uvolnění tuto paměť. Proto by měly volat destruktor ovládacího prvku [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) jakékoli vlastnosti typu BLOB až obslužné rutiny pro uvolnění paměti přidělené do ovládacího prvku.  
  
##  <a name="px_bool"></a>  Px_bool –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializovat vlastnost typu BOOL.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *bValue*  
 Odkaz na proměnnou, kde je uložen vlastnosti (obvykle proměnné člena vaší třídy).  
  
 *bDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti se číst nebo zapisovat do proměnná odkazuje *bValue*podle potřeby. Pokud *bDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže procesu serializace ovládacího prvku.  
  
##  <a name="px_color"></a>  Px_color –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` k serializaci nebo inicializovat vlastnost typu OLE_COLOR členskou funkci.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *clrValue*  
 Odkaz na proměnnou, kde je uložen vlastnosti (obvykle proměnné člena vaší třídy).  
  
 *clrDefault*  
 Výchozí hodnota pro vlastnost, jak je definováno vývojářem ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti se číst nebo zapisovat do proměnná odkazuje *clrValue*podle potřeby. Pokud *clrDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže procesu serializace ovládacího prvku.  
  
##  <a name="px_currency"></a>  Px_currency –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializovat vlastnost typu **měny**.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *cyValue*  
 Odkaz na proměnnou, kde je uložen vlastnosti (obvykle proměnné člena vaší třídy).  
  
 *cyDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti se číst nebo zapisovat do proměnná odkazuje *cyValue*podle potřeby. Pokud *cyDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže procesu serializace ovládacího prvku.  
  
##  <a name="px_datapath"></a>  Px_datapath –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializaci data cesty vlastnost typu [cdatapathproperty –](../../mfc/reference/cdatapathproperty-class.md).  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *dataPathProperty*  
 Odkaz na proměnnou, kde je uložen vlastnosti (obvykle proměnné člena vaší třídy).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Vlastnosti cesty dat implementovat asynchronní ovládacího prvku vlastnosti. Hodnota vlastnosti se číst nebo zapisovat do proměnná odkazuje *dataPathProperty*podle potřeby.  
  
##  <a name="px_double"></a>  Px_double –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializovat vlastnost typu **double**.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *doubleValue*  
 Odkaz na proměnnou, kde je uložen vlastnosti (obvykle proměnné člena vaší třídy).  
  
 *doubleDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst nebo do proměnné odkazuje *doubleValue*podle potřeby. Pokud *doubleDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže procesu serializace ovládacího prvku.  
  
##  <a name="px_font"></a>  Px_font –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializovat vlastnost typ písma.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *Písma*  
 Odkaz na `CFontHolder` objekt, který obsahuje vlastnosti font.  
  
 *pFontDesc*  
 Ukazatel `FONTDESC` struktury obsahující hodnoty pro použití při inicializaci výchozí stav vlastností písma, v případě, kde *pFontDispAmbient* má hodnotu NULL.  
  
 *pFontDispAmbient*  
 Ukazatel `IFontDisp` rozhraní písma pro použití v inicializaci výchozí stav vlastností písma.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst nebo zapisovat do `font`, `CFontHolder` odkazovat, pokud je to vhodné. Pokud *pFontDesc* a *pFontDispAmbient* nejsou zadány, používají se pro inicializaci výchozí hodnotu vlastnosti, pokud je nepotřebujete. Tyto hodnoty se použijí, pokud z nějakého důvodu selže procesu serializace ovládacího prvku. Obvykle předat hodnotu NULL pro *pFontDesc* a okolí hodnoty vrácené `COleControl::AmbientFont` pro *pFontDispAmbient*. Všimněte si, že vrácený objekt písmo `COleControl::AmbientFont` musí uvolnit voláním `IFontDisp::Release` členskou funkci.  
  
##  <a name="px_float"></a>  Px_float –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializovat vlastnost typu **float**.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *floatValue*  
 Odkaz na proměnnou, kde je uložen vlastnosti (obvykle proměnné člena vaší třídy).  
  
 *floatDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst nebo do proměnné odkazuje *floatValue*podle potřeby. Pokud *floatDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže procesu serializace ovládacího prvku.  
  
##  <a name="px_iunknown"></a>  Px_iunknown –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializace je vlastnost reprezentována tím, že objektu `IUnknown`-odvozené rozhraní.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *pUnk*  
 Odkaz na proměnnou obsahující rozhraní objektu, který představuje hodnotu vlastnosti.  
  
 *identifikátor IID*  
 ID rozhraní určující, které rozhraní objekt vlastnost se používá ovládacím prvkem.  
  
 *pUnkDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst nebo do proměnné odkazuje *pUnk*podle potřeby. Pokud *pUnkDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže procesu serializace ovládacího prvku.  
  
##  <a name="px_long"></a>  Px_long –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializovat vlastnost typu **dlouhé**.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *l-hodnoty.*  
 Odkaz na proměnnou, kde je uložen vlastnosti (obvykle proměnné člena vaší třídy).  
  
 *lDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst nebo do proměnné odkazuje *l-hodnoty*podle potřeby. Pokud *lDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže procesu serializace ovládacího prvku.  
  
##  <a name="px_picture"></a>  Px_picture –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializovat vlastnost obrázek ovládacího prvku.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *PICT*  
 Odkaz [cpictureholder –](../../mfc/reference/cpictureholder-class.md) objekt vlastnost se mají ukládat (obvykle proměnné člena vaší třídy).  
  
 *pictDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst nebo do proměnné odkazuje *pict*podle potřeby. Pokud *pictDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže procesu serializace ovládacího prvku.  
  
##  <a name="px_short"></a>  Px_short –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializovat vlastnost typu **krátký**.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *sValue*  
 Odkaz na proměnnou, kde je uložen vlastnosti (obvykle proměnné člena vaší třídy).  
  
 *sDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst nebo do proměnné odkazuje *sValue*podle potřeby. Pokud *sDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže procesu serializace ovládacího prvku.  
  
##  <a name="px_ulong"></a>  Px_ulong –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializovat vlastnost typu **ULONG**.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *ulValue*  
 Odkaz na proměnnou, kde je uložen vlastnosti (obvykle proměnné člena vaší třídy).  
  
 *ulDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst nebo do proměnné odkazuje *ulValue*podle potřeby. Pokud *ulDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže procesu serializace ovládacího prvku.  
  
##  <a name="px_ushort"></a>  Px_ushort –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializovat vlastnost typu **unsigned short**.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *usValue*  
 Odkaz na proměnnou, kde je uložen vlastnosti (obvykle proměnné člena vaší třídy).  
  
 *usDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst nebo do proměnné odkazuje *usValue*podle potřeby. Pokud *usDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže procesu serializace ovládacího prvku.  
  
##  <a name="px_string"></a>  PXstring  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k serializaci nebo inicializovat vlastnost řetězce znaků.  
  
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
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *strValue*  
 Odkaz na proměnnou, kde je uložen vlastnosti (obvykle proměnné člena vaší třídy).  
  
 *strDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst nebo do proměnné odkazuje *strValue*podle potřeby. Pokud *strDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže procesu serializace ovládacího prvku.  
  
##  <a name="px_vbxfontconvert"></a>  Px_vbxfontconvert –  
 Voláním této funkce v rámci ovládacího prvku `DoPropExchange` členskou funkci k inicializaci vlastnosti písma převedením vlastností písma související VBX ovládacího prvku.  
  
```  
 
BOOL  
PX_VBXFontConvert(
    CPropExchange* 
pPX  ,  
    CFontHolder& font);  
```  
  
### <a name="parameters"></a>Parametry  
 *pPX*  
 Ukazatel [cpropexchange –](../../mfc/reference/cpropexchange-class.md) objektu (obvykle předán jako parametr `DoPropExchange`).  
  
 *Písma*  
 Vlastnosti font ovládacího prvku OLE, který bude obsahovat vlastnosti související s písma převedený VBX.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měly být používány pouze ovládací prvek OLE, který je navržený jako přímé nahrazení pro ovládací prvek VBX. Když vývojové prostředí jazyka Visual Basic převede formulář obsahující ovládací prvek VBX použít odpovídající náhradní ovládací prvek OLE, zavolá ovládacího prvku `IDataObject::SetData` funkci a předává jí sadu vlastností, která obsahuje data vlastnosti ovládacího prvku VBX. Tato operace však způsobí, že ovládacího prvku `DoPropExchange` funkce má být volána. `DoPropExchange` můžete volat `PX_VBXFontConvert` pro převod vlastnosti související se písmo VBX ovládacího prvku (například "název písma," "Velikost písma," a tak dále) do odpovídajících komponent vlastnosti font ovládacího prvku OLE.  
  
 `PX_VBXFontConvert` by měla volat pouze v případě ovládací prvek je ve skutečnosti převáděn z formuláře aplikace VBX. Příklad:  
  
 [!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]  
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
