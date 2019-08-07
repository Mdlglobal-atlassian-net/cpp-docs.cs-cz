---
title: CMFCPropertyGridFileProperty Class
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: 4b64d18a67ea499c202b81481684227200846483
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821278"
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty Class

`CMFCPropertyGridFileProperty` Třída podporuje položku ovládacího prvku seznamu vlastností, která otevře dialogové okno Výběr souboru.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|`CMFCPropertyGridFileProperty` Vytvoří objekt.|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|`CMFCPropertyGridFileProperty::OnClickButton`|(Overrides [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

### <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpropertygridctrl. h

##  <a name="cmfcpropertygridfileproperty"></a>CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty

`CMFCPropertyGridFileProperty` Vytvoří objekt.

```
CMFCPropertyGridFileProperty(
    const CString& strName,
    BOOL bOpenFileDialog,
    const CString& strFileName,
    LPCTSTR lpszDefExt=NULL,
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,
    LPCTSTR lpszFilter=NULL,
    LPCTSTR lpszDescr=NULL,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*strName*<br/>
pro Název vlastnosti

*bOpenFileDialog*<br/>
pro TRUE pro otevření dialogového okna **otevřít soubor** ; FALSE pro otevření dialogového okna **Uložit soubor** .

*strFileName*<br/>
pro Počáteční název souboru

*lpszDefExt*<br/>
pro Řetězec jedné nebo více přípon názvů souborů. Výchozí hodnota je NULL.

*dwFlags*<br/>
pro Příznaky dialogových oken Výchozí hodnota je bitová kombinace (nebo) hodnot OFN_HIDEREADONLY a OFN_OVERWRITEPROMPT.

*lpszFilter*<br/>
pro Řetězec jednoho nebo více filtrů souborů. Výchozí hodnota je NULL.

*lpszDescr*<br/>
pro Popis položky vlastnosti Výchozí hodnota je NULL.

*dwData*<br/>
pro Data specifická pro aplikaci, která jsou přidružena k položce vlastnosti. Například celé číslo 32 nebo ukazatel na jiná data. Výchozí hodnota je 0.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Úplný seznam dostupných příznaků najdete v tématu [Struktura lpstrFile](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt pomocí konstruktoru `CMFCPropertyGridFileProperty` třídy. Tento příklad je součástí ukázkového [vzorku sady Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty – třída](../../mfc/reference/cmfcpropertygridproperty-class.md)
