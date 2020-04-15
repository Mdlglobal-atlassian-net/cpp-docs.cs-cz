---
title: CMFCPropertyGridFileProperty – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: 0ce3321968f0c29ce3b946f6127e4435b531c422
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360585"
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty – třída

Třída `CMFCPropertyGridFileProperty` podporuje položku ovládacího prvku seznamu vlastností, která otevře dialogové okno pro výběr souboru.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCPropertyGridFileProperty::VLASTNOST CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|Vytvoří `CMFCPropertyGridFileProperty` objekt.|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|`CMFCPropertyGridFileProperty::OnClickButton`|(Přepíše [CMFCPropertyProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

### <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Vlastnost CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[Vlastnost CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpropertygridctrl.h

## <a name="cmfcpropertygridfilepropertycmfcpropertygridfileproperty"></a><a name="cmfcpropertygridfileproperty"></a>CMFCPropertyGridFileProperty::VLASTNOST CMFCPropertyGridFileProperty

Vytvoří `CMFCPropertyGridFileProperty` objekt.

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
[v] Název vlastnosti.

*bOtevřítdialog*<br/>
[v] TRUE pro otevření dialogového okna **Otevřít soubor;** Nepravda pro otevření dialogového okna **Uložit soubor.**

*Strfilename*<br/>
[v] Počáteční název souboru.

*lpszDefExt*<br/>
[v] Řetězec jedné nebo více přípon názvů souborů. Výchozí hodnota je NULL.

*dwFlags*<br/>
[v] Příznaky dialogového okna. Výchozí hodnota je bitová kombinace (OR) OFN_HIDEREADONLY a OFN_OVERWRITEPROMPT.

*lpszFiltr*<br/>
[v] Řetězec jednoho nebo více filtrů souborů. Výchozí hodnota je NULL.

*lpszDescr*<br/>
[v] Popis položky vlastnosti. Výchozí hodnota je NULL.

*dwData*<br/>
[v] Data specifická pro aplikaci, která je přidružena k položce vlastnosti. Například 32bitové celé číslo nebo ukazatel na jiná data. Výchozí hodnota je 0.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Úplný seznam dostupných příznaků naleznete v tématu [OPENFILENAME structure](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt pomocí konstruktoru třídy. `CMFCPropertyGridFileProperty` Tento příklad je součástí [ukázky visual studia](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty – třída](../../mfc/reference/cmfcpropertygridproperty-class.md)
