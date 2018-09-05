---
title: Idispeventsimpleimpl – použití (ATL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a47cef741e9db3237bbc9f6477cdf2863b38e4e3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760367"
---
# <a name="using-idispeventsimpleimpl"></a>Idispeventsimpleimpl – použití

Při použití `IDispEventSimpleImpl` zpracování událostí, budete muset:

- Odvodit třídu z [idispeventsimpleimpl –](../atl/reference/idispeventsimpleimpl-class.md).

- Přidáte mapu jímky událostí do vaší třídy.

- Definování [_atl_func_info –](../atl/reference/atl-func-info-structure.md) struktury popisující události.

- Přidání položky do pomocí mapě událostí jímky [SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) – makro.

- Implementace metody, že máte zájem zpracování.

- Dokáží a zrušíte avízo o zdroji události.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak naložit `DocumentChange` události vyvolané Wordu **aplikace** objektu. Tato událost je definována jako metody na `ApplicationEvents` dispinterface.

Příklad je z [ATLEventHandling ukázka](../visual-cpp-samples.md).  

```cpp
[ uuid(000209F7-0000-0000-C000-000000000046), hidden ]  
dispinterface ApplicationEvents {
properties:
methods:
    [id(0x00000001), restricted, hidden]
    void Startup();

    [id(0x00000002)]
    void Quit();

    [id(0x00000003)]
    void DocumentChange();
};
```

V příkladu `#import` ke generování požadované záhlaví soubory z knihovny typů Wordu. Pokud chcete použít tento příklad s jinými verzemi aplikace Word, musíte zadat správné mso souboru knihovny dll. Například Office 2000 poskytuje mso9.dll a OfficeXP poskytuje mso.dll. Tento kód je jednodušší z stdafx.h:

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

Jediná informace z knihovny typů ve skutečnosti použitý v tomto příkladu je identifikátor CLSID slova `Application` objektu a identifikátor IID `ApplicationEvents` rozhraní. Tyto informace slouží jenom v době kompilace.

Následující kód se zobrazí v Simple.h. Příslušný kód je uvedeno ve komentáře:

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

Následující kód je z Simple.cpp:

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>Viz také

[Zpracování událostí](../atl/event-handling-and-atl.md)   
[Ukázka ATLEventHandling](../visual-cpp-samples.md)

