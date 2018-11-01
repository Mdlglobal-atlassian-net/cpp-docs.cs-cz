---
title: Makra zpráv Windows
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: 3ab102ec486af0c7119e8ed28da4898c8beeb293
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582509"
---
# <a name="windows-messages-macros"></a>Makra zpráv Windows

Toto makro předává zprávy okna.

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Slouží k předání zprávy přijímány okno do jiného okna pro zpracování.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="wm_forwardmsg"></a>  WM_FORWARDMSG

Toto makro předává zprávy přijímány okno do jiného okna pro zpracování.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zpráva byla zpracována, hodnotu není.

### <a name="remarks"></a>Poznámky

Použijte WM_FORWARDMSG přeposílat přijatých okno do jiného okna pro zpracování zprávy. LPARAM a WPARAM parametry jsou použity následujícím způsobem:

|Parametr|Použití|
|---------------|-----------|
|WPARAM|Data definovaná uživatelem|
|LPARAM|Ukazatel `MSG` strukturu, která obsahuje informace o zprávě|

### <a name="example"></a>Příklad

V následujícím příkladu `m_hWndOther` představuje ostatní okna, která obdrží tuto zprávu.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
