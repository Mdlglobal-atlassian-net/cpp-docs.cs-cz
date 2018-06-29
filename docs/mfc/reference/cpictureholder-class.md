---
title: Třída CPictureHolder | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
dev_langs:
- C++
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b81a35a696d3d5cdcb22a6f9a66425320b544c2
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079446"
---
# <a name="cpictureholder-class"></a>CPictureHolder – třída
Implementuje vlastnosti obrázku, která umožňuje uživatelům zobrazit obrázek v vlastního ovládacího prvku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPictureHolder  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPictureHolder::CPictureHolder](#cpictureholder)|Vytvoří `CPictureHolder` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPictureHolder::CreateEmpty](#createempty)|Vytvoří prázdnou `CPictureHolder` objektu.|  
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Vytvoří `CPictureHolder` objekt z rastrového obrázku.|  
|[CPictureHolder::CreateFromIcon](#createfromicon)|Vytvoří `CPictureHolder` objekt z ikonu.|  
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|Vytvoří `CPictureHolder` objekt z metasoubory.|  
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Načte řetězec zobrazí v prohlížeči vlastností kontejneru ovládacího prvku.|  
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Vrátí `CPictureHolder` objektu `IDispatch` rozhraní.|  
|[CPictureHolder::GetType](#gettype)|Informuje jestli `CPictureHolder` je objekt rastrový obrázek, metasoubory nebo ikonu.|  
|[CPictureHolder::Render](#render)|Vykreslí na obrázku.|  
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Nastaví `CPictureHolder` objektu `IDispatch` rozhraní.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPictureHolder::m_pPict](#m_ppict)|Ukazatel na objekt obrázku.|  
  
## <a name="remarks"></a>Poznámky  
 `CPictureHolder` nemá základní třídu.  
  
 Pomocí uložených vlastností obrázků můžete určit vývojář rastrového obrázku, ikona nebo metafile pro zobrazení.  
  
 Informace o vytvoření vlastní obrázek – vlastnosti, najdete v článku [MFC – ovládací prvky ActiveX: použití obrázků v ovládacím prvku ActiveX](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CPictureHolder`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h  
  
##  <a name="cpictureholder"></a>  CPictureHolder::CPictureHolder  
 Vytvoří `CPictureHolder` objektu.  
  
```  
CPictureHolder();
```  
  
##  <a name="createempty"></a>  CPictureHolder::CreateEmpty  
 Vytvoří prázdnou `CPictureHolder` objektu a připojí jej k `IPicture` rozhraní.  
  
```  
BOOL CreateEmpty();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekt je úspěšně vytvořen; jinak 0.  
  
##  <a name="createfrombitmap"></a>  CPictureHolder::CreateFromBitmap  
 Rastrový obrázek používá k chybě při inicializaci objektu obrázek ve `CPictureHolder`.  
  
```  
BOOL CreateFromBitmap(
    UINT idResource);

 
BOOL CreateFromBitmap(
    CBitmap* pBitmap,  
    CPalette* pPal = NULL,  
    BOOL bTransferOwnership = TRUE);

 
BOOL CreateFromBitmap(
    HBITMAP hbm,  
    HPALETTE hpal = NULL,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *idResource*  
 ID prostředku bitové mapy prostředků.  
  
 *pBitmap*  
 Ukazatel na [CBitmap](../../mfc/reference/cbitmap-class.md) objektu.  
  
 *pPal*  
 Ukazatel na [CPalette](../../mfc/reference/cpalette-class.md) objektu.  
  
 *bTransferOwnership*  
 Označuje, zda objekt obrázek budou brát rastrového obrázku a paleta objektů.  
  
 *hbm*  
 Zpracování pro bitovou mapu, ze kterého `CPictureHolder` je vytvořen objekt.  
  
 *hpal*  
 Popisovač palety používané k vykreslování bitové mapy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekt je úspěšně vytvořen; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bTransferOwnership* je **TRUE**, volající neměli používat bitmapy nebo vrátí objekt palety žádným způsobem po toto volání. Pokud *bTransferOwnership* je **FALSE**, volající zodpovídá za zajištění, že objekty rastrového obrázku a palety jsou dál platné po dobu jeho existence objektu obrázku.  
  
##  <a name="createfromicon"></a>  CPictureHolder::CreateFromIcon  
 Používá ikonu k chybě při inicializaci objektu obrázek ve `CPictureHolder`.  
  
```  
BOOL CreateFromIcon(
    UINT idResource);

 
BOOL CreateFromIcon(
    HICON hIcon,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *idResource*  
 ID prostředku bitové mapy prostředků.  
  
 *hIcon*  
 Zpracování na ikonu, ze kterého `CPictureHolder` je vytvořen objekt.  
  
 *bTransferOwnership*  
 Určuje, zda objekt obrázku se převzít vlastnictví objektu ikonu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekt je úspěšně vytvořen; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bTransferOwnership* je **TRUE**, volající neměli používat objekt ikonu žádným způsobem po vrátí toto volání. Pokud *bTransferOwnership* je **FALSE**, volající zodpovídá za zajištění, že objekt ikonu zůstane platný po dobu jeho existence objektu obrázku.  
  
##  <a name="createfrommetafile"></a>  CPictureHolder::CreateFromMetafile  
 Používá k inicializaci objektu obrázku v metasoubory `CPictureHolder`.  
  
```  
BOOL CreateFromMetafile(
    HMETAFILE hmf,  
    int xExt,  
    int yExt,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *hmf*  
 Popisovač metafile použít k vytvoření `CPictureHolder` objektu.  
  
 *xExt*  
 X rozsah na obrázku.  
  
 *yExt*  
 Rozsah Y na obrázku.  
  
 *bTransferOwnership*  
 Určuje, zda objekt obrázku se převzít vlastnictví objektu metafile.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekt je úspěšně vytvořen; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bTransferOwnership* je **TRUE**, volající neměli používat objekt metafile žádným způsobem po vrátí toto volání. Pokud *bTransferOwnership* je **FALSE**, volající zodpovídá za zajištění, že objekt metafile zůstane platný po dobu jeho existence objektu obrázku.  
  
##  <a name="getdisplaystring"></a>  CPictureHolder::GetDisplayString  
 Načte řetězec, který se zobrazí v prohlížeči vlastností kontejneru.  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>Parametry  
 *strValue*  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který má obsahovat řetězec zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud řetězec je úspěšně načetl; jinak 0.  
  
##  <a name="getpicturedispatch"></a>  CPictureHolder::GetPictureDispatch  
 Tato funkce vrátí ukazatel `CPictureHolder` objektu `IPictureDisp` rozhraní.  
  
```  
LPPICTUREDISP GetPictureDispatch();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CPictureHolder` objektu `IPictureDisp` rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Volající musí volat **verze** na tento ukazatel po dokončení s ním.  
  
##  <a name="gettype"></a>  CPictureHolder::GetType  
 Určuje, zda je na obrázku rastrového obrázku, metafile nebo ikonu.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která určuje typ obrázku. Možné hodnoty a jejich významy jsou následující:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|**PICTYPE_UNINITIALIZED**|`CPictureHolder` objekt je unititialized.|  
|**PICTYPE_NONE**|`CPictureHolder` objekt je prázdný.|  
|**PICTYPE_BITMAP**|Obrázek je rastrový obrázek.|  
|**PICTYPE_METAFILE**|Obrázek je metasoubory.|  
|**PICTYPE_ICON**|Obrázek je ikonu.|  
  
##  <a name="m_ppict"></a>  CPictureHolder::m_pPict  
 Ukazatel `CPictureHolder` objektu `IPicture` rozhraní.  
  
```  
LPPICTURE m_pPict;  
```  
  
##  <a name="render"></a>  CPictureHolder::Render  
 Vykreslí obrázek v obdélníku odkazuje *rcRender*.  
  
```  
void Render(
    CDC* pDC,  
    const CRect& rcRender,  
    const CRect& rcWBounds);
```  
  
### <a name="parameters"></a>Parametry  
 *primárního řadiče domény*  
 Ukazatel na kontext zobrazení, ve kterém má být vykreslen na obrázku.  
  
 *rcRender*  
 Obdélníku, ve kterém má být vykreslen na obrázku.  
  
 *rcWBounds*  
 Obdélník představující ohraničující obdélník objekt vykreslování obrázku. Pro ovládací prvek, je tento obdélník *rcBounds* parametr předaný přepsání [COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).  
  
##  <a name="setpicturedispatch"></a>  CPictureHolder::SetPictureDispatch  
 Připojí `CPictureHolder` do objektu `IPictureDisp` rozhraní.  
  
```  
void SetPictureDispatch(LPPICTUREDISP pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 *pDisp*  
 Ukazatel na nové `IPictureDisp` rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CFontHolder – třída](../../mfc/reference/cfontholder-class.md)
