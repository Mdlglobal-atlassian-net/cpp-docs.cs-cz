---
title: Makra zpráv systému Windows
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: a5a6d45c64d6123128ae362c1ef5643392439f41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329414"
---
# <a name="windows-messages-macros"></a>Makra zpráv systému Windows

Toto makro předá zprávy okna.

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Slouží k předání zprávy přijaté oknem do jiného okna ke zpracování.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="wm_forwardmsg"></a><a name="wm_forwardmsg"></a>WM_FORWARDMSG

Toto makro předá zprávu přijatou oknem do jiného okna ke zpracování.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla zpráva zpracována, nula, pokud ne.

### <a name="remarks"></a>Poznámky

Pomocí WM_FORWARDMSG přeposlat zprávu přijatou oknem do jiného okna ke zpracování. Parametry LPARAM a WPARAM se používají takto:

|Parametr|Využití|
|---------------|-----------|
|WPARAM|Data definovaná uživatelem|
|Lparam|Ukazatel na `MSG` strukturu, která obsahuje informace o zprávě|

### <a name="example"></a>Příklad

V následujícím příkladu představuje další okno, `m_hWndOther` které obdrží tuto zprávu.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
