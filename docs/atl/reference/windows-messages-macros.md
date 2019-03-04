---
title: Windows Messages Macros
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: 7bb5e2fa265c3a5dcabcc16d8343d5b86a4aaf42
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273908"
---
# <a name="windows-messages-macros"></a>Windows Messages Macros

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

## <a name="see-also"></a>Viz také:

[Makra](../../atl/reference/atl-macros.md)
