---
title: Třída CMFCTasksPaneTaskGroup
ms.date: 11/19/2018
f1_keywords:
- CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsBottom
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsCollapsed
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsSpecial
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_lstTasks
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rect
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rectGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_strName
helpviewer_keywords:
- CMFCTasksPaneTaskGroup [MFC], CMFCTasksPaneTaskGroup
- CMFCTasksPaneTaskGroup [MFC], SetACCData
- CMFCTasksPaneTaskGroup [MFC], m_bIsBottom
- CMFCTasksPaneTaskGroup [MFC], m_bIsCollapsed
- CMFCTasksPaneTaskGroup [MFC], m_bIsSpecial
- CMFCTasksPaneTaskGroup [MFC], m_lstTasks
- CMFCTasksPaneTaskGroup [MFC], m_rect
- CMFCTasksPaneTaskGroup [MFC], m_rectGroup
- CMFCTasksPaneTaskGroup [MFC], m_strName
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
ms.openlocfilehash: 4c24eba646bede462a5f3cfb85715278cfa7daee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366259"
---
# <a name="cmfctaskspanetaskgroup-class"></a>Třída CMFCTasksPaneTaskGroup

Třída `CMFCTasksPaneTaskGroup` je pomocná třída používaná ovládacím prvkem [CMFCTasksPane.](../../mfc/reference/cmfctaskspane-class.md) Objekty `CMFCTasksPaneTaskGroup` typu představují *skupinu úkolů*. Skupina úloh je seznam položek, které se v rámci zobrazí v samostatném poli, které má tlačítko sbalit. Pole může mít volitelný titulek (název skupiny). Pokud je skupina sbalena, seznam úkolů není viditelný.

## <a name="syntax"></a>Syntaxe

```
class CMFCTasksPaneTaskGroup : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](#cmfctaskspanetaskgroup)|Vytvoří `CMFCTasksPaneTaskGroup` objekt.|
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|Určuje data usnadnění pro aktuální skupinu úkolů.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|Určuje, zda je skupina úkolů zarovnána k dolnímu konci ovládacího prvku podokna úloh.|
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|Určuje, zda je skupina úkolů sbalena.|
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|Určuje, zda je skupina úkolů *zvláštní.* Rámec zobrazí speciální titulky v jiné barvě.|
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|Obsahuje interní seznam úkolů.|
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|Určuje ohraničovací obdélník titulku skupiny.|
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|Určuje ohraničovací obdélník skupiny.|
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|Určuje název skupiny.|

## <a name="remarks"></a>Poznámky

Následující obrázek znázorňuje rozbalené skupiny úkolů:

![Skupina úkolů, rozbalená](../../mfc/reference/media/nexttaskgrpexpand.png "Skupina úkolů, rozbalená")

Následující obrázek znázorňuje sbalenou skupinu úkolů:

![Sbalená skupina úkolů](../../mfc/reference/media/nexttaskgrpcollapse.png "Sbalená skupina úkolů")

Následující obrázek znázorňuje skupinu úkolů bez titulku:

![Skupina úkolů bez titulku](../../mfc/reference/media/nexttaskgrpnocapt.png "Skupina úkolů bez titulku")

Následující obrázek znázorňuje dvě skupiny úkolů. První skupina úkolů je označena `m_bIsSpecial` jako zvláštní nastavením příznaku TRUE, zatímco druhá skupina úkolů není zvláštní. Všimněte si, jak je titulek pro první skupinu úkolů tmavší než druhá skupina úkolů:

![Zvláštní skupina úkolů](../../mfc/reference/media/nexttaskgrpspecial.png "Zvláštní skupina úkolů")

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneSkupina úloh](../../mfc/reference/cmfctaskspanetaskgroup-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxTasksPane.h

## <a name="cmfctaskspanetaskgroupcmfctaskspanetaskgroup"></a><a name="cmfctaskspanetaskgroup"></a>CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup

Vytvoří `CMFCTasksPaneTaskGroup` objekt.

```
CMFCTasksPaneTaskGroup(
    LPCTSTR lpszName,
    BOOL bIsBottom,
    BOOL bIsSpecial=FALSE,
    BOOL bIsCollapsed=FALSE,
    CMFCTasksPanePropertyPage* pPage=NULL,
    HICON hIcon=NULL);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Určuje název skupiny v titulku skupiny.

*bIsBottom*<br/>
Určuje, zda je skupina zarovnána k dolnímu konci ovládacího prvku podokna úloh.

