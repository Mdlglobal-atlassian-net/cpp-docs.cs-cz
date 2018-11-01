---
title: Cmfcpropertygridfileproperty – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: 659b2cf4cf563450e51b1d6f407414273a5109aa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487357"
---
# <a name="cmfcpropertygridfileproperty-class"></a>Cmfcpropertygridfileproperty – třída

`CMFCPropertyGridFileProperty` Třída podporuje položku ovládacího prvku seznamu s, která se otevře dialogové okno Výběr souboru.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|Vytvoří `CMFCPropertyGridFileProperty` objektu.|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|`CMFCPropertyGridFileProperty::OnClickButton`|(Přepíše [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

### <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cmfcpropertygridproperty –](../../mfc/reference/cmfcpropertygridproperty-class.md)

[Cmfcpropertygridfileproperty –](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpropertygridctrl.h

##  <a name="cmfcpropertygridfileproperty"></a>  CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty

Vytvoří `CMFCPropertyGridFileProperty` objektu.

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

*%{strName/*<br/>
[in] Název vlastnosti.

*bOpenFileDialog*<br/>
[in] True pro otevření **otevřít soubor** dialogové okno; FALSE, pokud chcete otevřít **uložit soubor** dialogové okno.

*%{strFileName/*<br/>
[in] Je původní název souboru.

*lpszDefExt*<br/>
[in] Řetězec jeden nebo více přípon souborů. Výchozí hodnota je NULL.

*dwFlags*<br/>
[in] Dialogové okno pole příznaky. Výchozí hodnota je bitová kombinace (nebo) OFN_HIDEREADONLY a OFN_OVERWRITEPROMPT.

*lpszFilter*<br/>
[in] Řetězec jeden nebo více filtrů souborů. Výchozí hodnota je NULL.

*lpszDescr*<br/>
[in] Popis vlastnosti položky. Výchozí hodnota je NULL.

*dwData*<br/>
[in] Specifické pro aplikaci data, která je přidružená k položce vlastnost. Například 32bitové celé číslo nebo ukazatel na další data. Výchozí hodnota je 0.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Úplný seznam dostupných příznaků najdete v tématu [LPSTRFILE struktury](/windows/desktop/api/commdlg/ns-commdlg-tagofna).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt pomocí konstruktoru `CMFCPropertyGridFileProperty` třídy. V tomto příkladu je součástí [Visual Studio demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty – třída](../../mfc/reference/cmfcpropertygridproperty-class.md)
