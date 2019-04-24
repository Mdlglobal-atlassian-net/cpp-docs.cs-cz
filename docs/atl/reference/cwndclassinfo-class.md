---
title: Cwndclassinfo – třída
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
ms.openlocfilehash: 4aeac558c28d0ac89707423433e51f348bc35d29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276715"
---
# <a name="cwndclassinfo-class"></a>Cwndclassinfo – třída

Tato třída poskytuje metody pro registraci informace pro třídu okna.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CWndClassInfo
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|[Register](#register)|Zaregistruje třídu okna.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_atom](#m_atom)|Jednoznačně identifikuje třídy registrované okna.|
|[m_bSystemCursor](#m_bsystemcursor)|Určuje, zda odkazuje prostředku kurzoru do pozice kurzoru systém nebo ke kurzoru obsažené v modulu zdroje.|
|[m_lpszCursorID](#m_lpszcursorid)|Určuje název prostředku kurzoru.|
|[m_lpszOrigName](#m_lpszorigname)|Obsahuje název existující třídy okna.|
|[m_szAutoName](#m_szautoname)|ATL generovaný název třídy okna obsahuje.|
|[m_wc](#m_wc)|Udržuje informace o třídě okna v `WNDCLASSEX` struktury.|
|[pWndProc](#pwndproc)|Body procedury okna existující třídy okna.|

## <a name="remarks"></a>Poznámky

`CWndClassInfo` spravuje informace třídy okna. Obvykle použijete `CWndClassInfo` prostřednictvím jednoho z tři makra, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX nebo DECLARE_WND_SUPERCLASS, jak je popsáno v následující tabulce:

|– Makro|Popis|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo` zaregistruje informace pro novou třídu okna.|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo` zaregistruje informace pro novou třídu okna, včetně parametrů třídy.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo` zaregistruje informace pro třídy okna, která je založena na existující třídy, ale používá jiné okno procedury. Tato technika se nazývá superclassing.|

Ve výchozím nastavení [CWindowImpl](../../atl/reference/cwindowimpl-class.md) zahrnuje `DECLARE_WND_CLASS` – makro vytvořit okno založené na nové třídě okna. DECLARE_WND_CLASS poskytuje výchozí styly a barva pozadí ovládacího prvku. Pokud chcete určit styl a barva pozadí sami, odvodit třídu z `CWindowImpl` a zahrnují DECLARE_WND_CLASS_EX makra v definici třídy.

Pokud chcete vytvořit okno na základě existující třídy okna, jsou odvozeny z vaší třídy `CWindowImpl` a zahrnují DECLARE_WND_SUPERCLASS makra v definici třídy. Příklad:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

Další informace o třídách oken, naleznete v tématu [tříd oken](/windows/desktop/winmsg/window-classes) v sadě Windows SDK.

Další informace o používání oken v ATL, najdete v článku [tříd oken ATL](../../atl/atl-window-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="m_atom"></a>  CWndClassInfo::m_atom

Obsahuje jedinečný identifikátor pro třídu registrované okna.

```
ATOM m_atom;
```

##  <a name="m_bsystemcursor"></a>  CWndClassInfo::m_bSystemCursor

Při hodnotě TRUE se při registraci třídu okna se načtou systémový prostředek kurzoru.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Poznámky

V opačném případě bude načten prostředku kurzoru obsažené v modulu.

`CWndClassInfo` používá `m_bSystemCursor` pouze tehdy, když [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí nastavení v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) nebo [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) – makro je zadán. V takovém případě `m_bSystemCursor` je inicializován na hodnotu TRUE. Další informace najdete v tématu [cwndclassinfo –](../../atl/reference/cwndclassinfo-class.md) Přehled.

##  <a name="m_lpszcursorid"></a>  CWndClassInfo::m_lpszCursorID

Určuje název prostředku kurzoru nebo identifikátor prostředku v nižší řád slova a nulu, ve vyšší řád slova.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Poznámky

Při registraci třídy okna, popisovač do pozice kurzoru identifikovaný `m_lpszCursorID` je načten a ukládaná [m_wc](#m_wc).

`CWndClassInfo` používá `m_lpszCursorID` pouze tehdy, když [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí nastavení v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) nebo [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) – makro je zadán. V takovém případě `m_lpszCursorID` je inicializován na IDC_ARROW. Další informace najdete v tématu [cwndclassinfo –](../../atl/reference/cwndclassinfo-class.md) Přehled.

##  <a name="m_lpszorigname"></a>  CWndClassInfo::m_lpszOrigName

Obsahuje název existující třídy okna.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Poznámky

`CWndClassInfo` používá `m_lpszOrigName` pouze pokud zahrnete [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra v definici třídy. V takovém případě `CWndClassInfo` registrů třídy okna založené na třídě s názvem podle `m_lpszOrigName`. Další informace najdete v tématu [cwndclassinfo –](../../atl/reference/cwndclassinfo-class.md) Přehled.

##  <a name="m_szautoname"></a>  CWndClassInfo::m_szAutoName

Obsahuje název třídy okna.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Poznámky

`CWndClassInfo` používá `m_szAutoName` pouze tehdy, pokud je předána hodnota NULL `WndClassName` parametr [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) nebo [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . ATL – vytvoří název třídy okna se po zaregistrování.

##  <a name="m_wc"></a>  CWndClassInfo::m_wc

Udržuje informace o třídě okna v [WNDCLASSEX](/windows/desktop/api/winuser/ns-winuser-tagwndclassexa) struktury.

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Poznámky

Pokud jste zadali [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí nastavení v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) nebo [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) – makro, `m_wc` obsahuje informace o nové třídy okna.

Pokud jste zadali [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) – makro, `m_wc` obsahuje informace supertřídě – třídy okna, která je založena na existující třídy, ale používá jiné okno procedury. [m_lpszOrigName](#m_lpszorigname) a [pWndProc](#pwndproc) uložit název existující třídy okna a proceduru okna, v uvedeném pořadí.

##  <a name="pwndproc"></a>  CWndClassInfo::pWndProc

Body procedury okna existující třídy okna.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Poznámky

`CWndClassInfo` používá `pWndProc` pouze pokud zahrnete [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra v definici třídy. V takovém případě `CWndClassInfo` zaregistruje třídu okna, která vychází z existující třídy, ale používá jiné okno postup. Proceduru okna existující třídu okna se uloží do `pWndProc`. Další informace najdete v tématu [cwndclassinfo –](../../atl/reference/cwndclassinfo-class.md) Přehled.

##  <a name="register"></a>  CWndClassInfo::Register

Volané [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create) registrace třídy okna, pokud ho ještě není zaregistrovaný.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>Parametry

*pProc*<br/>
[out] Určuje původní proceduru okna existující třídy okna.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu, atom, který jednoznačně identifikuje registrovaného třídu okna. Jinak 0.

### <a name="remarks"></a>Poznámky

Pokud jste zadali [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí nastavení v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) nebo [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) – makro, `Register` zaregistruje nové třídy okna. V takovém případě *pProc* parametr se nepoužívá.

Pokud jste zadali [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) – makro, `Register` zaregistruje nadřazenou třídu – třídy okna, která je založena na existující třídy, ale používá jiné okno procedury. Proceduru okna existující třídu okna se vrátí v *pProc*.

## <a name="see-also"></a>Viz také:

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
