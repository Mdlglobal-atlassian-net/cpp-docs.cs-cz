---
title: Makra zpráv Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
dev_langs:
- C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58c9f26b33c3ab2bcdc4e7f0c0a676835da0e3c3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758840"
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
