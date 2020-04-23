---
title: CMFCCustomColorsPropertyPage – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: 468d947947fc89f9ebc832cda722d854bb8b4be2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752474"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage – třída

Představuje stránku vlastností, která může vybrat vlastní barvy v dialogovém okně barvy.

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
|`CMFCCustomColorsPropertyPage::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCCustomColorsPropertyPage::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCCustomColorsPropertyPage::Instalace](#setup)|Nastaví barevné komponenty stránky vlastností.|

### <a name="remarks"></a>Poznámky

Třída `CMFCColorDialog` používá tuto třídu k zobrazení vlastní stránky vlastností color. Další informace `CMFCColorDialog`naleznete v tématu [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCCustomColorsPropertyPage` vytvořit objekt a nastavit barevné komponenty stránky vlastností.

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[Stránka CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CmFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcustomcolorspropertypage.h

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a>CMFCCustomColorsPropertyPage::Instalace

Nastaví barevné komponenty stránky vlastností.

```cpp
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*R*|[v] Červená součást hodnoty RGB.|
|*G*|[v] Zelená součást hodnoty RGB.|
|*B*|[v] Modrá součást hodnoty RGB.|

### <a name="remarks"></a>Poznámky

Tato metoda aktualizuje aktuální RGB a přidružené HODNOTY barev HLS (odstín, světlost a sytost) stránky vlastností. Metoda [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) volá tuto metodu, když rozhraní inicializuje dialogové okno barva nebo uživatel stiskne levé tlačítko myši. Další informace `CMFCColorDialog`naleznete v tématu [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage – třída](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
