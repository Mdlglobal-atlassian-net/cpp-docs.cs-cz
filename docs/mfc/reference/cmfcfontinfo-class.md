---
title: CMFCFontInfo – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
ms.openlocfilehash: a27606b494b13cd7b50f01b38fa95a918bacc7aa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505274"
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo – třída

`CMFCFontInfo` Třída popisuje název a další atributy písma.

## <a name="syntax"></a>Syntaxe

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|`CMFCFontInfo`|`CMFCFontInfo` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCFontInfo::GetFullName](#getfullname)|Načte zřetězené názvy písma a jeho znakové sady (skriptu).|

### <a name="data-members"></a>Datové členy

|Name|Popis|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Hodnota, která určuje znakovou sadu (skript) spojenou s fontem.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Hodnota, která určuje rozteč a rodinu písma.|
|[CMFCFontInfo::m_nType](#m_ntype)|Hodnota, která určuje typ písma.|
|[CMFCFontInfo::m_strName](#m_strname)|Název písma; například **Arial**.|
|[CMFCFontInfo::m_strScript](#m_strscript)|Název znakové sady (skriptu) přidružené k danému písmu.|

## <a name="remarks"></a>Poznámky

`CMFCFontInfo` Objekt lze připojit k položce třídy třídy [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) . Voláním metody [CMFCToolBarFontComboBox:: GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) načtěte ukazatel na `CMFCFontInfo` objekt.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé členy `CMFCFontInfo` třídy. Příklad ukazuje `CMFCFontInfo` `CMFCRibbonFontComboBox`, jak získat objekt z a, jak přistupovat k místním proměnným. Tento příklad je součástí [ukázky ukázky MSOffice 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbarfontcombobox. h

##  <a name="cmfcfontinfo"></a>CMFCFontInfo::CMFCFontInfo

`CMFCFontInfo` Vytvoří objekt.

```
CMFCFontInfo(
    LPCTSTR lpszName,
    LPCTSTR lpszScript,
    BYTE nCharSet,
    BYTE nPitchAndFamily,
    int nType);

CMFCFontInfo(const CMFCFontInfo& src);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
pro Název písma Další informace naleznete v tématu `lfFaceName` člen struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*lpszScript*<br/>
pro Název skriptu (znakové sady) písma.

*nCharSet*<br/>
pro Hodnota, která určuje znakovou sadu (skript) písma. Další informace naleznete v tématu `lfCharSet` člen struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*nPitchAndFamily*<br/>
pro Hodnota, která určuje rozteč a rodinu písma. Další informace naleznete v tématu `lfPitchAndFamily` člen struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*nType*<br/>
pro Hodnota, která určuje typ písma. Tento parametr může být bitovou kombinací (nebo) hodnot DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE.

*src*<br/>
pro Existující `CMFCFontInfo` objekt, jehož členové jsou použity k vytvoření tohoto `CMFCFontInfo` objektu.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Tato dokumentace používá znaková *sada* pro výrazy a zaměnitelné *skripty* . *Skript*, který se také označuje jako systém pro zápis, je kolekce znaků a pravidel pro zápis těchto znaků v jednom nebo více jazycích. Kolekce znaků obsahuje abecední a interpunkční znaménko použité v tomto skriptu. Například skript latinky se používá pro angličtinu, protože se používá v USA a jeho abeceda obsahuje znaky z A až Z. Člen struktury LOGFONT určuje znakovou sadu. [](/windows/win32/api/wingdi/ns-wingdi-logfontw) `lfCharSet` Například hodnota ANSI_CHARSET určuje znakovou sadu ANSI, která obsahuje abecední znak skriptu latinky.

##  <a name="getfullname"></a>CMFCFontInfo:: getfull

Načte zřetězené názvy písma a jeho znakové sady (skriptu).

```
CString GetFullName() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec, který obsahuje název a skript písma.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li získat úplný název písma. Například pokud je název písma písmo **Arial** a skript písma je **cyrilice**, vrátí tato metoda "Arial (cyrilice)".

##  <a name="m_ncharset"></a>CMFCFontInfo::m_nCharSet

Hodnota, která určuje znakovou sadu (skript) spojenou s fontem.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v parametru *nCharSet* konstruktoru [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_npitchandfamily"></a>CMFCFontInfo::m_nPitchAndFamily

Hodnota, která určuje rozteč (velikost bodu) a rodinu (například Serif, Sans-Serif a neproporcionální) písma.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v parametru *nPitchAndFamily* konstruktoru [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType

Hodnota, která určuje typ písma.

```
const int m_nType;
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v parametru *noznámení* konstruktoru [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_strname"></a>CMFCFontInfo::m_strName

Název písma: například **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v parametru *lpszName* konstruktoru [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript

Název znakové sady (skriptu) přidružené k danému písmu.

```
const CString m_strScript;
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v parametru *lpszScript* konstruktoru [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox – třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox – třída](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
