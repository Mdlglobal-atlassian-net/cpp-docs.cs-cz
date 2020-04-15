---
title: Třída CMFCDisableMenuAnimation
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: 990f41d2dfa6491d246797322ee275c9648d52a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367573"
---
# <a name="cmfcdisablemenuanimation-class"></a>Třída CMFCDisableMenuAnimation

Zakáže animaci rozbalovací nabídky.

## <a name="syntax"></a>Syntaxe

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Name (Název)|Popis|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Vytvoří `CMFCDisableMenuAnimation` objekt.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name (Název)|Popis|
|[CMFCDisableMenuAnimation::Obnovit](#restore)|Obnoví předchozí animaci, kterou rámec slouží k zobrazení rozbalovací nabídky.|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|Name (Název)|Popis|
|`CMFCDisableMenuAnimation::m_animType`|Ukládá předchozí typ animace rozbalovací nabídky.|

### <a name="remarks"></a>Poznámky

Pomocí této pomocné třídy můžete dočasně zakázat animaci rozbalovací nabídky (například při zpracování příkazů myši nebo klávesnice).

Objekt `CMFCDisableMenuAnimation` zakáže animaci rozbalovací nabídky během jeho životnosti. Konstruktor uloží aktuální typ animace rozbalovací `m_animType` nabídky do pole a `CMFCPopupMenu::NO_ANIMATION`nastaví aktuální typ animace na . Destruktor obnoví předchozí typ animace.

Můžete vytvořit `CMFCDisableMenuAnimation` objekt v zásobníku zakázat animace rozbalovací nabídky v rámci jedné funkce. Pokud chcete zakázat animaci rozbalovací `CMFCDisableMenuAnimation` nabídky mezi funkcemi, vytvořte objekt na haldě a odstraňte jej, pokud chcete obnovit animaci rozbalovací nabídky.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít zásobník udočasně zakázat animaci nabídky.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpopupmenu.h

## <a name="cmfcdisablemenuanimationrestore"></a><a name="restore"></a>CMFCDisableMenuAnimation::Obnovit

Obnoví předchozí animaci, kterou rámec slouží k zobrazení rozbalovací nabídky.

```
void Restore ();
```

### <a name="remarks"></a>Poznámky

Tato metoda je `CMFCDisableMenuAnimation` volána destruktorem k obnovení předchozí animace, která framework slouží k zobrazení rozbalovací nabídky.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída cmfcpopupmenu](../../mfc/reference/cmfcpopupmenu-class.md)
