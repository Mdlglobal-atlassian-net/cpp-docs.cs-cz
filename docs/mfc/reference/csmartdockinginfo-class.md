---
title: Třída CSmartDockingInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo::CopyTo
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_bUseThemeColorInShading
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrBaseBackground
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneDest
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneSrc
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrTransparent
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_nCentralGroupOffset
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_sizeTotal
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerBmpResID
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerLightBmpResID
dev_langs:
- C++
helpviewer_keywords:
- CSmartDockingInfo [MFC], CopyTo
- CSmartDockingInfo [MFC], m_bUseThemeColorInShading
- CSmartDockingInfo [MFC], m_clrBaseBackground
- CSmartDockingInfo [MFC], m_clrToneDest
- CSmartDockingInfo [MFC], m_clrToneSrc
- CSmartDockingInfo [MFC], m_clrTransparent
- CSmartDockingInfo [MFC], m_nCentralGroupOffset
- CSmartDockingInfo [MFC], m_sizeTotal
- CSmartDockingInfo [MFC], m_uiMarkerBmpResID
- CSmartDockingInfo [MFC], m_uiMarkerLightBmpResID
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b787828c59535f0e3008816df6f4ab209e1d882c
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079131"
---
# <a name="csmartdockinginfo-class"></a>CSmartDockingInfo – třída
Definuje vzhled elementů inteligentní značky ukotvení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSmartDockingInfo : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CSmartDockingInfo::CSmartDockingInfo`|Výchozí konstruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSmartDockingInfo::CopyTo](#copyto)|Zkopíruje aktuální inteligentní ukotvení informace o parametrech do zadaných [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) objektu.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|Určuje, jestli se má použít aktuální barevný motiv při rozhraní zobrazí inteligentní značky ukotvení.|  
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|Určuje barvu pozadí základní inteligentní ukotvení značek.|  
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|Určuje barvu, která nahrazuje `m_clrToneSrc` v inteligentní ukotvení bitmap značky.|  
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|Určuje barvu inteligentního ukotvení bitmap značky.|  
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|Určuje barvu inteligentního ukotvení bitmap značky, když jsou transparentní.|  
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|Určuje posun centrálního skupiny inteligentní značky ukotvení z hranice obdélníku centrální skupiny.|  
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|Celková velikost všech inteligentních značek ukotvení určuje ve skupině.|  
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|Definuje ID rastrových obrázků, který rozhraní používá pro inteligentní ukotvení značek, které nejsou zvýrazněná prostředků.|  
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|Definuje ID rastrových obrázků, který rozhraní používá pro inteligentní ukotvení označení, která je zvýrazněná prostředků.|  
  
## <a name="remarks"></a>Poznámky  
 Obslužné rutiny framework inteligentní značky ukotvení interně. Následující obrázek znázorňuje standardní značky inteligentního dokování:  
  
 ![Standardní značky pro inteligentní ukotvení](../../mfc/reference/media/nextsdmarkers.png "nextsdmarkers")  
  
 Obrázek na levé straně na tomto obrázku ukazuje centrální skupinu inteligentní ukotvení značku, nemá ukotvení na kartě povoleno. Obrázek uprostřed ukazuje inteligentní ukotvení značku pravý okraj. Obrázek na pravé straně ukazuje centrální skupinu inteligentní ukotvení značku která nemá ukotvení na kartě povoleno. Inteligentní značky centrální skupinu ukotvení má hlavní rastrového obrázku a pět inteligentní ukotvení bitmap značky.  
  
 Můžete přizpůsobit inteligentních značek ukotvení následující parametry:  
  
-   Barva. Můžete například nahradit všechny uživatelem definovaných barev modrou barvu značek na obrázku.  
  
-   Průhledná barva.  
  
-   Posun ukotvení inteligentní značky ve skupině centrální z ohraničení ohraničující obdélník.  
  
-   Hlavní bitmapy, který představuje centrální skupinu.  
  
-   Rastrové obrázky, který představuje obyčejnými a zvýrazněná inteligentní ukotvení značek.  
  
 Následující obrázek znázorňuje příklad inteligentní ukotvení značek, které byly upraveny:  
  
 ![Vlastní značky pro inteligentní ukotvení](../../mfc/reference/media/nextsdmarkerscustom.png "nextsdmarkerscustom")  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxDockingManager.h  
  
##  <a name="copyto"></a>  CSmartDockingInfo::CopyTo  
 Zkopíruje aktuální inteligentní ukotvení parametry do zadaných [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) objektu.  
  
```  
void CopyTo(CSmartDockingInfo& params);
```  
  
### <a name="parameters"></a>Parametry  
 [out] *parametry*  
 Objekt typu `CSmartDockingInfo` , se zobrazí v parametrech aktuální inteligentní ukotvení.  
  
##  <a name="m_busethemecolorinshading"></a>  CSmartDockingInfo::m_bUseThemeColorInShading  
 Určuje, jestli se má použít aktuální barevný motiv při rozhraní zobrazí inteligentní značky ukotvení.  
  
```  
BOOL m_bUseThemeColorInShading;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `TRUE`, značek jsou vykreslovány pomocí aktuální barva motivu; v opačném případě jsou vykreslovány značek světla modrou barvou.  
  
 Výchozí hodnota je `FALSE`.  
  
