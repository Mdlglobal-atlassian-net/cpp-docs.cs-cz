---
title: CMFCToolBarComboBoxEdit – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit
helpviewer_keywords:
- CMFCToolBarComboBoxEdit [MFC], CMFCToolBarComboBoxEdit
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
ms.openlocfilehash: 2a0ab1766f42d34c86339cffb86f876358c97a4a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504869"
---
# <a name="cmfctoolbarcomboboxedit-class"></a>CMFCToolBarComboBoxEdit – třída

Rozhraní používá `CMFCToolBarComboBoxEdit` třídu k vytvoření tlačítka panelu nástrojů, které se chová jako upravitelný ovládací prvek pole se seznamem.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarComboBoxEdit : public CEdit
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit](#cmfctoolbarcomboboxedit)|`CMFCToolBarComboBoxEdit` Vytvoří objekt.|
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|Přeloží zprávy oken před odesláním do funkcí Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Potlačení [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|

### <a name="remarks"></a>Poznámky

Odvodit třídu z `CMFCToolBarComboBoxEdit` třídy pro přizpůsobení jeho operací úprav.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbarcomboboxbutton. h

##  <a name="cmfctoolbarcomboboxedit"></a>CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit

`CMFCToolBarComboBoxEdit` Vytvoří objekt.

```
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```

### <a name="parameters"></a>Parametry

*combo*<br/>
pro Odkaz na objekt [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) , což je tlačítko panelu nástrojů, které obsahuje ovládací prvek pole se seznamem.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCToolBarComboBoxEdit` třídy. Tento fragment kódu je součástí ukázky [Ukázka IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#5](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarComboBoxButton – třída](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)
