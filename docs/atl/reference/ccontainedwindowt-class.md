---
title: Ccontainedwindowt – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CContainedWindowT
- ATLWIN/ATL::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::Create
- ATLWIN/ATL::CContainedWindowT::DefWindowProc
- ATLWIN/ATL::CContainedWindowT::GetCurrentMessage
- ATLWIN/ATL::CContainedWindowT::RegisterWndSuperclass
- ATLWIN/ATL::CContainedWindowT::SubclassWindow
- ATLWIN/ATL::CContainedWindowT::SwitchMessageMap
- ATLWIN/ATL::CContainedWindowT::UnsubclassWindow
- ATLWIN/ATL::CContainedWindowT::WindowProc
- ATLWIN/ATL::CContainedWindowT::m_dwMsgMapID
- ATLWIN/ATL::CContainedWindowT::m_lpszClassName
- ATLWIN/ATL::CContainedWindowT::m_pfnSuperWindowProc
- ATLWIN/ATL::CContainedWindowT::m_pObject
dev_langs:
- C++
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e65451fcb506da9072d0dc8031ffba1b30280e6
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861431"
---
# <a name="ccontainedwindowt-class"></a>Ccontainedwindowt – třída

Tato třída implementuje oken obsažených v rámci jiného objektu.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>Parametry

*Tčíslice*<br/>
Základní třídy novou třídu. Výchozí základní třída je `CWindow`.

