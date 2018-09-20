---
title: Nccalcsize_params – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- NCCALCSIZE_PARAMS
dev_langs:
- C++
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6290c7600584f3225fee6cf9ed6a0f94373584c8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413702"
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS – struktura

`NCCALCSIZE_PARAMS` Struktura obsahuje informace, že aplikace může použít při zpracování zprávy WM_NCCALCSIZE vypočítat velikost, umístění a platný obsah klientské oblasti okna.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagNCCALCSIZE_PARAMS {
    RECT rgrc[3];
    PWINDOWPOS lppos;
} NCCALCSIZE_PARAMS;
```

#### <a name="parameters"></a>Parametry

*rgrc*<br/>
Určuje pole obdélníků. První obsahuje souřadnice nové okno, které byly přesunuty nebo změně jejich velikosti. Druhá obsahuje souřadnice okna předtím, než bylo přesunutí nebo změně velikosti. Třetí obsahuje souřadnice klientské oblasti okna předtím, než bylo přesunutí nebo změně velikosti. Pokud je okno podřízené okno, souřadnice jsou vzhledem ke klientské oblasti okna nadřazené. Pokud okno je okno nejvyšší úrovně, souřadnice jsou relativní vzhledem k obrazovce.

*lppos*<br/>
Odkazuje [windowpos –](../../mfc/reference/windowpos-structure1.md) strukturu, která obsahuje hodnoty velikost a umístění zadané v operaci, která způsobila k přesunutí nebo změně velikosti okna.

## <a name="requirements"></a>Požadavky

**Záhlaví:** winuser

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