*bIsZvláštní*<br/>
Určuje, zda je skupina označena jako *zvláštní* a tedy zda je titulek skupiny vyplněn jinou barvou.

*bIsSbalené*<br/>
Určuje, zda je skupina sbalena.

*pStránka*<br/>
Určuje stránku vlastností, ke které tato skupina úkolů patří.

*hIkona*<br/>
Určuje ikonu, která se zobrazí v titulku skupiny.

### <a name="remarks"></a>Poznámky

## <a name="cmfctaskspanetaskgroupm_bisbottom"></a><a name="m_bisbottom"></a>CMFCTasksPaneTaskGroup::m_bIsBottom

Určuje, zda je skupina úkolů zarovnána k dolnímu konci ovládacího prvku podokna úloh.

```
BOOL m_bIsBottom;
```

### <a name="remarks"></a>Poznámky

K dolnímu konci ovládacího prvku podokna úloh lze zarovnat pouze jednu skupinu. Tato skupina úkolů musí být přidána jako poslední. Další informace naleznete v tématu [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).

## <a name="cmfctaskspanetaskgroupm_biscollapsed"></a><a name="m_biscollapsed"></a>CMFCTasksPaneTaskGroup::m_bIsCollapsed

Určuje, zda je skupina úkolů sbalena.

```
BOOL m_bIsCollapsed;
```

### <a name="remarks"></a>Poznámky

Možnost sbalení skupin v podokně úloh můžete povolit nebo zakázat voláním [CMFCTasksPane::EnableGroupCollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse).

## <a name="cmfctaskspanetaskgroupm_bisspecial"></a><a name="m_bisspecial"></a>CMFCTasksPaneTaskGroup::m_bIsSpecial

Určuje, zda je skupina úkolů *zvláštní* a zda má být titulek pro zvláštní skupinu úkolů identifikován jinou barvou.

```
BOOL m_bIsSpecial;
```

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace používá vizuální motiv `m_bIsSpecial` systému Windows XP `DrawThemeBackground` a je FALSE, rozhraní framework volá s příznakem EBP_NORMALGROUPBACKGROUND. Pokud `m_bIsSpecial` je TRUE, `DrawThemeBackground` rozhraní framework volá s příznakem EBP_SPECIALGROUPBACKGROUND.

## <a name="cmfctaskspanetaskgroupm_lsttasks"></a><a name="m_lsttasks"></a>CMFCTasksPaneTaskGroup::m_lstTasks

Obsahuje interní seznam úkolů.

```
CObList m_lstTasks;
```

### <a name="remarks"></a>Poznámky

Chcete-li vyplnit tento seznam, zavolejte [CMFCTasksPane::AddTask](../../mfc/reference/cmfctaskspane-class.md#addtask).

## <a name="cmfctaskspanetaskgroupm_rect"></a><a name="m_rect"></a>CMFCTasksPaneTaskGroup::m_rect

Určuje ohraničovací obdélník titulku skupiny.

```
CRect m_rect;
```

### <a name="remarks"></a>Poznámky

Tato hodnota je automaticky vypočítána rozhraním.

## <a name="cmfctaskspanetaskgroupm_rectgroup"></a><a name="m_rectgroup"></a>CMFCTasksPaneTaskGroup::m_rectGroup

Určuje ohraničovací obdélník skupiny.

```
CRect m_rectGroup;
```

### <a name="remarks"></a>Poznámky

Tato hodnota je vypočítána automaticky rámci.

## <a name="cmfctaskspanetaskgroupm_strname"></a><a name="m_strname"></a>CMFCTasksPaneTaskGroup::m_strName

Určuje název skupiny.

```
CString m_strName;
```

### <a name="remarks"></a>Poznámky

Pokud je tato hodnota prázdná, titulek skupiny se nezobrazí a skupinu nelze sbalit.

## <a name="cmfctaskspanetaskgroupsetaccdata"></a><a name="setaccdata"></a>CMFCTasksPaneTaskGroup::SetACCData

Určuje data usnadnění pro aktuální skupinu úkolů.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
[v] Představuje nadřazené okno aktuální skupiny úkolů.

*Dat*<br/>
[out] Objekt typu, `CAccessibilityData` který je naplněn daty usnadnění aktuální skupiny úkolů.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl parametr *dat* úspěšně naplněn daty usnadnění aktuální skupiny úkolů; jinak NEPRAVDA.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTasksPane – třída](../../mfc/reference/cmfctaskspane-class.md)<br/>
[Třída úloh CMFCTasksPane](../../mfc/reference/cmfctaskspanetask-class.md)<br/>
[CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)
