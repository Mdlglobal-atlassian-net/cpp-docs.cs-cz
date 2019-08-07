---
title: CMFCRibbonApplicationButton – třída
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
ms.openlocfilehash: d1dc8ef6e801623aa96cb4b47936413cd17f24f0
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821242"
---
# <a name="cmfcribbonapplicationbutton-class"></a>CMFCRibbonApplicationButton – třída

Implementuje speciální tlačítko, které se nachází v levém horním rohu okna aplikace. Po kliknutí na toto tlačítko se otevře nabídka, která obvykle obsahuje běžné příkazy **souborů** , jako je například **otevřít**, **Uložit**a **ukončit**.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|Vytvoří a inicializuje `CMFCRibbonApplicationButton` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|Používá se rozhraním k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCRibbonApplicationButton::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Přiřadí obrázek tlačítku aplikace pásu karet.|

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody ve `CMFCRibbonApplicationButton` třídě. Příklad ukazuje, jak přiřadit obrázek tlačítku aplikace a jak nastavit jeho popis. Tento fragment kódu je součástí ukázkového [klienta pro vykreslování](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonBar. h

##  <a name="cmfcribbonapplicationbutton"></a>CMFCRibbonApplicationButton::CMFCRibbonApplicationButton

Vytvoří a inicializuje objekt [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md) .

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>Parametry

*uiBmpResID*<br/>
ID prostředku obrázku, který má být zobrazen na tlačítku aplikace

*hBmp*<br/>
Popisovač rastrového obrázku, který má být zobrazen na tlačítku aplikace.

### <a name="remarks"></a>Poznámky

Tlačítko aplikace pásu karet je speciální tlačítko, které se nachází v levém horním rohu okna aplikace. Když uživatel klikne na toto tlačítko, aplikace otevře nabídku, která obvykle obsahuje běžné příkazy **souborů** , například **otevřít**, **Uložit**a **ukončit**.

##  <a name="setimage"></a>CMFCRibbonApplicationButton::SetImage

Přiřadí obrázek tlačítku aplikace.

```
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>Parametry

*uiBmpResID*<br/>
pro ID prostředku obrázku, který má být zobrazen na tlačítku aplikace

*hBmp*<br/>
pro Popisovač rastrového obrázku, který má být zobrazen na tlačítku aplikace.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li přiřadit nový obrázek tlačítku aplikace pásu karet po vytvoření tlačítka. Tlačítko aplikace se nachází v levém horním rohu okna aplikace.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
