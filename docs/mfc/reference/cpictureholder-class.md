---
title: Cpictureholder – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: e00a1da7aeffd07e19b58437bda2c8631af9158a
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852858"
---
# <a name="cpictureholder-class"></a>Cpictureholder – třída
Implementuje vlastnost obrázku, který umožňuje uživateli zobrazit obrázek v ovládacím prvku.  
  
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
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Vytvoří `CPictureHolder` objekt z bitmapy.|  
|[CPictureHolder::CreateFromIcon](#createfromicon)|Vytvoří `CPictureHolder` objekt z ikony.|  
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|Vytvoří `CPictureHolder` objekt z metasouboru.|  
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Načte řetězec zobrazený v prohlížeči vlastností ovládacího prvku kontejneru.|  
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Vrátí `CPictureHolder` objektu `IDispatch` rozhraní.|  
|[CPictureHolder::GetType](#gettype)|Určuje, zda `CPictureHolder` je objekt rastrový obrázek, metasoubor nebo ikonu.|  
|[CPictureHolder::Render](#render)|Vykreslí obrázek.|  
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Nastaví `CPictureHolder` objektu `IDispatch` rozhraní.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPictureHolder::m_pPict](#m_ppict)|Ukazatel na objekt obrázku.|  
  
## <a name="remarks"></a>Poznámky  
 `CPictureHolder` nemá základní třídu.  
  
 Pomocí uložených vlastností obrázků vývojář může určit rastrový obrázek, ikona nebo metasoubor pro zobrazení.  
  
 Informace o vytvoření vlastnosti vlastního obrázku, najdete v článku [knihovny MFC – ovládací prvky ActiveX: použití obrázků v ovládacím prvku ActiveX](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).  
  
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
 Vytvoří prázdnou `CPictureHolder` objektu a připojí ji k `IPicture` rozhraní.  
  
```  
BOOL CreateEmpty();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud objekt je úspěšně vytvořen; jinak 0.  
  
##  <a name="createfrombitmap"></a>  CPictureHolder::CreateFromBitmap  
 Rastrový obrázek používá k inicializaci objektu na obrázku `CPictureHolder`.  
  
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
 ID prostředku prostředku rastrového obrázku.  
  
 *pBitmap*  
 Ukazatel [cbitmap –](../../mfc/reference/cbitmap-class.md) objektu.  
  
 *pPal*  
 Ukazatel [cpalette –](../../mfc/reference/cpalette-class.md) objektu.  
  
 *bTransferOwnership*  
 Označuje, zda objekt obrázek bude trvat vlastnictví objektů rastrového obrázku a palety.  
  
 *hbm*  
 Zpracování do bitmapy, ze kterého `CPictureHolder` je vytvořen objekt.  
  
 *hpal*  
 Popisovač na paletě používané k vykreslování rastrového obrázku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud objekt je úspěšně vytvořen; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bTransferOwnership* má hodnotu TRUE, volající by neměly používat rastrový obrázek nebo vrátí objekt palety nijak po tomto volání. Pokud *bTransferOwnership* má hodnotu FALSE, volající zodpovídá za to, že rastrového obrázku a paleta objektů jsou dál platné po dobu životnosti objektu obrázku.  
  
##  <a name="createfromicon"></a>  CPictureHolder::CreateFromIcon  
 Používá ikony k inicializaci objektu na obrázku `CPictureHolder`.  
  
```  
BOOL CreateFromIcon(
    UINT idResource);

 
BOOL CreateFromIcon(
    HICON hIcon,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *idResource*  
 ID prostředku prostředku rastrového obrázku.  
  
 *hIcon*  
 Zpracování na ikonu, ze kterého `CPictureHolder` je vytvořen objekt.  
  
 *bTransferOwnership*  
 Označuje, zda objekt obrázek bude převzít vlastnictví objektu ikona.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud objekt je úspěšně vytvořen; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bTransferOwnership* má hodnotu TRUE, volající by neměl ikona objektu užívat žádným způsobem po tomto volání vrátí. Pokud *bTransferOwnership* má hodnotu FALSE, volající zodpovídá za to, že zůstane ikona objektu platný po dobu životnosti objektu obrázku.  
  
##  <a name="createfrommetafile"></a>  CPictureHolder::CreateFromMetafile  
 Používá metasoubor k inicializaci objektu na obrázku `CPictureHolder`.  
  
```  
BOOL CreateFromMetafile(
    HMETAFILE hmf,  
    int xExt,  
    int yExt,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *hmf*  
 Zpracování na metasoubor použitý k vytvoření `CPictureHolder` objektu.  
  
 *xExt*  
 X rozsahu obrázku.  
  
 *yExt*  
 Y rozsahu obrázku.  
  
 *bTransferOwnership*  
 Určuje, zda objekt obrázek bude převzít vlastnictví objektu metasouboru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud objekt je úspěšně vytvořen; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bTransferOwnership* má hodnotu TRUE, volající by neměl objekt metasoubor užívat žádným způsobem po tomto volání vrátí. Pokud *bTransferOwnership* má hodnotu FALSE, volající zodpovídá za to, že objekt metasoubor zůstane platný po dobu životnosti objektu obrázku.  
  
##  <a name="getdisplaystring"></a>  CPictureHolder::GetDisplayString  
 Načte řetězec, který se zobrazí v prohlížeči vlastností kontejneru.  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>Parametry  
 *strValue*  
 Odkaz [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který je pro uložení řetězce zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud řetězec je úspěšně načíst. jinak 0.  
  
##  <a name="getpicturedispatch"></a>  CPictureHolder::GetPictureDispatch  
 Tato funkce vrací ukazatel `CPictureHolder` objektu `IPictureDisp` rozhraní.  
  
```  
LPPICTUREDISP GetPictureDispatch();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CPictureHolder` objektu `IPictureDisp` rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Volající musí volat `Release` na tento ukazatel po jeho dokončení.  
  
##  <a name="gettype"></a>  CPictureHolder::GetType  
 Označuje, zda je na obrázku rastrový obrázek, metafile nebo ikonu.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota určující typ obrázku. Možné hodnoty a jejich význam jsou následující:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|PICTYPE_UNINITIALIZED|`CPictureHolder` objekt je unititialized.|  
|PICTYPE_NONE|`CPictureHolder` objekt je prázdný.|  
|PICTYPE_BITMAP|Obrázek je rastrový obrázek.|  
|PICTYPE_METAFILE|Obrázek je metasouboru.|  
|PICTYPE_ICON|Obrázek je ikona.|  
  
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
 *primární řadič domény*  
 Ukazatel na kontextu zobrazení, ve kterém má být vykreslen na obrázku.  
  
 *rcRender*  
 Obdélník, ve kterém má být vykreslen na obrázku.  
  
 *rcWBounds*  
 Obdélník představující ohraničující obdélník objekt vykreslování obrázku. Pro ovládací prvek, je tento obdélník *rcBounds* byl předán parametr přepsání [COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).  
  
##  <a name="setpicturedispatch"></a>  CPictureHolder::SetPictureDispatch  
 Připojuje `CPictureHolder` do objektu `IPictureDisp` rozhraní.  
  
```  
void SetPictureDispatch(LPPICTUREDISP pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 *pDisp*  
 Ukazatel na novou `IPictureDisp` rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CFontHolder – třída](../../mfc/reference/cfontholder-class.md)
