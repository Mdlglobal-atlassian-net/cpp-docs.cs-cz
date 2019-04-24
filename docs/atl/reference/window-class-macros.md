---
title: Makra třídy okna
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: c4617a04c199741b97316122456e417a94275e89
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197171"
---
# <a name="window-class-macros"></a>Makra třídy okna

Tato makra definují nástroje třídy okna.

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Můžete zadat název nové třídy okna.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Můžete zadat název nové třídy okna a jejichž proceduru okna používat nové třídy nadřazené třídy.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Můžete zadat název existující třídy okna, na kterém bude na základě nové třídy okna.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Umožňuje zadat parametry třídy.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="declare_wnd_class"></a>  DECLARE_WND_CLASS

Můžete zadat název nové třídy okna. Toto makro umístěte ovládací prvek ActiveX knihovny ATL třídy ovládacího prvku.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
[in] Název nové třídy okna. Pokud má hodnotu NULL, ATL vygeneruje název třídy okna.

### <a name="remarks"></a>Poznámky

Pokud použijete možnost /permissive-compiler, pak DECLARE_WND_CLASS způsobí chybu kompilátoru; Místo toho použijte DECLARE_WND_CLASS2.

DECLARE_WND_CLASS můžete zadat název nové třídy okna, jehož informace se spravovanou aplikací služby [cwndclassinfo –](cwndclassinfo-class.md). DECLARE_WND_CLASS definuje novou třídu okna díky implementaci následující statické funkce:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS určuje následující styly pro nové okno:

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS také určuje barvu pozadí okna výchozí. Použití [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) – makro poskytovat vlastní styly a barva pozadí.

[CWindowImpl](cwindowimpl-class.md) používá makro DECLARE_WND_CLASS vytvořit okno založené na nové třídě okna. Chcete-li toto chování přepsat, použijte [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) – makro, nebo Poskytněte vlastní implementaci [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) funkce.

Další informace o používání oken v ATL, najdete v článku [tříd oken ATL](../../atl/atl-window-classes.md).

##  <a name="declare_wnd_class2"></a>  DECLARE_WND_CLASS2

(Visual Studio 2017) Podobně jako DECLARE_WND_CLASS, ale se speciálním parametrem, který předchází název závislý chyby při kompilaci s /permissive-option.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
[in] Název nové třídy okna. Pokud má hodnotu NULL, ATL vygeneruje název třídy okna.

*EnclosingClass*<br/>
[in] Název třídy okna, která vloží nové třídy okna. Nemůže mít hodnotu NULL.

### <a name="remarks"></a>Poznámky

Pokud používáte /permissive-option, pak DECLARE_WND_CLASS způsobí chybu kompilace protože obsahuje název závislý. DECLARE_WND_CLASS2 vyžaduje, abyste explicitní název třídy, že toto makro je používán a nezpůsobí chybu v části /permissive-flag.
V opačném případě toto makro je stejné jako [DECLARE_WND_CLASS](#declare_wnd_class).

##  <a name="declare_wnd_superclass"></a>  DECLARE_WND_SUPERCLASS

Umožňuje zadat parametry třídy. Toto makro umístěte ovládací prvek ActiveX knihovny ATL třídy ovládacího prvku.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
[in] Název okna třídy této nadřazené třídy bude *OrigWndClassName*. Pokud má hodnotu NULL, ATL vygeneruje název třídy okna.

*OrigWndClassName*<br/>
[in] Název existující třídy okna.

### <a name="remarks"></a>Poznámky

Toto makro můžete zadat název třídy okna, která bude supertřídě existující třídy okna. [Cwndclassinfo –](cwndclassinfo-class.md) spravuje informace nadřazené třídy.

DECLARE_WND_SUPERCLASS implementuje následující statické funkce:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Ve výchozím nastavení [CWindowImpl](cwindowimpl-class.md) používá [DECLARE_WND_CLASS](#declare_wnd_class) – makro vytvořit okno založené na nové třídě okna. Zadáním DECLARE_WND_SUPERCLASS – makro v `CWindowImpl`-odvozené třídy, třídu okna bude vycházet z existující třídy, ale bude používat vaše proceduru okna. Tato technika se nazývá superclassing.

Kromě použití maker DECLARE_WND_CLASS a DECLARE_WND_SUPERCLASS, můžete přepsat [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) funkci s vlastní implementaci.

Další informace o používání oken v ATL, najdete v článku [tříd oken ATL](../../atl/atl-window-classes.md).

##  <a name="declare_wnd_class_ex"></a>  DECLARE_WND_CLASS_EX

Můžete zadat název existující třídy okna, na kterém bude na základě nové třídy okna. Toto makro umístěte ovládací prvek ActiveX knihovny ATL třídy ovládacího prvku.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
[in] Název nové třídy okna. Pokud má hodnotu NULL, ATL vygeneruje název třídy okna.

*style*<br/>
[in] Styl okna.

*bkgnd*<br/>
[in] Barva pozadí okna.

### <a name="remarks"></a>Poznámky

Toto makro umožňuje zadat parametry třídy nové třídy okna, jehož informace bude spravovat [cwndclassinfo –](cwndclassinfo-class.md). DECLARE_WND_CLASS_EX definuje novou třídu okna díky implementaci následující statické funkce:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Pokud chcete použít výchozí styly a barva pozadí, použijte [DECLARE_WND_CLASS](#declare_wnd_class) – makro. Další informace o používání oken v ATL, najdete v článku [tříd oken ATL](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Viz také:

[Makra](atl-macros.md)
