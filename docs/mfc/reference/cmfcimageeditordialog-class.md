---
title: CMFCImageEditorDialog – třída
ms.date: 11/19/2018
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 23c2a919428689fe107b82041bd87b758ede2bc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367470"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog – třída

Třída `CMFCImageEditorDialog` podporuje dialogové okno editoru obrázků.

## <a name="syntax"></a>Syntaxe

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|Vytvoří `CMFCImageEditorDialog` objekt.|

## <a name="remarks"></a>Poznámky

Třída `CMFCImageEditorDialog` poskytuje dialogové okno, které obsahuje:

- Oblast obrázku, kterou použijete k úpravě jednotlivých obrazových bodů v obraze.

- Kreslicí nástroje pro úpravu obrazových bodů v oblasti obrázku.

- Paleta barev pro určení barvy, kterou používají kreslicí nástroje.

- Oblast náhledu, která zobrazuje efekt úprav.

Na následujícím obrázku je zobrazeno dialogové okno editoru obrázků.

![Dialogové okno CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "Dialogové okno CMFCImageEditorDialog")

Jedním ze způsobů `CMFCImageEditorDialog` použití objektu `CBitmap` je předat mu obrázek, který má být upraven. Nevytvářejte velký obraz, protože oblast úprav obrazu má omezenou velikost a velikost logického obrazového bodu je upravena tak, aby odpovídala oblasti. Volání `DoModal` metody pro spuštění modálního dialogového okna.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CmFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afximageeditordialog.h

## <a name="cmfcimageeditordialogcmfcimageeditordialog"></a><a name="cmfcimageeditordialog"></a>CMFCImageEditorDialog::CMFCImageEditorDialog

Vytvoří `CMFCImageEditorDialog` objekt.

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Ukazatel na obrázek.

*pParent*<br/>
Ukazatel na nadřazené okno aktuálního dialogového okna editoru obrázků.

*nBitsPixel*<br/>
Počet bitů použitých k reprezentaci barvy jednoho obrazového bodu, který se také označuje jako barevná hloubka.  Pokud je parametr *nBitsPixel* -1, hloubka barev je odvozena od obrazu určeného parametrem *pBitmap.* Výchozí hodnota je -1.

### <a name="return-value"></a>Návratová hodnota

Chcete-li upravit obrázek, předaďte konstruktoru ukazatel obrázku. `CMFCImageEditorDialog` Potom voláním `DoModal` metody otevřete modální dialogové okno. Když `DoModal` se metoda vrátí, bitmapa obsahuje nový obraz.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCImageEditorDialog` třídy. Tento příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)
