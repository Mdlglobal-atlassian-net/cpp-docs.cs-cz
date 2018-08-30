---
title: Cmfcribbonfontcombobox – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a53dd239d2c6cdba77f977cc94642828c5e91b7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216471"
---
# <a name="cmfcribbonfontcombobox-class"></a>Cmfcribbonfontcombobox – třída
Implementuje pole se seznamem, který obsahuje seznam písem. Pole se seznamem umístíte na panel pásu karet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destruktor.|  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Vytvoří a inicializuje `CMFCRibbonFontComboBox` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Naplní pásu karet pole se seznamem písma s písmy zadaný font typu, znaková sada a rozteč a rodiny.|  
|`CMFCRibbonFontComboBox::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|  
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Vrátí zadanou znakovou sadu.|  
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||  
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Vrátí typy písem pro zobrazení v okně se seznamem. Platné možnosti jsou DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE nebo jakékoli bitová kombinace.|  
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Vrátí rozteč a rodiny písem, které se zobrazí v poli se seznamem.|  
|`CMFCRibbonFontComboBox::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|  
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Naplní pásu karet pole se seznamem písma s písmy z dříve zadané písmo, znakové sady a rozteč a rodiny.|  
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Vybere písmo zadaný v poli se seznamem.|  
  
## <a name="remarks"></a>Poznámky  
 Po vytvoření `CMFCRibbonFontComboBox` objektu, přidejte na panel pásu karet pomocí volání [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [Cmfcribbonbutton –](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [Cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [Cmfcribboncombobox –](../../mfc/reference/cmfcribboncombobox-class.md)  
  
 [Cmfcribbonfontcombobox –](../../mfc/reference/cmfcribbonfontcombobox-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonComboBox.h  
  
##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts  
 Naplní pole se seznamem na pásu karet pomocí písem.  
  
```  
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nFontType*  
 Určuje písmo typ písma pro přidání.  
  
 [in] *nCharSet*  
 Určuje znakovou sadu písma pro přidání.  
  
 [in] *nPitchAndFamily*  
 Určuje rozteč a rodiny písem pro přidání.  
  
##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox  
 Vytvoří a inicializuje [cmfcribbonfontcombobox –](../../mfc/reference/cmfcribbonfontcombobox-class.md) objektu.  
  
```  
CMFCRibbonFontComboBox(
    UINT nID,  
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH,  
    int nWidth = -1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nID*  
 ID příkazu, který se spustí, když uživatel vybere položku v poli se seznamem příkazu.  
  
 [in] *nFontType*  
 Určuje, které Písmo typy mají zobrazit v poli se seznamem. Platné možnosti jsou DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE nebo jakékoli bitová kombinace.  
  
 [in] *nCharSet*  
 Filtry v poli se seznamem na ty, které patří do zadanou znakovou sadu písma...  
  
 [in] *nPitchAndFamily*  
 Určuje, rozteč a rodiny písem, které se zobrazí v poli se seznamem.  
  
 [in] *nWidth*  
 Určuje šířku v pixelech, pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o možných *nFontType* hodnoty parametrů naleznete v tématu [EnumFontFamProc](https://msdn.microsoft.com/library/windows/desktop/dd162621) v dokumentaci Windows SDK.  
  
 Další informace o platné znakových sad, které je možné přiřadit *nCharSet*a platné hodnoty, které je možné přiřadit *nPitchAndFamily*, naleznete v tématu [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) v Dokumentace k sadě Windows SDK.  
  
##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc  
 Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts  
 Naplní pole se seznamem na pásu karet pomocí písem z dříve zadané písmo, znakové sady a rozteč a rodiny.  
  
```  
void RebuildFonts();
```  
  
### <a name="remarks"></a>Poznámky  
 Můžete zadat typ písma, znakové sady a rozteč a rodiny písem, které chcete zahrnout do pole se seznamem písma pásu karet pole [konstruktor](#cmfcribbonfontcombobox) pro tuto třídu nebo voláním [CMFCRibbonFontComboBox::BuildFonts](#buildfonts).  
  
##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont  
 Vybere písmo zadaný v poli se seznamem.  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BOOL bExact = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 "lpszName *  
 Určuje název písma k výběru.  
  
 *nCharSet*  
 Určuje znakovou sadu vybraného písma.  
  
 *bExact*  
 TRUE, pokud chcete určit, že při výběru písma; musí odpovídat znakové sady FALSE, pokud chcete určit, že při výběru písma můžete ignorovat znakovou sadu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud zadaný font byl nalezen a zaškrtnuto. jinak, nula.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet  
 Vrátí zadanou znakovou sadu.  
  
```  
BYTE GetCharSet() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Znakové sady (viz LOGFONT v dokumentaci Windows SDK).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType  
 Vrátí typy písem pro zobrazení v okně se seznamem. Platné možnosti jsou DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE nebo jakékoli bitová kombinace.  
  
```  
int GetFontType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Typy písem (viz EnumFontFamProc v dokumentaci Windows SDK).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily  
 Vrátí rozteč a rodiny písem, které se zobrazí v poli se seznamem.  
  
```  
BYTE GetPitchAndFamily() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Rozteč a rodiny (viz LOGFONT v dokumentaci Windows SDK).  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonComboBox – třída](../../mfc/reference/cmfcribboncombobox-class.md)
