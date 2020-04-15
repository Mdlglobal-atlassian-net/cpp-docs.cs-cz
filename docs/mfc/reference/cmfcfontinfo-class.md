---
title: Třída CMFCFontInfo
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
ms.openlocfilehash: 6e87971e2afefc9cf1574abe951920c254dcd2ae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367482"
---
# <a name="cmfcfontinfo-class"></a>Třída CMFCFontInfo

Třída `CMFCFontInfo` popisuje název a další atributy písma.

## <a name="syntax"></a>Syntaxe

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCFontInfo`|Vytvoří `CMFCFontInfo` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCFontInfo::GetfullName](#getfullname)|Načte zřetězené názvy písma a jeho znakovou sadu (skript).|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Hodnota, která určuje znakovou sadu (skript) přidruženou k písmu.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Hodnota, která určuje výšku a rodinu písma.|
|[CMFCFontInfo::m_nType](#m_ntype)|Hodnota, která určuje typ písma.|
|[CMFCFontInfo::m_strName](#m_strname)|Název písma; například **Arial**.|
|[CMFCFontInfo::m_strScript](#m_strscript)|Název znakové sady (skriptu) přidružené k písmu.|

## <a name="remarks"></a>Poznámky

Objekt můžete `CMFCFontInfo` připojit k položce třídy [TŘÍDY CMFCToolBarFontComboBox.](../../mfc/reference/cmfctoolbarfontcombobox-class.md) Volání [CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) metoda načíst ukazatel `CMFCFontInfo` na objekt.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCFontInfo` členy třídy. Příklad ukazuje, jak získat `CMFCFontInfo` objekt `CMFCRibbonFontComboBox`z , a jak získat přístup k jeho místní proměnné. Tento příklad je součástí [ukázky ukázky ukázky msoffice 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbarfontcombobox.h

## <a name="cmfcfontinfocmfcfontinfo"></a><a name="cmfcfontinfo"></a>CMFCFontInfo::CMFCFontInfo

Vytvoří `CMFCFontInfo` objekt.

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

*název lpsz*<br/>
[v] Název písma. Další informace naleznete `lfFaceName` v člen [logfont](/windows/win32/api/wingdi/ns-wingdi-logfontw) struktury.

*lpszScript*<br/>
[v] Název skriptu (znakové sady) písma.

*nSada char*<br/>
[v] Hodnota, která určuje znakovou sadu (skript) písma. Další informace naleznete `lfCharSet` v člen [logfont](/windows/win32/api/wingdi/ns-wingdi-logfontw) struktury.

*nPitchAndFamily*<br/>
[v] Hodnota, která určuje výšku a rodinu písma. Další informace naleznete `lfPitchAndFamily` v člen [logfont](/windows/win32/api/wingdi/ns-wingdi-logfontw) struktury.

*nTyp*<br/>
[v] Hodnota, která určuje typ písma. Tento parametr může být bitovou kombinací (OR) DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE.

*src*<br/>
[v] Existující `CMFCFontInfo` objekt, jehož členy `CMFCFontInfo` se používají k vytvoření tohoto objektu.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Tato dokumentace používá termíny *znakové sady* a *skript* zaměnitelně. *Skript*, který je také známý jako systém zápisu, je kolekce znaků a pravidel pro psaní těchto znaků v jednom nebo více jazycích. Kolekce znaků zahrnuje abecedu a interpunkci použitou v tomto skriptu. Například latinka se používá pro angličtinu, jak se mluví ve Spojených státech a jeho abeceda obsahuje znaky od A do Z. Člen `lfCharSet` struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) určuje znakovou sadu. Například hodnota ANSI_CHARSET určuje znakovou sadu ANSI, která obsahuje abecedu latinky.

## <a name="cmfcfontinfogetfullname"></a><a name="getfullname"></a>CMFCFontInfo::GetfullName

Načte zřetězené názvy písma a jeho znakovou sadu (skript).

```
CString GetFullName() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec, který obsahuje název písma a skript.

### <a name="remarks"></a>Poznámky

Pomocí této metody získat úplný název písma. Pokud je například název **písma Arial** a skript písma je **Cyrilice**, vrátí tato metoda hodnotu Arial (Cyrilice)".

## <a name="cmfcfontinfom_ncharset"></a><a name="m_ncharset"></a>CMFCFontInfo::m_nCharSet

Hodnota, která určuje znakovou sadu (skript) přidruženou k písmu.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v parametru *nCharSet* konstruktoru [CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="cmfcfontinfom_npitchandfamily"></a><a name="m_npitchandfamily"></a>CMFCFontInfo::m_nPitchAndFamily

Hodnota, která určuje výšku (velikost bodu) a rodinu (například patka, bez patkové a monospace) písma.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v parametru *nPitchAndFamily* konstruktoru [CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="cmfcfontinfom_ntype"></a><a name="m_ntype"></a>CMFCFontInfo::m_nType

Hodnota, která určuje typ písma.

```
const int m_nType;
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v parametru *nType* konstruktoru [CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="cmfcfontinfom_strname"></a><a name="m_strname"></a>CMFCFontInfo::m_strName

Název písma: například **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v parametru *lpszName* konstruktoru [CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="cmfcfontinfom_strscript"></a><a name="m_strscript"></a>CMFCFontInfo::m_strScript

Název znakové sady (skriptu) přidružené k písmu.

```
const CString m_strScript;
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v parametru *lpszScript* konstruktoru [CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox – třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox – třída](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