##  <a name="m_clrbasebackground"></a>  CSmartDockingInfo::m_clrBaseBackground  
 Určuje barvu pozadí základní inteligentní ukotvení značek.  
  
```  
COLORREF m_clrBaseBackground;  
```  
  
##  <a name="m_clrtonedest"></a>  CSmartDockingInfo::m_clrToneDest  
 Určuje barvu, která nahradí `m_clrToneSrc` v inteligentní ukotvení bitmap značky.  
  
```  
COLORREF m_clrToneDest;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavením této hodnoty můžete změnit barvu značky bitmap prostřednictvím kódu programu. Například pokud chcete změnit barvu standardní značek, které jsou součástí rozhraní, nastavte tuto hodnotu na požadovanou barvu. Ve výchozím nastavení [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc) je nastaven na RGB (61, 123, 241) (namodralý barvu).  
  
 Chcete-li změnit barvu vlastní značky, musíte zadat oba `m_clrToneDest` a `m_clrToneSrc`.  
  
##  <a name="m_clrtonesrc"></a>  CSmartDockingInfo::m_clrToneSrc  
 Určuje barvu inteligentního ukotvení bitmap značky.  
  
```  
COLORREF m_clrToneSrc;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto hodnotu nastavte jenom v případě, že budete chtít nahradit barvu vlastního rastrového obrázku s jinou barvou. Není nutné tuto hodnotu nastavit, pokud chcete změnit barvu standard (rámec poskytovaný) značky.  
  
 Použití `(COLORREF)-1` člen skupiny inteligentní ukotvení ponechat prázdné.  
  
##  <a name="m_clrtransparent"></a>  CSmartDockingInfo::m_clrTransparent  
 Určuje barvu inteligentního ukotvení bitmap značky, když jsou transparentní.  
  
```  
COLORREF m_clrTransparent;  
```  
  
### <a name="remarks"></a>Poznámky  
 Je nutné nastavit tuto hodnotu, při zobrazení vlastní značky a vlastní bitmap ve skupině ukotvení.  
  
##  <a name="m_ncentralgroupoffset"></a>  CSmartDockingInfo::m_nCentralGroupOffset  
 Určuje odsazení mezi centrální skupina inteligentní značky ukotvení a hranice obdélníku centrální skupiny.  
  
```  
int m_nCentralGroupOffset;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto hodnotu zadejte, pokud chcete změnit výchozí posun mezi vlastní značky a rozsah skupiny centrální inteligentní značky ukotvení. Výchozí posun je 5 pixelů.  
  
##  <a name="m_sizetotal"></a>  CSmartDockingInfo::m_sizeTotal  
 Určuje celkovou velikost ohraničující obdélník ohraničující všechny značky inteligentního ukotvení v centrální skupinu.  
  
```  
CSize m_sizeTotal;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavit `m_sizeTotal` velikosti ohraničující obdélník centrální skupinu značky. Musíte zadat tuto hodnotu, pokud používáte vlastní bitmap pro označení.  
  
##  <a name="m_uimarkerbmpresid"></a>  CSmartDockingInfo::m_uiMarkerBmpResID  
 Definuje ID rastrových obrázků, které se používají pro – zvýrazněná vlastní značky inteligentního dokování prostředků.  
  
```  
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];  
```  
  
### <a name="remarks"></a>Poznámky  
 Toto pole vyplníte ID rastrových obrázků představující inteligentní značky ukotvení prostředků. `AFX_SD_MARKERS_NUM` aktuálně je definován jako 5. Vyplňte pole následujícím způsobem:  
  
 `params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;`  
  
 `params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;`  
  
 `params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;`  
  
 `params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;`  
  
 `params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;`  
  
##  <a name="m_uimarkerlightbmpresid"></a>  CSmartDockingInfo::m_uiMarkerLightBmpResID  
 Definuje ID rastrových obrázků, které se používají pro zvýrazněná vlastní značky inteligentního ukotvení prostředků.  
  
```  
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];  
```  
  
### <a name="remarks"></a>Poznámky  
 Toto pole vyplníte ID rastrových obrázků představující zvýrazněná inteligentních značek ukotvení prostředků. `AFX_SD_MARKERS_NUM` aktuálně je definován jako 5. Vyplňte pole následujícím způsobem:  
  
 `params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;`  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)
