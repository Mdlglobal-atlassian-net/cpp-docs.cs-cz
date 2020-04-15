---
title: Třída CWndClassInfo
ms.date: 11/04/2016
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
ms.openlocfilehash: 01706bf61c3b977c28998325ece68724cfbc7452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330328"
---
# <a name="cwndclassinfo-class"></a>Třída CWndClassInfo

Tato třída poskytuje metody pro registraci informací pro třídu okna.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CWndClassInfo
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|[Zaregistrovat](#register)|Zaregistruje třídu okna.|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|[m_atom](#m_atom)|Jednoznačně identifikuje registrovanou třídu okna.|
|[m_bSystemCursor](#m_bsystemcursor)|Určuje, zda prostředek kurzoru odkazuje na systémový kurzor nebo kurzor obsažený v prostředku modulu.|
|[m_lpszCursorID](#m_lpszcursorid)|Určuje název prostředku kurzoru.|
|[m_lpszOrigName](#m_lpszorigname)|Obsahuje název existující třídy okna.|
|[m_szAutoName](#m_szautoname)|Obsahuje název třídy okna generovaný atl.|
|[m_wc](#m_wc)|Udržuje informace o třídě `WNDCLASSEX` okna ve struktuře.|
|[pWndProc](#pwndproc)|Odkazuje na proceduru okna existující třídy okna.|

## <a name="remarks"></a>Poznámky

`CWndClassInfo`spravuje informace o třídě okna. Obvykle se `CWndClassInfo` používá prostřednictvím jednoho ze tří maker, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX nebo DECLARE_WND_SUPERCLASS, jak je popsáno v následující tabulce:

|Makro|Popis|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`zaregistruje informace pro novou třídu okna.|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`zaregistruje informace pro novou třídu okna, včetně parametrů třídy.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`registruje informace pro třídu okna, která je založena na existující třídě, ale používá jinou proceduru okna. Tato technika se nazývá superclassing.|

Ve výchozím nastavení [CWindowImpl](../../atl/reference/cwindowimpl-class.md) obsahuje `DECLARE_WND_CLASS` makro k vytvoření okna na základě nové třídy okna. DECLARE_WND_CLASS poskytuje výchozí styly a barvu pozadí pro ovládací prvek. Pokud chcete zadat styl a barvu pozadí sami, `CWindowImpl` odvodit třídu z a zahrnout DECLARE_WND_CLASS_EX makro v definici třídy.

Pokud chcete vytvořit okno založené na existující třídě okna, `CWindowImpl` odvodit třídu z a zahrnout DECLARE_WND_SUPERCLASS makro v definici třídy. Příklad:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

Další informace o třídách oken naleznete v tématu [Window Classes](/windows/win32/winmsg/window-classes) v sadě Windows SDK.

Další informace o použití oken v atl naleznete v článku [Třídy oken ATL](../../atl/atl-window-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="cwndclassinfom_atom"></a><a name="m_atom"></a>CWndClassInfo::m_atom

Obsahuje jedinečný identifikátor pro registrovanou třídu okna.

```
ATOM m_atom;
```

## <a name="cwndclassinfom_bsystemcursor"></a><a name="m_bsystemcursor"></a>CWndClassInfo::m_bSystemCursor

Pokud true, prostředek kurzor systému se načte při registraci třídy okna.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Poznámky

V opačném případě bude načten prostředek kurzoru obsažený v modulu.

`CWndClassInfo`používá `m_bSystemCursor` pouze v [případě, že](window-class-macros.md#declare_wnd_class) je zadán a DECLARE_WND_CLASS (výchozí v [CWindowImpl)](../../atl/reference/cwindowimpl-class.md)nebo [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makro. V tomto `m_bSystemCursor` případě je inicializovánna na HODNOTU TRUE. Další informace naleznete v přehledu [CWndClassInfo.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinfom_lpszcursorid"></a><a name="m_lpszcursorid"></a>CWndClassInfo::m_lpszCursorID

Určuje buď název prostředku kurzoru nebo identifikátor prostředku ve slově nižšího řádu a nulu ve slově nejvyššího řádu.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Poznámky

Když je zaregistrována třída okna, popisovač kurzoru identifikovaného je `m_lpszCursorID` načten a uložen [m_wc](#m_wc).

`CWndClassInfo`používá `m_lpszCursorID` pouze v [případě, že](window-class-macros.md#declare_wnd_class) je zadán a DECLARE_WND_CLASS (výchozí v [CWindowImpl)](../../atl/reference/cwindowimpl-class.md)nebo [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makro. V tomto `m_lpszCursorID` případě je inicializován a IDC_ARROW. Další informace naleznete v přehledu [CWndClassInfo.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinfom_lpszorigname"></a><a name="m_lpszorigname"></a>CWndClassInfo::m_lpszOrigName

Obsahuje název existující třídy okna.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Poznámky

`CWndClassInfo`používá `m_lpszOrigName` pouze v případě, že do definice třídy zahrnete [makro DECLARE_WND_SUPERCLASS.](window-class-macros.md#declare_wnd_superclass) V tomto `CWndClassInfo` případě zaregistruje třídu okna na `m_lpszOrigName`základě třídy pojmenované . Další informace naleznete v přehledu [CWndClassInfo.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinfom_szautoname"></a><a name="m_szautoname"></a>CWndClassInfo::m_szAutoName

Obsahuje název třídy okna.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Poznámky

`CWndClassInfo`používá `m_szAutoName` pouze v případě, `WndClassName` že je parametr NULL předán, aby byl parametr [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) nebo [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). Atl vytvoří název při registraci třídy okna.

## <a name="cwndclassinfom_wc"></a><a name="m_wc"></a>CWndClassInfo::m_wc

Udržuje informace o třídě okna ve struktuře [WNDCLASSEX.](/windows/win32/api/winuser/ns-winuser-wndclassexw)

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Poznámky

Pokud jste zadali [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) `m_wc` nebo [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makro, obsahuje informace o nové třídě okna.

Pokud jste zadali [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro, `m_wc` obsahuje informace o nadřazené třídy – třída okna, která je založena na existující třídy, ale používá jiný postup okna. [m_lpszOrigName](#m_lpszorigname) a [pWndProc](#pwndproc) uložit název existující třídy okna a proceduru okna.

## <a name="cwndclassinfopwndproc"></a><a name="pwndproc"></a>CWndClassInfo::pWndProc

Odkazuje na proceduru okna existující třídy okna.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Poznámky

`CWndClassInfo`používá `pWndProc` pouze v případě, že do definice třídy zahrnete [makro DECLARE_WND_SUPERCLASS.](window-class-macros.md#declare_wnd_superclass) V tomto `CWndClassInfo` případě zaregistruje třídu okna, která je založena na existující třídě, ale používá jinou proceduru okna. Procedura okna existující třídy okna `pWndProc`je uložena v aplikaci . Další informace naleznete v přehledu [CWndClassInfo.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinforegister"></a><a name="register"></a>CWndClassInfo::Registrovat

Volána [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create) zaregistrovat třídu okna, pokud ještě nebyla zaregistrována.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>Parametry

*pProc*<br/>
[out] Určuje původní proceduru okna existující třídy okna.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, atom, který jednoznačně identifikuje třídu okna, která je registrována. V opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud jste zadali [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) `Register` nebo [makro DECLARE_WND_CLASS_EX,](window-class-macros.md#declare_wnd_class_ex) zaregistruje novou třídu okna. V tomto případě se parametr *pProc* nepoužívá.

Pokud jste zadali makro `Register` [DECLARE_WND_SUPERCLASS,](window-class-macros.md#declare_wnd_superclass) zaregistruje nadřazenou třídu – třídu okna, která je založena na existující třídě, ale používá jinou proceduru okna. Procedura okna existující třídy okna je vrácena v *pProc*.

## <a name="see-also"></a>Viz také

[Třída CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
