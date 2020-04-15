---
title: Třída CSimpleDialog
ms.date: 11/04/2016
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
ms.openlocfilehash: 345372d71ad96a74bb0ae6dd7e89bdf0724cd822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330824"
---
# <a name="csimpledialog-class"></a>Třída CSimpleDialog

Tato třída implementuje základní modální dialogové okno.

## <a name="syntax"></a>Syntaxe

```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>
class CSimpleDialog : public CDialogImplBase
```

#### <a name="parameters"></a>Parametry

*t_wDlgTemplateID*

ID prostředku prostředku šablony dialogu.

*t_bCenter*<br/>
TRUE, pokud má být objekt dialogového okna vycentrován v okně vlastníka; jinak FALSE.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleDialog::DoModální](#domodal)|Vytvoří modální dialogové okno.|

## <a name="remarks"></a>Poznámky

Implementuje modální dialogové okno se základními funkcemi. `CSimpleDialog`poskytuje podporu pouze pro běžné ovládací prvky systému Windows. Chcete-li vytvořit a zobrazit modální dialogové okno, vytvořte instanci této třídy a zadejte název existující šablony prostředků pro dialogové okno. Objekt dialogového okna se zavře, když uživatel klepne na libovolný ovládací prvek s předdefinovanou hodnotou (například IDOK nebo IDCANCEL).

`CSimpleDialog`umožňuje vytvářet pouze modální dialogová okna. `CSimpleDialog`Poskytuje proceduru dialogového okna, která používá výchozí mapování zpráv k přesměrování zpráv na příslušné obslužné rutiny.

Další informace naleznete [v tématu Implementace dialogového okna.](../../atl/implementing-a-dialog-box.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CDialogImplBase`

`CSimpleDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="csimpledialogdomodal"></a><a name="domodal"></a>CSimpleDialog::DoModální

Vyvolá modální dialogové okno a vrátí výsledek dialogového okna po dokončení.

```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Úchyt pro nadřazený dialogový dialog. Pokud není k dispozici žádná hodnota, nadřazený je nastaven na aktuální aktivní okno.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrácená hodnota je ID prostředku ovládacího prvku, který zamítl dialogové okno.

Pokud funkce selže, vrácená hodnota je -1. Chcete-li získat rozšířené `GetLastError`informace o chybě, volejte .

### <a name="remarks"></a>Poznámky

Tato metoda zpracovává všechny interakce s uživatelem, zatímco dialogové okno je aktivní. To je to, co dělá dialogové okno modální; to znamená, že uživatel nemůže pracovat s jinými okny, dokud není dialogové okno uzavřeno.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
