---
title: Třída CSmartDockingInfo
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
ms.openlocfilehash: ebb5e75b5b298097cfce043bd83ec88ca0ab4030
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751304"
---
# <a name="csmartdockinginfo-class"></a>Třída CSmartDockingInfo

Definuje vzhled inteligentních značkovacích značek.

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
|[CSmartDockingInfo::Kopírovat](#copyto)|Zkopíruje aktuální parametry inteligentních dokovacích informací do poskytnutého objektu [CSmartDockingInfo.](../../mfc/reference/csmartdockinginfo-class.md)|

### <a name="data-members"></a>Členové dat

|Název|Popis|
|----------|-----------------|
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|Určuje, zda se má použít aktuální barva motivu, když se v rámci zobrazí inteligentní značky ukotvení.|
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|Určuje základní barvu pozadí inteligentních značek ukotvení.|
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|Určuje barvu, která `m_clrToneSrc` nahrazuje bitmapy inteligentních dokovacích značek.|
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|Určuje barvu bitmap inteligentních dokovacích značek.|
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|Určuje barvu bitmap inteligentních dokovacích značek, pokud jsou průhledné.|
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|Určuje posun centrální skupiny inteligentních dokovacích značek od hranic obdélníku centrální skupiny.|
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|Určuje celkovou velikost všech inteligentních dokovacích značek ve skupině.|
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|Definuje ID prostředků bitmap, které rozhraní používá pro inteligentní značky ukotvení, které nejsou zvýrazněny.|
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|Definuje ID prostředků bitmap, které rozhraní používá pro inteligentní značky ukotvení, které jsou zvýrazněny.|

## <a name="remarks"></a>Poznámky

Rámec zpracovává inteligentní dokovací značky interně. Následující obrázek znázorňuje standardní inteligentní dokovací značky:

![Standardní značky pro inteligentní dokování](../../mfc/reference/media/nextsdmarkers.png "Standardní značky pro inteligentní dokování")

Na tomto obrázku obrázek vlevo zobrazuje značku inteligentního ukotvení centrální skupiny, která nemá povoleno ukotvení na kartě. Obrázek uprostřed zobrazuje značku inteligentního dokování pravého okraje. Obrázek vpravo zobrazuje centrální skupinu inteligentní dokovací značku, která má ukotvení na kartě povoleno. Centrální skupina inteligentní dokovací značka má hlavní bitmapu a pět inteligentních dokovacích rastrů značky.

Můžete přizpůsobit následující parametry inteligentních dokovacích značek:

- Barev. Můžete například nahradit modrou barvu značek na obrázku libovolnou uživatelem definovanou barvou.

- Barva průhlednosti.

- Odsazení inteligentní dokovací značky v centrální skupině od okraje ohraničovacího obdélníku.

- Hlavní bitmapa, která představuje centrální skupinu.

- Bitmapy, které představují pravidelné a zvýrazněné inteligentní dokovací značky.

Následující obrázek znázorňuje příklad inteligentních značek ukotvení, které byly přizpůsobeny:

![Vlastní značky pro inteligentní dokování](../../mfc/reference/media/nextsdmarkerscustom.png "Vlastní značky pro inteligentní dokování")

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDockingManager.h

## <a name="csmartdockinginfocopyto"></a><a name="copyto"></a>CSmartDockingInfo::Kopírovat

Zkopíruje aktuální inteligentní dokovací parametry do zadaný objekt [CSmartDockingInfo.](../../mfc/reference/csmartdockinginfo-class.md)

```cpp
void CopyTo(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Parametry

*params*<br/>
[out] Objekt typu, `CSmartDockingInfo` který je naplněn aktuálními parametry inteligentního ukotvení.

## <a name="csmartdockinginfom_busethemecolorinshading"></a><a name="m_busethemecolorinshading"></a>CSmartDockingInfo::m_bUseThemeColorInShading

Určuje, zda se má použít aktuální barva motivu, když se v rámci zobrazí inteligentní značky ukotvení.

```
BOOL m_bUseThemeColorInShading;
```

### <a name="remarks"></a>Poznámky

Pokud je hodnota PRAVDA, jsou značky nakresleny pomocí aktuální barvy motivu; jinak jsou značky nakresleny světle modrou barvou.

Výchozí hodnota je FALSE.

## <a name="csmartdockinginfom_clrbasebackground"></a><a name="m_clrbasebackground"></a>CSmartDockingInfo::m_clrBaseBackground

Určuje základní barvu pozadí inteligentních značek ukotvení.

```
COLORREF m_clrBaseBackground;
```

## <a name="csmartdockinginfom_clrtonedest"></a><a name="m_clrtonedest"></a>CSmartDockingInfo::m_clrToneDest

Určuje barvu, která `m_clrToneSrc` bude nahrazena v bitmapách inteligentních dokovacích značek.

```
COLORREF m_clrToneDest;
```

### <a name="remarks"></a>Poznámky

Tuto hodnotu nastavte, chcete-li programově měnit barvu bitmap značek. Chcete-li například změnit barvu standardních značek dodávaných s rámcem, nastavte tuto hodnotu na požadovanou barvu. Ve výchozím nastavení [cSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc) je nastavena na RGB (61, 123, 241) (modravá barva).

Chcete-li změnit barvu vlastních značek, `m_clrToneDest` `m_clrToneSrc`musíte zadat obě značky a .

## <a name="csmartdockinginfom_clrtonesrc"></a><a name="m_clrtonesrc"></a>CSmartDockingInfo::m_clrToneSrc

Určuje barvu bitmap inteligentních dokovacích značek.

```
COLORREF m_clrToneSrc;
```

### <a name="remarks"></a>Poznámky

Tuto hodnotu nastavte pouze v případě, že chcete nahradit barvu vlastní bitmapy jinou barvou. Tuto hodnotu není třeba nastavovat, pokud měníte barvu standardní značky (poskytujete rámec).

Slouží `(COLORREF)-1` k tomu, aby byl člen inteligentní dokovací skupiny prázdný.

## <a name="csmartdockinginfom_clrtransparent"></a><a name="m_clrtransparent"></a>CSmartDockingInfo::m_clrTransparent

Určuje barvu bitmap inteligentních dokovacích značek, pokud jsou průhledné.

```
COLORREF m_clrTransparent;
```

### <a name="remarks"></a>Poznámky

Tuto hodnotu je nutné nastavit při zobrazení vlastních značek a vlastních bitmap v dokovací skupině.

## <a name="csmartdockinginfom_ncentralgroupoffset"></a><a name="m_ncentralgroupoffset"></a>CSmartDockingInfo::m_nCentralGroupOffset

Určuje posun mezi centrální skupinou inteligentních značek ukotvení a hranicemi obdélníku centrální skupiny.

```
int m_nCentralGroupOffset;
```

### <a name="remarks"></a>Poznámky

Tuto hodnotu zadejte, pokud chcete změnit výchozí posun mezi vlastními značkami a hranicemi centrální skupiny inteligentních značek ukotvení. Výchozí posun je 5 pixelů.

## <a name="csmartdockinginfom_sizetotal"></a><a name="m_sizetotal"></a>CSmartDockingInfo::m_sizeTotal

Určuje celkovou velikost ohraničujícího obdélníku, který obklopuje všechny inteligentní dokovací značky v centrální skupině.

```
CSize m_sizeTotal;
```

### <a name="remarks"></a>Poznámky

Nastavte `m_sizeTotal` velikost ohraničovacího obdélníku značky centrální skupiny. Tuto hodnotu musíte zadat, pokud používáte vlastní rastrové obrázky pro značky.

## <a name="csmartdockinginfom_uimarkerbmpresid"></a><a name="m_uimarkerbmpresid"></a>CSmartDockingInfo::m_uiMarkerBmpResID

Definuje ID prostředků bitmap, které se používají pro nezvýrazněné vlastní inteligentní dokovací značky.

```
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Poznámky

Vyplňte toto pole ID prostředků rastrových obrázků představujících inteligentní značky ukotvení. AFX_SD_MARKERS_NUM je v současné době definována jako 5. Pole vyplníte následujícím způsobem:

```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```

## <a name="csmartdockinginfom_uimarkerlightbmpresid"></a><a name="m_uimarkerlightbmpresid"></a>CSmartDockingInfo::m_uiMarkerLightBmpResID

Definuje ID prostředků bitmap, které se používají pro zvýrazněné vlastní inteligentní dokovací značky.

```
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Poznámky

Vyplňte toto pole ID prostředků rastrů představujících zvýrazněné inteligentní značky ukotvení. AFX_SD_MARKERS_NUM je v současné době definována jako 5. Pole vyplníte následujícím způsobem:

```cpp
params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;
params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;
params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;
params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;
params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;
```

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)
