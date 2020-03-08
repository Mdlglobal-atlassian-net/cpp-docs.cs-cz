---
title: Makra třídy oken
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: c4617a04c199741b97316122456e417a94275e89
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862959"
---
# <a name="window-class-macros"></a>Makra třídy oken

Tato makra definují nástroje třídy okna.

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Umožňuje zadat název nové třídy okna.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Umožňuje zadat název nové třídy okna a ohraničující třídu, jejíž procedura Window bude tuto novou třídu používat.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Umožňuje zadat název existující třídy okna, na které bude založena nová třída okna.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Umožňuje zadat parametry třídy.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="declare_wnd_class"></a>DECLARE_WND_CLASS

Umožňuje zadat název nové třídy okna. Toto makro umístěte do třídy ovládacího prvku ActiveX knihovny ATL.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
pro Název nové třídy okna. Pokud má hodnotu NULL, knihovna ATL vytvoří název třídy okna.

### <a name="remarks"></a>Poznámky

Používáte-li možnost kompilátoru/Permissive-, DECLARE_WND_CLASS způsobí chybu kompilátoru; místo toho použijte DECLARE_WND_CLASS2.

DECLARE_WND_CLASS umožňuje zadat název nové třídy okna, jejíž informace budou spravovány pomocí [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS definuje novou třídu okna implementací následující statické funkce:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS určuje následující styly pro nové okno:

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS také určuje barvu pozadí výchozího okna. Pomocí makra [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) můžete zadat vlastní styly a barvu pozadí.

[CWindowImpl](cwindowimpl-class.md) používá makro DECLARE_WND_CLASS k vytvoření okna založeného na nové třídě okna. Chcete-li toto chování přepsat, použijte makro [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) nebo Poskytněte vlastní implementaci funkce [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) .

Další informace o použití systému Windows v knihovně ATL naleznete v článku [třídy okna ATL](../../atl/atl-window-classes.md).

##  <a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2

(Visual Studio 2017) Podobně jako u DECLARE_WND_CLASS, ale se speciálním parametrem, který brání chybě závislého názvu při kompilování s možností/Permissive-.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
pro Název nové třídy okna. Pokud má hodnotu NULL, knihovna ATL vytvoří název třídy okna.

*EnclosingClass*<br/>
pro Název třídy okna, která obklopuje novou třídu okna. Nemůže mít hodnotu NULL.

### <a name="remarks"></a>Poznámky

Pokud používáte možnost/Permissive-, DECLARE_WND_CLASS způsobí chybu kompilace, protože obsahuje závislý název. DECLARE_WND_CLASS2 vyžaduje explicitní pojmenování třídy, ve které se toto makro používá, a nezpůsobuje chybu pod příznakem/Permissive-.
V opačném případě je toto makro stejné jako [DECLARE_WND_CLASS](#declare_wnd_class).

##  <a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS

Umožňuje zadat parametry třídy. Toto makro umístěte do třídy ovládacího prvku ActiveX knihovny ATL.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
pro Název třídy okna, která bude *OrigWndClassName*supertřída. Pokud má hodnotu NULL, knihovna ATL vytvoří název třídy okna.

*OrigWndClassName*<br/>
pro Název existující třídy okna.

### <a name="remarks"></a>Poznámky

Toto makro umožňuje zadat název třídy okna, která bude mít existující třídu okna. [CWndClassInfo](cwndclassinfo-class.md) spravuje informace o supertřídě.

DECLARE_WND_SUPERCLASS implementuje následující statickou funkci:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Ve výchozím nastavení [CWindowImpl](cwindowimpl-class.md) používá makro [DECLARE_WND_CLASS](#declare_wnd_class) k vytvoření okna založeného na nové třídě okna. Zadáním DECLARE_WND_SUPERCLASS makra v třídě odvozené `CWindowImpl`bude Třída okna založena na stávající třídě, ale bude použita procedura okna. Tato technika se nazývá "podtříd".

Kromě použití makra DECLARE_WND_CLASS a DECLARE_WND_SUPERCLASS můžete funkci [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) přepsat vlastní implementací.

Další informace o použití systému Windows v knihovně ATL naleznete v článku [třídy okna ATL](../../atl/atl-window-classes.md).

##  <a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX

Umožňuje zadat název existující třídy okna, na které bude založena nová třída okna. Toto makro umístěte do třídy ovládacího prvku ActiveX knihovny ATL.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
pro Název nové třídy okna. Pokud má hodnotu NULL, knihovna ATL vytvoří název třídy okna.

*řez*<br/>
pro Styl okna

*štětec*<br/>
pro Barva pozadí okna

### <a name="remarks"></a>Poznámky

Toto makro umožňuje zadat parametry třídy nové třídy okna, jejichž informace budou spravovány pomocí [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS_EX definuje novou třídu okna implementací následující statické funkce:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Chcete-li použít výchozí styly a barvu pozadí, použijte makro [DECLARE_WND_CLASS](#declare_wnd_class) . Další informace o použití systému Windows v knihovně ATL naleznete v článku [třídy okna ATL](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Viz také

[Makr](atl-macros.md)
