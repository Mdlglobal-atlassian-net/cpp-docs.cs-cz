---
title: DEVNAMES – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DEVNAMES
dev_langs:
- C++
helpviewer_keywords:
- DEVNAMES [MFC]
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d91a44a38d331a49927d5129c5002eef53c224ad
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077969"
---
# <a name="devnames-structure"></a>DEVNAMES – struktura

`DEVNAMES` Struktura obsahuje řetězce, které identifikují ovladač, zařízení a názvy výstupní port tiskárny.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagDEVNAMES { /* dvnm */
    WORD wDriverOffset;
    WORD wDeviceOffset;
    WORD wOutputOffset;
    WORD wDefault; */* driver,
    device,
    and port-name strings follow wDefault */
} DEVNAMES;
```

#### <a name="parameters"></a>Parametry

*wDriverOffset*<br/>
(Vstup/výstup) Určuje posun ve znacích pro řetězec zakončený hodnotou null, který obsahuje název souboru (bez přípony) ovladače zařízení. Na vstupu se tento řetězec používá k určení tiskárny, kterou chcete zobrazit zpočátku v dialogovém okně.

*wDeviceOffset*<br/>
(Vstup/výstup) Určuje posun v znaků, které mají řetězec zakončený hodnotou null (maximálně 32 bajtů, včetně hodnotu null), který obsahuje název zařízení. Tento řetězec musí být stejný jako `dmDeviceName` člena [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) struktury.

*wOutputOffset*<br/>
(Vstup/výstup) Určuje posun ve znacích pro řetězec zakončený hodnotou null, který obsahuje název zařízení DOS pro střední fyzické výstup (výstupní port).

*wDefault*<br/>
Určuje, zda jsou řetězce součástí `DEVNAMES` struktura určit výchozí tiskárna. Tento řetězec se používá k ověření, že výchozí tiskárna nebyl změněn od poslední operace tisku. Na vstupu, pokud je nastavený příznak DN_DEFAULTPRN, druhé hodnoty v `DEVNAMES` struktury jsou porovnávána s aktuální výchozí tiskárna. Pokud některý z řetězců neshodují, se zobrazí zpráva s upozorněním informující uživatele, který možná bude nutné dokument naformátována. Na výstupu `wDefault` člena se změní pouze v případě, že se zobrazí dialogové okno Nastavení tisku a uživatel vybral tlačítko OK. Příznak DN_DEFAULTPRN je nastaven, pokud byla vybrána výchozí tiskárna. Pokud je vybraný konkrétní tiskárnu, příznak není nastaven. Všechny bity v tento člen jsou vyhrazené pro interní použití pole proceduru dialogového okna Tisk.

## <a name="remarks"></a>Poznámky

`PrintDlg` Funkce používá tyto řetězce inicializace členů v systému definované dialogového okna Tisk. Když uživatel zavře dialogové okno, informace o vybrané tiskárny se vrátí v této struktuře.

## <a name="requirements"></a>Požadavky

**Záhlaví:** commdlg.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)

