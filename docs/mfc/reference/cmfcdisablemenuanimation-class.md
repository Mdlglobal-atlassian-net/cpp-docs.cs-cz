---
title: Cmfcdisablemenuanimation – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: 0b0df30d48b2f77d620b00f67d40743445981b66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665033"
---
# <a name="cmfcdisablemenuanimation-class"></a>Cmfcdisablemenuanimation – třída

Zakáže animace rozbalovací nabídky.

## <a name="syntax"></a>Syntaxe

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Vytvoří `CMFCDisableMenuAnimation` objektu.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCDisableMenuAnimation::Restore](#restore)|Obnoví předchozí animace, která rozhraní použité k zobrazení místní nabídky.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|Název|Popis|
|`CMFCDisableMenuAnimation::m_animType`|Ukládá předchozí typ animace rozbalovací nabídky.|

### <a name="remarks"></a>Poznámky

Pomocí této pomocné rutiny třídy dočasně zakázat místní nabídka animace (třeba při zpracování příkazů myš či klávesnice).

A `CMFCDisableMenuAnimation` zakáže rozbalovací nabídky animace průběhu svého životního cyklu objektu. Uloží aktuální typ animace místní nabídky v konstruktoru `m_animType` pole a nastaví aktuální animace typ, který `CMFCPopupMenu::NO_ANIMATION`. Destruktor obnoví předchozí typ animace.

Můžete vytvořit `CMFCDisableMenuAnimation` objekt v zásobníku zakázat místní nabídka animace v rámci jedné funkce. Pokud chcete zakázat místní nabídka animace mezi funkcemi, vytvořte `CMFCDisableMenuAnimation` objektů na haldě a odstraňte ji. Pokud chcete obnovit animace rozbalovací nabídky.

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití zásobníku dočasně zakázat nabídky animace.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Cmfcdisablemenuanimation –](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpopupmenu.h

##  <a name="restore"></a>  CMFCDisableMenuAnimation::Restore

Obnoví předchozí animace, která rozhraní použité k zobrazení místní nabídky.

```
void Restore ();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána metodou `CMFCDisableMenuAnimation` destruktor obnovit předchozí animace, která rozhraní použité k zobrazení místní nabídky.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu – třída](../../mfc/reference/cmfcpopupmenu-class.md)
