---
title: Makra třídy oken
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: 18c0912c506bc52421b18d36346204b557c0fc5c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325730"
---
# <a name="window-class-macros"></a>Makra třídy oken

Tato makra definují nástroje třídy oken.

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Umožňuje zadat název nové třídy okna.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Umožňuje zadat název nové třídy okna a ohraničující třídy, jejíž procedura okna bude nová třída používat.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Umožňuje zadat název existující třídy okna, na které bude založena nová třída okna.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Umožňuje zadat parametry třídy.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="declare_wnd_class"></a><a name="declare_wnd_class"></a>DECLARE_WND_CLASS

Umožňuje zadat název nové třídy okna. Umístěte toto makro do třídy řízení activex atl ovládacího prvku.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Parametry

*Název _WndClass*<br/>
[v] Název nové třídy okna. Pokud null, ATL vygeneruje název třídy okna.

### <a name="remarks"></a>Poznámky

Pokud používáte /tolerantní- kompilátor možnost, pak DECLARE_WND_CLASS způsobí chybu kompilátoru; místo toho použijte DECLARE_WND_CLASS2.

DECLARE_WND_CLASS umožňuje zadat název nové třídy okna, jejíž informace budou spravovány [cWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS definuje novou třídu okna implementací následující statické funkce:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS určuje následující styly pro nové okno:

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS také určuje barvu pozadí výchozího okna. Pomocí [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) makra můžete zadat vlastní styly a barvu pozadí.

[CWindowImpl](cwindowimpl-class.md) používá DECLARE_WND_CLASS makro k vytvoření okna na základě nové třídy okna. Chcete-li toto chování přepsat, použijte [makro DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) nebo zadejte vlastní implementaci funkce [GetWndClassInfo.](cwindowimpl-class.md#getwndclassinfo)

Další informace o použití oken v atl naleznete v článku [Třídy oken ATL](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class2"></a><a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2

(Visual Studio 2017) Podobné DECLARE_WND_CLASS, ale s extra parametr, který se vyhýbá chybě závislého názvu při kompilaci s /tolerantní- možnost.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Parametry

*Název _WndClass*<br/>
[v] Název nové třídy okna. Pokud null, ATL vygeneruje název třídy okna.

*Ohraničujícíclass*<br/>
[v] Název třídy okna, která obklopuje novou třídu okna. Nemůže být null.

### <a name="remarks"></a>Poznámky

Pokud používáte /tolerantní- možnost, pak DECLARE_WND_CLASS způsobí chybu kompilace, protože obsahuje závislý název. DECLARE_WND_CLASS2 vyžaduje, abyste explicitně pojmenovat třídu, ve které se toto makro používá, a nezpůsobuje chybu pod příznakem /tolerantní.
V opačném případě je toto makro shodné s [DECLARE_WND_CLASS](#declare_wnd_class).

## <a name="declare_wnd_superclass"></a><a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS

Umožňuje zadat parametry třídy. Umístěte toto makro do třídy řízení activex atl ovládacího prvku.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Parametry

*Název _WndClass*<br/>
[v] Název třídy okna, která bude nadtřídy *OrigWndClassName*. Pokud null, ATL vygeneruje název třídy okna.

*Název origWndClass*<br/>
[v] Název existující třídy okna.

### <a name="remarks"></a>Poznámky

Toto makro umožňuje zadat název třídy okna, která bude nadřazenou existující třídu okna. [CWndClassInfo](cwndclassinfo-class.md) spravuje informace nadřazené třídy.

DECLARE_WND_SUPERCLASS implementuje následující statickou funkci:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Ve výchozím nastavení [CWindowImpl](cwindowimpl-class.md) používá [makro DECLARE_WND_CLASS](#declare_wnd_class) k vytvoření okna založeného na nové třídě okna. Zadáním DECLARE_WND_SUPERCLASS makro v `CWindowImpl`odvozené třídě, třída okna bude založena na existující třídě, ale použije proceduru okna. Tato technika se nazývá superclassing.

Kromě použití DECLARE_WND_CLASS a DECLARE_WND_SUPERCLASS makra můžete přepsat funkci [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) vlastní implementací.

Další informace o použití oken v atl naleznete v článku [Třídy oken ATL](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class_ex"></a><a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX

Umožňuje zadat název existující třídy okna, na které bude založena nová třída okna. Umístěte toto makro do třídy řízení activex atl ovládacího prvku.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Parametry

*Název _WndClass*<br/>
[v] Název nové třídy okna. Pokud null, ATL vygeneruje název třídy okna.

* – styl*<br/>
[v] Styl okna.

*bkgnd*<br/>
[v] Barva pozadí okna.

### <a name="remarks"></a>Poznámky

Toto makro umožňuje zadat parametry třídy nové třídy okna, jejíž informace budou spravovány [společností CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS_EX definuje novou třídu okna implementací následující statické funkce:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Pokud chcete použít výchozí styly a barvu pozadí, použijte [DECLARE_WND_CLASS](#declare_wnd_class) makro. Další informace o použití oken v atl naleznete v článku [Třídy oken ATL](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Viz také

[Makra](atl-macros.md)
