---
title: "Třída CMFCRibbonFontComboBox | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4ba1751a62feb417902c56880289011353b184e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox – třída
Implementuje pole se seznamem, který obsahuje seznam písem. Pole se seznamem umístíte na pásu karet panelu.  
  
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
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Naplní pásu karet pole se seznamem písma s písmy typ zadaný písma, znaková sada a výšky a rodiny.|  
|`CMFCRibbonFontComboBox::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Vrátí zadanou znakovou sadu.|  
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||  
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Vrátí jaké typy písem zobrazíte v pole se seznamem. Platné možnosti jsou DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE nebo jejich bitové kombinace.|  
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Vrátí výšku a rodiny písem, která se zobrazí v seznamu.|  
|`CMFCRibbonFontComboBox::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Naplní pásu karet pole se seznamem písma s písmy typ dříve zadaný písma, znaková sada a výšky a rodiny.|  
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Vybere písmo zadaný v poli se seznamem.|  
  
## <a name="remarks"></a>Poznámky  
 Po vytvoření `CMFCRibbonFontComboBox` objektu, přidejte na panel pásu karet voláním [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
 [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonComboBox.h  
  
##  <a name="buildfonts"></a>CMFCRibbonFontComboBox::BuildFonts  
 Naplní pole se seznamem na pásu karet pomocí písem.  
  
```  
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nFontType`  
 Určuje písmo typ písma, které chcete přidat.  
  
 [v]`nCharSet`  
 Určuje znakovou sadu písma, které chcete přidat.  
  
 [v]`nPitchAndFamily`  
 Určuje výšku a rodiny písem, které chcete přidat.  
  
##  <a name="cmfcribbonfontcombobox"></a>CMFCRibbonFontComboBox::CMFCRibbonFontComboBox  
 Vytvoří a inicializuje [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md) objektu.  
  
```  
CMFCRibbonFontComboBox(
    UINT nID,  
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH,  
    int nWidth = -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nID`  
 ID příkazu, příkazu, který provede, když uživatel vybere položku z pole se seznamem.  
  
 [v]`nFontType`  
 Určuje, které Písmo typy zobrazení v pole se seznamem. Platné možnosti jsou **DEVICE_FONTTYPE**, **RASTER_FONTTYPE**, a **TRUETYPE_FONTTYPE**, nebo jejich bitové kombinace.  
  
 [v]`nCharSet`  
 Filtry písem v poli se seznamem na ty, které patří do sady zadaný znak...  
  
 [v]`nPitchAndFamily`  
 Určuje výšku a rodiny písem, která se zobrazí v seznamu.  
  
 [v]`nWidth`  
 Určuje šířku v pixelech, pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o možných `nFontType` hodnoty parametrů, najdete v části [EnumFontFamProc](http://msdn.microsoft.com/library/windows/desktop/dd162621) v dokumentaci k Windows SDK.  
  
 Další informace o platný znakových sad, které lze přiřadit k `nCharSet`a platné hodnoty, které lze přiřadit k `nPitchAndFamily`, najdete v části [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) v dokumentaci k Windows SDK.  
  
##  <a name="getfontdesc"></a>CMFCRibbonFontComboBox::GetFontDesc  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iIndex`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="rebuildfonts"></a>CMFCRibbonFontComboBox::RebuildFonts  
 Naplní pole se seznamem na pásu karet pomocí písem typ dříve zadaný písma, znaková sada a výšky a rodiny.  
  
```  
void RebuildFonts();
```  
  
### <a name="remarks"></a>Poznámky  
 Můžete zadat typ písma, znaková sada, a výšky a rodiny písem, které chcete zahrnout do pole se seznamem pásu karet písma pole [konstruktor](#cmfcribbonfontcombobox) pro tuto třídu nebo voláním [CMFCRibbonFontComboBox::BuildFonts](#buildfonts).  
  
##  <a name="setfont"></a>CMFCRibbonFontComboBox::SetFont  
 Vybere písmo zadaný v poli se seznamem.  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BOOL bExact = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Určuje název písma. Chcete-li vybrat.  
  
 `nCharSet`  
 Určuje znakovou sadu pro vybrané písmo.  
  
 `bExact`  
 `TRUE`Chcete-li určit, že při výběru písmo; musí odpovídat znakové sady `FALSE` k určení, že při výběru písmo můžete ignorovat znaková sada.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zadaný písmo byl nalezen a vybrané; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcharset"></a>CMFCRibbonFontComboBox::GetCharSet  
 Vrátí zadanou znakovou sadu.  
  
```  
BYTE GetCharSet() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Znakové sady (viz LOGFONT v dokumentaci k Windows SDK).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getfonttype"></a>CMFCRibbonFontComboBox::GetFontType  
 Vrátí jaké typy písem zobrazíte v pole se seznamem. Platné možnosti jsou DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE nebo jejich bitové kombinace.  
  
```  
int GetFontType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Typy písem (viz EnumFontFamProc v dokumentaci k Windows SDK).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpitchandfamily"></a>CMFCRibbonFontComboBox::GetPitchAndFamily  
 Vrátí výšku a rodiny písem, která se zobrazí v seznamu.  
  
```  
BYTE GetPitchAndFamily() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řady a výška (viz LOGFONT v dokumentaci k Windows SDK).  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonComboBox – třída](../../mfc/reference/cmfcribboncombobox-class.md)
