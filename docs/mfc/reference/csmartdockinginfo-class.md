---
title: CSmartDockingInfo Class
ms.date: 11/19/2018
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
ms.openlocfilehash: d5f918b591e1db9ff67288a8761f7554698fa761
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273462"
---
# <a name="csmartdockinginfo-class"></a>CSmartDockingInfo Class

Definuje vzhled značek inteligentního dokování.

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
|[CSmartDockingInfo::CopyTo](#copyto)|Zkopíruje aktuální inteligentní dokovací informace o parametrech do zadaných [csmartdockinginfo –](../../mfc/reference/csmartdockinginfo-class.md) objektu.|

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|Určuje, jestli se má použít aktuální barvu motivu, při zobrazí rozhraní značek inteligentního dokování.|
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|Určuje barvu pozadí základní značek inteligentního dokování.|
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|Určuje barvu, která nahradí `m_clrToneSrc` v inteligentního dokování rastrové obrázky značky.|
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|Určuje barvu inteligentního dokování rastrové obrázky značky.|
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|Určuje barvu inteligentního dokování rastrových obrázků značky, pokud jsou transparentní.|
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|Určuje posun centrální skupina značek inteligentního dokování z obdélníku centrální skupiny hranic.|
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|Určuje celkovou velikost všech značek inteligentního dokování ve skupině.|
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|Definuje ID rastrové obrázky, systém použije pro značek inteligentního dokování, které se zvýrazněnou prostředků.|
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|Definuje ID rastrové obrázky, systém použije pro značek inteligentního dokování, kteří jsou zvýrazněni prostředků.|

## <a name="remarks"></a>Poznámky

Framework zpracovává inteligentní značky dokovací interně. Následující obrázek znázorňuje standardních značek inteligentního dokování:

![Standardní značky pro inteligentního dokování](../../mfc/reference/media/nextsdmarkers.png "standardní značky pro inteligentní ukotvení")

Na tomto obrázku zobrazuje obrázek na levé straně centrální skupina inteligentní dokovací značku, která nemá ukotvení na kartu povolena. Uprostřed obrázku značky pravého okraje inteligentní ukotvení. Na pravé straně obrázku centrální skupina inteligentní dokovací značku, na kterém ukotvení na kartu povolena. Inteligentní značky centrální skupina dokovací má hlavní rastrový obrázek a pět inteligentní dokovací rastrové obrázky značky.

Můžete přizpůsobit následující parametry značek inteligentního dokování:

- Barva. Můžete například nahradit všechny uživatelem definovaných barev modrou barvu značky na obrázku.

- Barva, průhlednost.

- Posun ukotvení inteligentní značky ve skupině centrální z ohraničení ohraničující obdélník.

- Hlavní rastrový obrázek, který představuje centrální skupina.

- Rastrové obrázky, který představuje pravidelné a zvýrazněné značek inteligentního dokování.

Následující obrázek znázorňuje příklad značek inteligentního dokování, které byly upraveny:

![Vlastní značky pro inteligentního dokování](../../mfc/reference/media/nextsdmarkerscustom.png "vlastní značky pro inteligentní ukotvení")

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDockingManager.h

##  <a name="copyto"></a>  CSmartDockingInfo::CopyTo

Zkopíruje aktuální inteligentního dokování parametry do zadaných [csmartdockinginfo –](../../mfc/reference/csmartdockinginfo-class.md) objektu.

```
void CopyTo(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Parametry

*params*<br/>
[out] Objekt typu `CSmartDockingInfo` , které se vyplní aktuální inteligentního dokování parametry.

##  <a name="m_busethemecolorinshading"></a>  CSmartDockingInfo::m_bUseThemeColorInShading

Určuje, jestli se má použít aktuální barvu motivu, při zobrazí rozhraní značek inteligentního dokování.

```
BOOL m_bUseThemeColorInShading;
```

### <a name="remarks"></a>Poznámky

Při hodnotě TRUE se značek jsou vykreslovány pomocí aktuální barva motivu; v opačném případě značek vykreslí ve světle modrou barvou.

Výchozí hodnota je FALSE.

##  <a name="m_clrbasebackground"></a>  CSmartDockingInfo::m_clrBaseBackground

Určuje barvu pozadí základní značek inteligentního dokování.

```
COLORREF m_clrBaseBackground;
```

##  <a name="m_clrtonedest"></a>  CSmartDockingInfo::m_clrToneDest

Určuje barvu, která nahradí `m_clrToneSrc` v inteligentního dokování rastrové obrázky značky.

```
COLORREF m_clrToneDest;
```

### <a name="remarks"></a>Poznámky

Nastavením této hodnoty můžete změnit barvu značky bitmap prostřednictvím kódu programu. Například pokud chcete změnit barvu standardní značek, opatřeného rozhraní framework, nastavte tuto hodnotu na požadovanou barvu. Ve výchozím nastavení [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc) je nastavena na RGB (61, 123, 241) (namodralý barvu).

Chcete-li změnit barvu vlastní značky, musíte zadat oba `m_clrToneDest` a `m_clrToneSrc`.

##  <a name="m_clrtonesrc"></a>  CSmartDockingInfo::m_clrToneSrc

Určuje barvu inteligentního dokování rastrové obrázky značky.

```
COLORREF m_clrToneSrc;
```

### <a name="remarks"></a>Poznámky

Tuto hodnotu lze nastavte pouze v případě, že chcete barva vlastní rastrový obrázek nahraďte jinou barvu. Nemáte nastavte tuto hodnotu, pokud chcete změnit barvu úrovně Standard (rámec poskytovaný) značky.

Použití `(COLORREF)-1` ponechat prázdný člen skupiny inteligentního dokování.

##  <a name="m_clrtransparent"></a>  CSmartDockingInfo::m_clrTransparent

Určuje barvu inteligentního dokování rastrových obrázků značky, pokud jsou transparentní.

```
COLORREF m_clrTransparent;
```

### <a name="remarks"></a>Poznámky

Tato hodnota je nutné nastavit při zobrazení vlastní značky a vlastních rastrových obrázků ve skupině ukotvení.

##  <a name="m_ncentralgroupoffset"></a>  CSmartDockingInfo::m_nCentralGroupOffset

Určuje odsazení mezi centrální skupina značek inteligentního dokování a hranice centrální skupina obdélník.

```
int m_nCentralGroupOffset;
```

### <a name="remarks"></a>Poznámky

Tuto hodnotu zadejte, pokud chcete změnit výchozí posun mezi vlastní značky a hranice centrální skupina značek inteligentního dokování. Posun výchozí je 5 pixelů.

##  <a name="m_sizetotal"></a>  CSmartDockingInfo::m_sizeTotal

Určuje celkovou velikost ohraničující obdélník, který obklopuje všech značek inteligentního dokování v centrální skupina.

```
CSize m_sizeTotal;
```

### <a name="remarks"></a>Poznámky

Nastavte `m_sizeTotal` velikosti ohraničující obdélník centrální skupina značky. Musíte zadat tuto hodnotu, pokud používáte vlastní rastrové obrázky pro značky.

##  <a name="m_uimarkerbmpresid"></a>  CSmartDockingInfo::m_uiMarkerBmpResID

Definuje prostředek ID rastrové obrázky, které se používají pro křížového zvýraznění vlastních značek inteligentního dokování.

```
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Poznámky

Vyplňte tato pole ID rastrových obrázků představující značek inteligentního dokování prostředků. AFX_SD_MARKERS_NUM je aktuálně definován jako 5. Vyplnění pole následujícím způsobem:

```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```

##  <a name="m_uimarkerlightbmpresid"></a>  CSmartDockingInfo::m_uiMarkerLightBmpResID

Definuje prostředek ID rastrové obrázky, které se používají pro zvýrazněné vlastních značek inteligentního dokování.

```
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Poznámky

Vyplňte tato pole ID rastrových obrázků představující zvýrazněné značek inteligentního dokování prostředků. AFX_SD_MARKERS_NUM je aktuálně definován jako 5. Vyplnění pole následujícím způsobem:

```cpp
params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;
params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;
params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;
params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;
params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;
```

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)
