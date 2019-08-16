---
title: CWndClassInfo – třída
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
ms.openlocfilehash: c416155ed103f1345c42e6680c2329ab98d35926
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496129"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo – třída

Tato třída poskytuje metody pro registraci informací pro třídu okna.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CWndClassInfo
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|[Registrace](#register)|Zaregistruje třídu okna.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_atom](#m_atom)|Jednoznačně identifikuje registrovanou třídu okna.|
|[m_bSystemCursor](#m_bsystemcursor)|Určuje, zda prostředek kurzoru odkazuje na systémový kurzor nebo na kurzor obsažený v prostředku modulu.|
|[m_lpszCursorID](#m_lpszcursorid)|Určuje název prostředku kurzoru.|
|[m_lpszOrigName](#m_lpszorigname)|Obsahuje název existující třídy okna.|
|[m_szAutoName](#m_szautoname)|Obsahuje název třídy okna generovaný knihovnou ATL.|
|[m_wc](#m_wc)|Udržuje informace o třídách okna `WNDCLASSEX` ve struktuře.|
|[pWndProc](#pwndproc)|Odkazuje na proceduru okna existující třídy okna.|

## <a name="remarks"></a>Poznámky

`CWndClassInfo`spravuje informace třídy okna. Obvykle používáte `CWndClassInfo` jednu ze tří maker, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX nebo DECLARE_WND_SUPERCLASS, jak je popsáno v následující tabulce:

|– Makro|Popis|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`registruje informace pro novou třídu okna.|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`registruje informace pro novou třídu okna včetně parametrů třídy.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`registruje informace pro třídu okna, která je založena na stávající třídě, ale používá jinou proceduru okna. Tato technika se nazývá "podtříd".|

Ve výchozím nastavení [](../../atl/reference/cwindowimpl-class.md) zahrnuje `DECLARE_WND_CLASS` CWindowImpl makro pro vytvoření okna založeného na nové třídě okna. DECLARE_WND_CLASS poskytuje pro ovládací prvek výchozí styly a barvu pozadí. Chcete-li zadat styl a barvu pozadí sami, odvodit třídu z `CWindowImpl` a zahrnout makro DECLARE_WND_CLASS_EX do definice třídy.

Pokud chcete vytvořit okno na základě existující třídy okna, odvodit třídu z `CWindowImpl` a zahrnout makro DECLARE_WND_SUPERCLASS do definice třídy. Příklad:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

Další informace o třídách okna naleznete v tématu [třídy oken](/windows/win32/winmsg/window-classes) v Windows SDK.

Další informace o použití systému Windows v knihovně ATL naleznete v článku [třídy okna ATL](../../atl/atl-window-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="m_atom"></a>CWndClassInfo::m_atom

Obsahuje jedinečný identifikátor pro registrovanou třídu okna.

```
ATOM m_atom;
```

##  <a name="m_bsystemcursor"></a>CWndClassInfo::m_bSystemCursor

Pokud je nastaveno na TRUE, prostředek systémového kurzoru se načte při registraci třídy okna.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Poznámky

V opačném případě se načte prostředek kurzoru obsažený v modulu.

`CWndClassInfo`používá `m_bSystemCursor` se pouze v případě, že je zadáno [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) nebo makro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) . V tomto případě `m_bSystemCursor` je inicializován na hodnotu true. Další informace najdete v tématu [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) Overview.

##  <a name="m_lpszcursorid"></a>  CWndClassInfo::m_lpszCursorID

Určuje buď název prostředku kurzoru, nebo identifikátor prostředku v aplikaci s nízkým pořadím a nula v aplikaci s vysokým pořadím.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Poznámky

Je-li Třída okna registrována, `m_lpszCursorID` je popisovač kurzoru, který je identifikován, načten a uložen pomocí [m_wc](#m_wc).

`CWndClassInfo`používá `m_lpszCursorID` se pouze v případě, že je zadáno [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) nebo makro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) . V tomto případě `m_lpszCursorID` je inicializována na IDC_ARROW. Další informace najdete v tématu [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) Overview.

##  <a name="m_lpszorigname"></a>  CWndClassInfo::m_lpszOrigName

Obsahuje název existující třídy okna.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Poznámky

`CWndClassInfo`používá `m_lpszOrigName` se pouze při zahrnutí makra [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) do definice třídy. V tomto případě `CWndClassInfo` registruje třídu okna na základě třídy `m_lpszOrigName`s názvem. Další informace najdete v tématu [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) Overview.

##  <a name="m_szautoname"></a>CWndClassInfo::m_szAutoName

Obsahuje název třídy okna.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Poznámky

`CWndClassInfo`používá `m_szAutoName` pouze v případě, že je předána hodnota `WndClassName` null pro parametr do [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) nebo [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ATL při registraci třídy okna vytvoří název.

##  <a name="m_wc"></a>  CWndClassInfo::m_wc

Udržuje informace o třídě okna ve struktuře [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw) .

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Poznámky

Pokud jste zadali [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) nebo makro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) , `m_wc` obsahuje informace o nové třídě okna.

Pokud jste zadali makro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) , `m_wc` obsahuje informace o supertřídě – třídu okna, která je založena na stávající třídě, ale používá jinou proceduru okna. [m_lpszOrigName](#m_lpszorigname) a [pWndProc](#pwndproc) uloží název a proceduru okna existující třídy okna (v uvedeném pořadí).

##  <a name="pwndproc"></a>CWndClassInfo::p WndProc

Odkazuje na proceduru okna existující třídy okna.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Poznámky

`CWndClassInfo`používá `pWndProc` se pouze při zahrnutí makra [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) do definice třídy. V tomto případě `CWndClassInfo` registruje třídu okna, která je založena na stávající třídě, ale používá jinou proceduru okna. Procedura okna existující třídy okna je uložena v `pWndProc`. Další informace najdete v tématu [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) Overview.

##  <a name="register"></a>CWndClassInfo:: Register

Volá se [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create) k registraci třídy okna, pokud ještě není zaregistrovaná.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>Parametry

*pProc*<br/>
mimo Určuje původní proceduru okna existující třídy okna.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu se jedná o Atom, který jedinečně identifikuje registrovanou třídu Window. V opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud jste zadali [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) nebo makro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) , `Register` zaregistruje novou třídu okna. V tomto případě není použit parametr *pProc* .

Pokud jste zadali makro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) , `Register` registruje supertřída třídu, která je založena na stávající třídě, ale používá jinou proceduru okna. V *pProc*se vrátí procedura okna existující třídy okna.

## <a name="see-also"></a>Viz také:

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
