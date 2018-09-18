---
title: CSimpleDialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f58efa7b7ba5c0452f2418a2dbbc27c94eedaca6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087952"
---
# <a name="csimpledialog-class"></a>CSimpleDialog – třída

Tato třída implementuje základní modální dialogové okno.

## <a name="syntax"></a>Syntaxe

```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>
class CSimpleDialog : public CDialogImplBase
```

#### <a name="parameters"></a>Parametry

*t_wDlgTemplateID*

ID prostředku šablony prostředku dialogového okna.

*t_bCenter*<br/>
Hodnota TRUE, pokud objektu dialogového okna je zarovnaný na střed na okno vlastníka. v opačném případě FALSE.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSimpleDialog::DoModal](#domodal)|Vytvoří modální dialogové okno.|

## <a name="remarks"></a>Poznámky

Implementuje modální dialogové okno se základní funkčností. `CSimpleDialog` poskytuje podporu pro Windows běžné ovládací prvky pouze. Vytvoření a zobrazení modálního dialogového okna, vytvoření instance této třídy, že zadáte název existující šablony prostředků pro dialogové okno. Pole objektu dialogového okna zavře, když uživatel klikne libovolný ovládací prvek s hodnotou předem definovaných (například IDOK nebo IDCANCEL).

`CSimpleDialog` Umožňuje vytvořit pouze modálních dialogových oken. `CSimpleDialog` poskytuje pole proceduru dialogového okna, který používá výchozí mapování zpráv ke směrování zpráv do příslušné obslužné rutiny.

Zobrazit [implementace dialogového okna](../../atl/implementing-a-dialog-box.md) Další informace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CDialogImplBase`

`CSimpleDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="domodal"></a>  CSimpleDialog::DoModal

Vyvolá modální dialogové okno a vrátí výsledek dialogového okna, až budete hotovi.

```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač na nadřazený prvek dialogového okna. Pokud se nezadá žádná hodnota, nadřazené nastavená na aktuálně aktivní okno.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrácená hodnota je ID prostředku ovládacího prvku, který se zavře dialogové okno.

Pokud funkce selže, vrácená hodnota je -1. Chcete-li získat rozšířené informace o chybě, volejte `GetLastError`.

### <a name="remarks"></a>Poznámky

Tato metoda zpracovává všechny interakce s uživatelem, dialogové okno je aktivní. Toto je kvůli tomu dialogové okno modální; To znamená uživatel nemohou komunikovat s ostatní okna, dokud není zavřena dialogových oken.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
