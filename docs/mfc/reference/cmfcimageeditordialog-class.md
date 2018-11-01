---
title: CMFCImageEditorDialog – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 84bbe72abeedc03f19f06a1f8498023ff54be95e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503061"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog – třída

`CMFCImageEditorDialog` Třída podporuje dialogové okno editor s bitové kopie.

## <a name="syntax"></a>Syntaxe

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|Vytvoří `CMFCImageEditorDialog` objektu.|

## <a name="remarks"></a>Poznámky

`CMFCImageEditorDialog` Třída poskytuje dialogové okno, které obsahuje:

- Oblast obrázku, který můžete použít ke změně jednotlivých pixelech ve bitovou kopii.

- Kreslicí nástroje k úpravě pixelů v oblasti obrázku.

- Palety barev pro určení barvy, který používá nástroje pro kreslení.

- Náhled zobrazující efekt úprav.

Následující obrázek znázorňuje dialogové okno editoru obrázků.

![Dialogové okno CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "imageedit")

Jeden ze způsobů použití `CMFCImageEditorDialog` objekt je komunikace `CBitmap` obrázek, který se upravovat. Nevytvářejte velký obrázek, protože image oblast úprav má omezenou velikost a velikost logických pixel je upravit podle oblasti. Volání `DoModal` metoda spuštění modální dialogové okno.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[Cdialogex –](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog –](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afximageeditordialog.h

##  <a name="cmfcimageeditordialog"></a>  CMFCImageEditorDialog::CMFCImageEditorDialog

Vytvoří `CMFCImageEditorDialog` objektu.

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Ukazatel na bitovou kopii.

*pParent*<br/>
Ukazatel do nadřazeného okna aktuální dialogového okna editoru obrázků.

*nBitsPixel*<br/>
Počet bitů se používá k reprezentování barvu jednoho obrazového bodu, který se také označuje jako barevnou hloubku.  Pokud *nBitsPixel* -1 je parametr, barevnou hloubku je odvozen z image určené *pBitmap* parametru. Výchozí hodnota je -1.

### <a name="return-value"></a>Návratová hodnota

Chcete-li upravit obrázek, předejte ukazatel image na `CMFCImageEditorDialog` konstruktoru. Zavolejte `DoModal` metodu otevření modální dialogové okno. Když `DoModal` metoda vrací výsledek, rastrového obrázku obsahuje novou bitovou kopii.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCImageEditorDialog` třídy. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)
