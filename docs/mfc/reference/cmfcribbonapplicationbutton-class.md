---
title: Třída CMFCFCRibbonApplicationButton
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
ms.openlocfilehash: 0debd40825990b647cd5b1df9a144e3abd450de3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361611"
---
# <a name="cmfcribbonapplicationbutton-class"></a>Třída CMFCFCRibbonApplicationButton

Implementuje speciální tlačítko umístěné v levém horním rohu okna aplikace. Po klepnutí se na tlačítko otevře nabídka, která obvykle obsahuje běžné příkazy **souboru,** jako **je Otevřít**, **Uložit**a **Ukončit**.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|Vytvoří a inicializuje `CMFCRibbonApplicationButton` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCRibbonApplicationButton::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCRibbonRibbonApplicationButton::SetImage](#setimage)|Přiřadí obrázek tlačítku aplikace pásu karet.|

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCRibbonApplicationButton` metody ve třídě. Příklad ukazuje, jak přiřadit obrázek tlačítku aplikace a jak nastavit jeho popisek. Tento fragment kódu je součástí [ukázky klienta Draw](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CmFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CmFCFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonBar.h

## <a name="cmfcribbonapplicationbuttoncmfcribbonapplicationbutton"></a><a name="cmfcribbonapplicationbutton"></a>CMFCRibbonRibbonApplicationButton::CMFCRibbonApplicationButton

Vytvoří a inicializuje objekt [CMFCRibbonApplicationButton.](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>Parametry

*uiBmpResID*<br/>
ID prostředku obrázku, který se má zobrazit na tlačítku aplikace.

*hBmp*<br/>
Úchyt k rastrové mapě, která se zobrazí na tlačítku aplikace.

### <a name="remarks"></a>Poznámky

Tlačítko aplikace pásu karet je speciální tlačítko, které se nachází v levém horním rohu okna aplikace. Když uživatel klepne na toto tlačítko, aplikace otevře nabídku, která obvykle obsahuje běžné příkazy **souboru,** například **Otevřít**, **Uložit**a **Ukončit**.

## <a name="cmfcribbonapplicationbuttonsetimage"></a><a name="setimage"></a>CMFCRibbonRibbonApplicationButton::SetImage

Přiřadí obrázek tlačítku aplikace.

```
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>Parametry

*uiBmpResID*<br/>
[v] ID prostředku obrázku, který se má zobrazit na tlačítku aplikace.

*hBmp*<br/>
[v] Úchyt k rastrové mapě, která se zobrazí na tlačítku aplikace.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete po vytvoření tlačítka přiřadit nové tlačítko aplikace na pásu karet novému obrázku. Tlačítko aplikace se nachází v levém horním rohu okna aplikace.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
