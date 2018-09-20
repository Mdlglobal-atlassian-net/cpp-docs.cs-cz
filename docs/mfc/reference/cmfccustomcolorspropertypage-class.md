---
title: Cmfccustomcolorspropertypage – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
dev_langs:
- C++
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 876d361d64681568ba22ba84fcc53cda08199703
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434931"
---
# <a name="cmfccustomcolorspropertypage-class"></a>Cmfccustomcolorspropertypage – třída

Představuje stránku vlastností, která můžete vybrat vlastní barvy v dialogovém okně barev.

## <a name="syntax"></a>Syntaxe

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|`CMFCCustomColorsPropertyPage::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCCustomColorsPropertyPage::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCCustomColorsPropertyPage::Setup](#setup)|Nastaví barvu součástí na stránce vlastností.|

### <a name="remarks"></a>Poznámky

`CMFCColorDialog` Třída používá tuto třídu zobrazíte na stránce vlastností vlastní barvy. Další informace o `CMFCColorDialog`, naleznete v tématu [cmfccolordialog – třída](../../mfc/reference/cmfccolordialog-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCCustomColorsPropertyPage` objektu a nastavit barvu součástí na stránce vlastností.

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage –](../../mfc/reference/cpropertypage-class.md)

[Cmfccustomcolorspropertypage –](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcustomcolorspropertypage.h

##  <a name="setup"></a>  CMFCCustomColorsPropertyPage::Setup

Nastaví barvu součástí na stránce vlastností.

```
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*R*|[in] Červené složku hodnoty RGB.|
|*G*|[in] Zelená složku hodnoty RGB.|
|*B*|[in] Modrou složku hodnoty RGB.|

### <a name="remarks"></a>Poznámky

Tato metoda aktualizuje aktuální RGB a přidružené HLS (hue, světlosti a sytost) hodnot barev stránky vlastností. [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) metoda volá tuto metodu při rozhraní inicializuje dialogové okno barev nebo uživatel stiskne levé tlačítko myši. Další informace o `CMFCColorDialog`, naleznete v tématu [cmfccolordialog – třída](../../mfc/reference/cmfccolordialog-class.md).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog – třída](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage – třída](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