*TWinTraits*<br/>
Třída vlastností, která definuje styly pro okno. Výchozí hodnota je `CControlWinTraits`.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) je specializací `CContainedWindowT`. Pokud chcete změnit základní třídu nebo vlastnosti, použijte `CContainedWindowT` přímo.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Konstruktor Inicializuje datové členy k určení, která mapu zpráv zpracuje zprávy obsaženého okna.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CContainedWindowT::Create](#create)|Vytvoří okno.|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Poskytuje výchozí zpracování zpráv.|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Vrátí aktuální zprávu.|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Zaregistruje třídu okna obsaženého okna.|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|Podtřídy okno.|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Změny, které mapu zpráv se používá ke zpracování zpráv obsaženého okna.|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Obnoví dříve rozčleněných do podtříd okna.|
|[CContainedWindowT::WindowProc](#windowproc)|(Statické) Zpracovává zprávy odeslané do obsaženého okna.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Určuje, která mapu zpráv zpracuje zprávy obsaženého okna.|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Určuje název existující třídy okna, na kterém bude na základě nové třídy okna.|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Odkazuje na třídu okna původní proceduru okna.|
|[CContainedWindowT::m_pObject](#m_pobject)|Odkazuje na nadřazený objekt.|

## <a name="remarks"></a>Poznámky

`CContainedWindowT` implementuje okno obsažené v rámci jiného objektu. `CContainedWindowT`vaší používá proceduru okna zprávu mapování nadřazeného objektu přímé zprávy do příslušné obslužné rutiny. Při vytváření `CContainedWindowT` objektu, můžete zadat, které mapy zpráv má být použita.

`CContainedWindowT` Umožňuje vytvořit nové okno podle superclassing existující třídy okna. `Create` Metoda nejprve zaregistruje třídu okna, která vychází z existující třídy, ale používá `CContainedWindowT::WindowProc`. `Create` vytvoří okno na základě této nové třídy okna. Každá instance `CContainedWindowT` můžete nadřazené třídu jiného okna.

`CContainedWindowT` podporuje také vytváření podtříd okna. `SubclassWindow` Metoda připojí k existujícímu oknu `CContainedWindowT` objektu a změní proceduru okna k `CContainedWindowT::WindowProc`. Každá instance `CContainedWindowT` můžou podtřídy jiného okna.

> [!NOTE]
>  Pro všechny uvedené `CContainedWindowT` objektu, volejte buď `Create` nebo `SubclassWindow`. Neměli vyvolání obou metod na stejný objekt.

Při použití **přidání ovládacího prvku na základě** možnost Průvodce projektem ATL, průvodce automaticky přidá `CContainedWindowT` datový člen třídy implementující ovládací prvek. Následující příklad ukazuje, jak je deklarován obsaženého okna:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|Další informace o|Další informace naleznete v tématu|
|--------------------------------|---------|
|Vytváření ovládacích prvků|[ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md)|
|Pomocí systému windows v knihovně ATL|[ATL – třídy oken](../../atl/atl-window-classes.md)|
|Průvodce projektem ATL|[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Windows](/windows/desktop/winmsg/windows) a dalších tématech v sadě Windows SDK|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="ccontainedwindowt"></a>  CContainedWindowT::CContainedWindowT

Konstruktor inicializuje datové členy.

```
CContainedWindowT(
    LPTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);

CContainedWindowT(
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0)
    CContainedWindowT();
```

### <a name="parameters"></a>Parametry

*lpszClassName*<br/>
[in] Název existující třídy okna, na které bude založená obsaženého okna.

*odstraněný objekt*<br/>
[in] Ukazatel na nadřazený objekt, který deklaruje mapování zprávy. Tento objekt třídy musí být odvozen od [cmessagemap –](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[in] Určuje, který bude zpracovávat zprávy obsaženého okna mapování zprávy. Výchozí hodnota je 0, určuje výchozí mapování zpráv deklarována s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Použijte mapu alternativní zpráva deklarována s [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), předejte `msgMapID`.

### <a name="remarks"></a>Poznámky

Pokud chcete vytvořit nové okno prostřednictvím [vytvořit](#create), musíte předat název existující třídy okna pro *lpszClassName* parametru. Příklad najdete v tématu [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) Přehled.

Existují tři konstruktory:

- Konstruktor s třemi argumenty je obvykle volána.

- Konstruktor se dvěma argumenty používá název třídy z `TBase::GetWndClassName`.

- Konstruktor bez argumentů se používá, pokud chcete zadat argumenty později. Musíte zadat název třídy okna, objekt map zpráv a mapování ID zprávy, když později zavoláte `Create`.

Pokud podtřídy existujícímu oknu prostřednictvím [SubclassWindow](#subclasswindow), *lpszClassName* nebude použita hodnota; proto můžete pro tento parametr předat hodnotu NULL.

##  <a name="create"></a>  CContainedWindowT::Create

Volání [RegisterWndSuperclass](#registerwndsuperclass) registrace třídy okna, která je založena na existující třídy, ale používá [CContainedWindowT::WindowProc](#windowproc).

```
HWND Create(  
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    LPCTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>Parametry

*lpszClassName*<br/>
[in] Název existující třídy okna, na které bude založená obsaženého okna.

*odstraněný objekt*<br/>
[in] Ukazatel na nadřazený objekt, který deklaruje mapování zprávy. Tento objekt třídy musí být odvozen od [cmessagemap –](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[in] Určuje, který bude zpracovávat zprávy obsaženého okna mapování zprávy. Výchozí hodnota je 0, určuje výchozí mapování zpráv deklarována s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Použijte mapu alternativní zpráva deklarována s [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), předejte `msgMapID`.

*hWndParent*<br/>
[in] Popisovač okna nadřazené nebo vlastníka.

*Rect*<br/>
[in] A [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura určující pozici okna. `RECT` Je možné předat ukazatelem nebo odkazem.

*szWindowName*<br/>
[in] Určuje název okna. Výchozí hodnota je NULL.

*dwStyle*<br/>
[in] Styl okna. Výchozí hodnota je WS_CHILD &#124; WS_VISIBLE. Seznam možných hodnot najdete v tématu [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) v sadě Windows SDK.

*dwExStyle*<br/>
[in] Styl rozšířené okna. Výchozí hodnota je 0, to znamená bez rozšířeného stylu. Seznam možných hodnot najdete v tématu [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) v sadě Windows SDK.

*MenuOrID*<br/>
[in] Pro podřízené okno identifikátor okna. Pro okno nejvyšší úrovně, nabídky popisovač okna. Výchozí hodnota je **0U**.

*lpCreateParam*<br/>
[in] Ukazatel na data vytvoření okna. Úplný popis naleznete v popisu pro poslední parametr [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa).

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu popisovač do nově vytvořeného okna. v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Existující název třídy okna je uložen v [m_lpszClassName](#m_lpszclassname). `Create` vytvoří na základě této nové třídy okna. Nově vytvořený okno je automaticky připojen k `CContainedWindowT` objektu.

> [!NOTE]
>  Nevolejte `Create` Pokud už jste volali [SubclassWindow](#subclasswindow).

> [!NOTE]
>  Pokud se použije jako hodnota 0 *MenuOrID* parametru, musí být zadán jako 0U (výchozí hodnota), aby chybu kompilátoru.

##  <a name="defwindowproc"></a>  CContainedWindowT::DefWindowProc

Volané [WindowProc](#windowproc) zpracování zpráv není zpracována v mapování zprávy.

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*uMsg*<br/>
[in] Zpráva odeslaná do okna.

*wParam*<br/>
[in] Další informace specifické pro zprávy.

*lParam*<br/>
[in] Další informace specifické pro zprávy.

### <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `DefWindowProc` volání [CallWindowProc](https://msdn.microsoft.com/library/windows/desktop/ms633571) funkci Win32 k odeslání informací zprávu do okna postupem uvedeným v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

##  <a name="getcurrentmessage"></a>  CContainedWindowT::GetCurrentMessage

Vrátí aktuální zprávu (`m_pCurrentMsg`).

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální zprávu zabalen do `MSG` struktury.

##  <a name="m_dwmsgmapid"></a>  CContainedWindowT::m_dwMsgMapID

Obsahuje identifikátor mapu zpráv aktuálně používá pro obsaženého okna.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>Poznámky

Toto mapování zpráv musí být deklarována v nadřazeného objektu.

Výchozí zprávu mapování deklarována s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), je vždy označena nula. Mapování zpráv alternativní deklarované s [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), je identifikován `msgMapID`.

`m_dwMsgMapID` Nejprve je inicializován pomocí konstruktoru a můžete změnit po zavolání [SwitchMessageMap](#switchmessagemap). Příklad najdete v tématu [ccontainedwindowt – přehled](../../atl/reference/ccontainedwindowt-class.md).

##  <a name="m_lpszclassname"></a>  CContainedWindowT::m_lpszClassName

Určuje název existující třídy okna.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>Poznámky

Při vytváření okna, [vytvořit](#create) zaregistruje novou třídu okna, která je založena na existující třída, ale používá [CContainedWindowT::WindowProc](#windowproc).

`m_lpszClassName` je inicializován pomocí konstruktoru. Příklad najdete v tématu [ccontainedwindowt –](../../atl/reference/ccontainedwindowt-class.md) Přehled.

##  <a name="m_pfnsuperwindowproc"></a>  CContainedWindowT::m_pfnSuperWindowProc

Pokud rozčlenění obsaženého okna `m_pfnSuperWindowProc` odkazuje na původní proceduru okna třídy okna.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Poznámky

Pokud je okno omezením supertřídu, to znamená, ho vychází třídy okna, která upravuje existující třídu, `m_pfnSuperWindowProc` odkazuje na existující třídu okna proceduru okna.

[DefWindowProc](#defwindowproc) metoda odesílá informace o zprávě proceduru okna, které jsou uloženy v `m_pfnSuperWindowProc`.

##  <a name="m_pobject"></a>  CContainedWindowT::m_pObject

Odkazuje na objekt obsahující `CContainedWindowT` objektu.

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>Poznámky

Tento kontejner, jehož třída musí být odvozen od [cmessagemap –](../../atl/reference/cmessagemap-class.md), deklaruje mapu zpráv používá obsaženého okna.

`m_pObject` je inicializován pomocí konstruktoru. Příklad najdete v tématu [ccontainedwindowt –](../../atl/reference/ccontainedwindowt-class.md) Přehled.

##  <a name="registerwndsuperclass"></a>  CContainedWindowT::RegisterWndSuperclass

Volané [vytvořit](#create) registrovat třídu okna obsaženého okna.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu, atom, který jednoznačně identifikuje registrovaného; třídu okna jinak, nula.

### <a name="remarks"></a>Poznámky

Tato třída okno vychází z existující třídy, ale používá [CContainedWindowT::WindowProc](#windowproc). Existující třídu okna název a okno procedury jsou uloženy v [m_lpszClassName](#m_lpszclassname) a [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)v uvedeném pořadí.

##  <a name="subclasswindow"></a>  CContainedWindowT::SubclassWindow

Podtřídy třídy okna identifikovaný *hWnd* a připojí ho k `CContainedWindowT` objektu.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Popisovač okna se rozčlenit do podtříd.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud v okně se úspěšně rozčlenit do podtříd; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Nyní používá rozčleněných do podtříd okno [CContainedWindowT::WindowProc](#windowproc). Původní proceduru okna se uloží do [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
>  Nevolejte `SubclassWindow` Pokud už jste volali [vytvořit](#create).

##  <a name="switchmessagemap"></a>  CContainedWindowT::SwitchMessageMap

Změny, které mapu zpráv se použije ke zpracování zpráv obsaženého okna.

```
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>Parametry

*dwMsgMapID*<br/>
[in] Identifikátor mapování zprávy. Použít výchozí mapování zpráv deklarována s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), předejte nula. Použijte mapu alternativní zpráva deklarována s [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), předejte `msgMapID`.

### <a name="remarks"></a>Poznámky

Mapy zpráv musí být definován v obsahujícího objektu.

Nejdřív zadejte identifikátor mapy zpráv v konstruktoru.

##  <a name="unsubclasswindow"></a>  CContainedWindowT::UnsubclassWindow

Odpojí okno rozčleněný z `CContainedWindowT` objektu a obnoví původní proceduru okna uložené v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>Parametry

*bForce*<br/>
[in] Nastavte na hodnotu PRAVDA, platnost obnovit původní proceduru okna i v případě proceduru okna pro tuto `CContainedWindowT` objekt není aktuálně aktivní. Pokud *bForce* je nastavena na hodnotu FALSE a proceduru okna pro tuto `CContainedWindowT` objekt není aktuálně aktivní, nebude možné obnovit původní proceduru okna.

### <a name="return-value"></a>Návratová hodnota

Popisovač okna dříve rozčlenit do podtříd. Pokud *bForce* je nastavena na hodnotu FALSE a proceduru okna pro tuto `CContainedWindowT` objekt není aktuálně aktivní, vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Tuto metodu lze použijte pouze v případě, že chcete obnovit původní proceduru okna zničen okna. V opačném případě [WindowProc](#windowproc) automaticky dělá to při zničení okna.

##  <a name="windowproc"></a>  CContainedWindowT::WindowProc

Tato statická metoda implementuje proceduru okna.

```
static LRESULT CALLBACK WindowProc(  
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Popisovač okna.

*uMsg*<br/>
[in] Zpráva odeslaná do okna.

*wParam*<br/>
[in] Další informace specifické pro zprávy.

*lParam*<br/>
[in] Další informace specifické pro zprávy.

### <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy.

### <a name="remarks"></a>Poznámky

`WindowProc` přesměruje zprávy do mapy zpráv, který je identifikován [m_dwMsgMapID](#m_dwmsgmapid). V případě potřeby `WindowProc` volání [DefWindowProc](#defwindowproc) pro zpracování další zprávy.

## <a name="see-also"></a>Viz také

[CWindow – třída](../../atl/reference/cwindow-class.md)<br/>
[CWindowImpl – třída](../../atl/reference/cwindowimpl-class.md)<br/>
[CMessageMap – třída](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
