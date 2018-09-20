---
title: Windowplacement – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WINDOWPLACEMENT
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPLACEMENT structure [MFC]
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b163d93de22d313d72ca5dbfd384788077ae1b01
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447270"
---
# <a name="windowplacement-structure"></a>WINDOWPLACEMENT – struktura

`WINDOWPLACEMENT` Struktura obsahuje informace o umístění okna na obrazovce.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagWINDOWPLACEMENT {     /* wndpl */
    UINT length;
    UINT flags;
    UINT showCmd;
    POINT ptMinPosition;
    POINT ptMaxPosition;
    RECT rcNormalPosition;
} WINDOWPLACEMENT;
```

#### <a name="parameters"></a>Parametry

*Délka*<br/>
Určuje délku v bajtech struktury.

*příznaky*<br/>
Určuje příznaky, které určují umístění minimalizované okno a metodu, pomocí kterého se obnoví okno. Tento člen může být jedno nebo obě z následujících příznaků:

- WPF_SETMINPOSITION Určuje, že lze zadat x - a y pozice minimalizované okno. Musí být tento příznak zadán, pokud souřadnice jsou nastaveny v `ptMinPosition` člena.

- WPF_RESTORETOMAXIMIZED Určuje, že okno obnovené budou maximalizovat, bez ohledu na to, zda byl maximalizované předtím, než bylo minimalizováno. Toto nastavení je platný pouze při příštím spuštění okna se obnoví. Výchozí chování obnovení nezmění. Tento příznak je platný pouze v případě, že je zadána hodnota SW_SHOWMINIMIZED `showCmd` člena.

*showCmd*<br/>
Určuje aktuální stav zobrazení okna. Tento člen může být jeden z následujících hodnot:

- SW_HIDE skryje okno a předá do další okno aktivace.

- SW_MINIMIZE minimalizuje určené okno a aktivuje okno nejvyšší úrovně v seznamu v systému.

- Aktivuje SW_RESTORE a zobrazí okno. Pokud v okně je minimalizovaná nebo maximalizované, Windows jej obnoví na jeho původní velikost a umístění (stejné jako SW_SHOWNORMAL).

- SW_SHOW aktivuje okně a zobrazí jej v jeho aktuální velikost a umístění.

- SW_SHOWMAXIMIZED aktivuje okno a zobrazí ho jako maximalizovaném okně.

- SW_SHOWMINIMIZED aktivuje okno a zobrazí ho jako ikona.

- SW_SHOWMINNOACTIVE zobrazí jako ikonu časové období. V okně, která je aktuálně aktivní zůstává aktivní.

- SW_SHOWNA zobrazí okno v jejím aktuálním stavu. V okně, která je aktuálně aktivní zůstává aktivní.

- SW_SHOWNOACTIVATE zobrazí okno v jeho aktuální velikost a umístění. V okně, která je aktuálně aktivní zůstává aktivní.

- Aktivuje SW_SHOWNORMAL a zobrazí okno. Pokud v okně je minimalizovaná nebo maximalizované, Windows jej obnoví na jeho původní velikost a umístění (stejné jako SW_RESTORE).

*ptMinPosition*<br/>
Určuje umístění levého horního rohu okna. Pokud minimalizované okno.

*ptMaxPosition*<br/>
Určuje umístění levého horního rohu okna při maximalizované okno.

*rcNormalPosition*<br/>
Určuje souřadnice okna, když je okno v normální pozice (obnovené).

## <a name="requirements"></a>Požadavky

**Záhlaví:** winuser

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)

