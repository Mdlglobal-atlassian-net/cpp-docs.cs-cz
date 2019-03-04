---
title: CMFCRibbonApplicationButton Class
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
ms.openlocfilehash: 892e9e56b6df5bc0a3dc0aa9cf3786e36b5311c7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302634"
---
# <a name="cmfcribbonapplicationbutton-class"></a>CMFCRibbonApplicationButton Class

Implementuje speciální tlačítko umístěné v levém horním rohu okna aplikace. Po kliknutí na tlačítko otevře nabídku, která obvykle obsahuje běžné **souboru** příkazy jako **otevřít**, **Uložit**, a **ukončovací**.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|Vytvoří a inicializuje `CMFCRibbonApplicationButton` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCRibbonApplicationButton::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Přiřadí obrázku tlačítka pásu karet aplikace.|

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCRibbonApplicationButton` třídy. Příklad ukazuje, jak přiřadit obrázek pro tlačítko aplikace a jak nastavit jeho popis. Tento fragment kódu je součástí [nakreslit Client sample](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonBar.h

##  <a name="cmfcribbonapplicationbutton"></a>  CMFCRibbonApplicationButton::CMFCRibbonApplicationButton

Vytvoří a inicializuje [cmfcribbonapplicationbutton –](../../mfc/reference/cmfcribbonapplicationbutton-class.md) objektu.

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
  CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>Parametry

*uiBmpResID*<br/>
ID prostředku bitové kopie se zobrazí na tlačítku aplikace.

*hBmp*<br/>
Popisovač rastrový obrázek se zobrazí na tlačítku aplikace.

### <a name="remarks"></a>Poznámky

Tlačítko aplikace pásu karet je speciální tlačítko, které se nachází v levém horním rohu okna aplikace. Když uživatel klikne na toto tlačítko, aplikace se otevře nabídka, která obvykle obsahuje běžné **souboru** příkazy, jako například **otevřít**, **Uložit**, a **ukončení**.

##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage

Přiřadí obrázek pro tlačítko aplikace.

```
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>Parametry

*uiBmpResID*<br/>
[in] ID prostředku bitové kopie se zobrazí na tlačítku aplikace.

*hBmp*<br/>
[in] Popisovač rastrový obrázek se zobrazí na tlačítku aplikace.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete po vytvoření tlačítka přiřadit novou bitovou kopii na pásu karet tlačítko aplikace. Tlačítko aplikace se nachází v levém horním rohu okna aplikace.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
