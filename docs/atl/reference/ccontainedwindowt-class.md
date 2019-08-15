---
title: CContainedWindowT – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
ms.openlocfilehash: 2eae6e149cf6f7422d0653c1c15f46985d8d55c8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496848"
---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT – třída

Tato třída implementuje okno obsažené v jiném objektu.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>Parametry

*TBase*<br/>
Základní třída vaší nové třídy. Výchozí základní třída je `CWindow`.

*TWinTraits*<br/>
Třída vlastností, která definuje styly pro vaše okno. Výchozí hodnota je `CControlWinTraits`.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) je specializace `CContainedWindowT`. Pokud chcete změnit základní třídu nebo vlastnosti, použijte `CContainedWindowT` přímo.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Konstruktor Inicializuje datové členy k určení, které rozvržení zprávy zpracuje zprávy obsažených oken.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CContainedWindowT::Create](#create)|Vytvoří okno.|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Poskytuje výchozí zpracování zpráv.|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Vrátí aktuální zprávu.|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Zaregistruje třídu okna obsažených oken.|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|Podtřídí okno.|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Mění, která mapa zpráv se používá ke zpracování zpráv obsažených oken.|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Obnoví dříve podtřídované okno.|
|[CContainedWindowT::WindowProc](#windowproc)|Tras Zpracuje zprávy odeslané do okna obsaženého.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Určuje, která mapa zpráv bude zpracovávat zprávy obsažených oken.|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Určuje název existující třídy okna, na které bude založena nová třída okna.|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Odkazuje na původní proceduru okna třídy okna.|
|[CContainedWindowT::m_pObject](#m_pobject)|Odkazuje na objekt, který jej obsahuje.|

## <a name="remarks"></a>Poznámky

`CContainedWindowT`implementuje okno obsažené v jiném objektu. `CContainedWindowT`procedura okna používá mapu zprávy v objektu, který obsahuje, k přímému směrování zpráv na příslušné obslužné rutiny. Při vytváření `CContainedWindowT` objektu je třeba určit, která mapa zpráv má být použita.

`CContainedWindowT`umožňuje vytvořit nové okno podle třídy existující třídy okna. Metoda nejprve registruje třídu okna, která je založena na stávající třídě, ale používá `CContainedWindowT::WindowProc`. `Create` `Create`pak vytvoří okno na základě této nové třídy okna. Každá instance `CContainedWindowT` třídy může být na supertřídě jinou třídou okna.

`CContainedWindowT`podporuje také roztřídění oken. Metoda připojí existující okno `CContainedWindowT` k objektu a změní proceduru okna na `CContainedWindowT::WindowProc`. `SubclassWindow` Každá instance `CContainedWindowT` třídy může podtřídit jiné okno.

> [!NOTE]
>  Pro libovolný daný `CContainedWindowT` objekt volejte buď `Create` nebo `SubclassWindow`. U stejného objektu byste neměli volat obě metody.

Použijete-li možnost **Přidat ovládací prvek na základě** možnosti v Průvodci projektem ATL, průvodce automaticky přidá `CContainedWindowT` datový člen do třídy, která implementuje ovládací prvek. Následující příklad ukazuje, jak je uvedené okno deklarováno:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|Další informace o|Další informace naleznete v tématu|
|--------------------------------|---------|
|Vytváření ovládacích prvků|[Kurz ATL](../../atl/active-template-library-atl-tutorial.md)|
|Použití Windows v ATL|[ATL – třídy oken](../../atl/atl-window-classes.md)|
|Průvodce projektem ATL|[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Okna](/windows/win32/winmsg/windows) a další témata v Windows SDK|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="ccontainedwindowt"></a>CContainedWindowT::CContainedWindowT

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
pro Název existující třídy okna, na které bude zacházet obsažené okno.

*pObject*<br/>
pro Ukazatel na obsahující objekt, který deklaruje mapu zprávy. Třída tohoto objektu musí být odvozena od [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
pro Identifikuje mapu zpráv, která bude zpracovávat zprávy obsažených oken. Výchozí hodnota 0 určuje výchozí mapu zprávy deklarované pomocí [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Chcete-li použít alternativní mapu zpráv deklarovanou pomocí [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), předejte `msgMapID`.

### <a name="remarks"></a>Poznámky

Pokud chcete vytvořit nové okno pomocí [Vytvoření](#create), musíte předat název existující třídy okna pro parametr *lpszClassName* . Příklad najdete v přehledu [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) .

Existují tři konstruktory:

- Konstruktor se třemi argumenty je ten, který se obvykle volá.

- Konstruktor se dvěma argumenty používá název třídy z `TBase::GetWndClassName`.

- Konstruktor bez argumentů se používá, pokud chcete argumenty dodat později. Když později voláte `Create`, je nutné, abyste zadali název třídy okna, objekt mapy zprávy a ID mapy zprávy.

Pokud provedete podtřídou existujícího okna prostřednictvím [SubclassWindow](#subclasswindow), hodnota *lpszClassName* se nepoužije. Proto můžete pro tento parametr předat hodnotu NULL.

##  <a name="create"></a>CContainedWindowT:: Create

Volá [RegisterWndSuperclass](#registerwndsuperclass) k registraci třídy okna, která je založena na stávající třídě, ale používá [CContainedWindowT:: WindowProc](#windowproc).

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
pro Název existující třídy okna, na které bude zacházet obsažené okno.

*pObject*<br/>
pro Ukazatel na obsahující objekt, který deklaruje mapu zprávy. Třída tohoto objektu musí být odvozena od [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
pro Identifikuje mapu zpráv, která bude zpracovávat zprávy obsažených oken. Výchozí hodnota 0 určuje výchozí mapu zprávy deklarované pomocí [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Chcete-li použít alternativní mapu zpráv deklarovanou pomocí [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), předejte `msgMapID`.

*hWndParent*<br/>
pro Popisovač nadřazeného nebo vlastníka okna.

*OBD*<br/>
pro Struktura [Rect](/previous-versions/dd162897\(v=vs.85\)) určující pozici okna. Rozhraní `RECT` může být předáno ukazatelem nebo odkazem.

*szWindowName*<br/>
pro Určuje název okna. Výchozí hodnota je NULL.

*dwStyle*<br/>
pro Styl okna Výchozí hodnota je WS_CHILD &#124; WS_VISIBLE. Seznam možných hodnot naleznete v tématu [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v Windows SDK.

*dwExStyle*<br/>
pro Rozšířený styl okna Výchozí hodnota je 0, což znamená, že žádný rozšířený styl. Seznam možných hodnot naleznete v tématu [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v Windows SDK.

*MenuOrID*<br/>
pro V případě podřízeného okna identifikátor okna. Pro okno nejvyšší úrovně se pro okno zobrazí popisovač nabídky. Výchozí hodnota je **0U**.

*lpCreateParam*<br/>
pro Ukazatel na data vytváření oken. Úplný popis naleznete v popisu pro výsledný parametr [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu, popisovač do nově vytvořeného okna; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Existující název třídy okna je uložený v [m_lpszClassName](#m_lpszclassname). `Create`pak vytvoří okno na základě této nové třídy. Nově vytvořené okno je automaticky připojeno k `CContainedWindowT` objektu.

> [!NOTE]
>  Nevolejte `Create` , pokud jste již volali [SubclassWindow](#subclasswindow).

> [!NOTE]
>  Pokud se hodnota 0 používá jako hodnota parametru *MenuOrID* , musí být zadána jako 0U (výchozí hodnota), aby se předešlo chybě kompilátoru.

##  <a name="defwindowproc"></a>CContainedWindowT::D efWindowProc

Volá se [WindowProc](#windowproc) ke zpracování zpráv, které nezpracovává mapa zpráv.

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*uMsg*<br/>
pro Zpráva byla odeslána do okna.

*wParam*<br/>
pro Další informace specifické pro zprávy

*lParam*<br/>
pro Další informace specifické pro zprávy

### <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `DefWindowProc` volá funkci [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 k odeslání informací o zprávě do procedury okna zadané v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

##  <a name="getcurrentmessage"></a>CContainedWindowT::GetCurrentMessage

Vrátí aktuální zprávu (`m_pCurrentMsg`).

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální zpráva zabalená ve `MSG` struktuře.

##  <a name="m_dwmsgmapid"></a>  CContainedWindowT::m_dwMsgMapID

Obsahuje identifikátor aktuálně používaného okna Mapa zpráv.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>Poznámky

Tato mapa zpráv musí být deklarována v objektu, který jej obsahuje.

Výchozí mapa zpráv deklarovaná pomocí [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)je vždy označena nulou. Alternativní mapa zpráv deklarovaná pomocí [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)je identifikována nástrojem `msgMapID`.

`m_dwMsgMapID`je nejprve inicializován konstruktorem a lze jej změnit voláním [SwitchMessageMap](#switchmessagemap). Příklad najdete v [přehledu CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md).

##  <a name="m_lpszclassname"></a>CContainedWindowT::m_lpszClassName

Určuje název existující třídy okna.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>Poznámky

Při vytváření okna je [vytvořena](#create) registrace nové třídy okna, která je založena na této existující třídě, ale používá [CContainedWindowT:: WindowProc](#windowproc).

`m_lpszClassName`je inicializován konstruktorem. Příklad najdete v přehledu [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) .

##  <a name="m_pfnsuperwindowproc"></a>  CContainedWindowT::m_pfnSuperWindowProc

Pokud je obsažené okno podtříd, `m_pfnSuperWindowProc` odkazuje na původní proceduru okna třídy okna.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Poznámky

Pokud je obsažené okno v základní třídě, znamená to, že je založena na třídě okna, která upravuje existující třídu, `m_pfnSuperWindowProc` odkazuje na existující proceduru okna třídy okna.

Metoda [DefWindowProc](#defwindowproc) odesílá informace o zprávě do procedury okna uložené v `m_pfnSuperWindowProc`.

##  <a name="m_pobject"></a>  CContainedWindowT::m_pObject

Odkazuje na objekt obsahující `CContainedWindowT` objekt.

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>Poznámky

Tento kontejner, jehož třída se musí odvozovat z [CMessageMap](../../atl/reference/cmessagemap-class.md), deklaruje mapu zprávy použitou obsaženým oknem.

`m_pObject`je inicializován konstruktorem. Příklad najdete v přehledu [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) .

##  <a name="registerwndsuperclass"></a>CContainedWindowT::RegisterWndSuperclass

Volá se [vytvořením](#create) pro registraci třídy okna obsaženého okna.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, Atom, který jedinečně identifikuje registrovanou třídu okna; v opačném případě nula.

### <a name="remarks"></a>Poznámky

Tato třída okna je založena na stávající třídě, ale používá [CContainedWindowT:: WindowProc](#windowproc). Název a procedura okna existující třídy okna jsou uloženy v [m_lpszClassName](#m_lpszclassname) a [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)v uvedeném pořadí.

##  <a name="subclasswindow"></a>CContainedWindowT::SubclassWindow

Roztřídí okno identifikované pomocí *HWND* a připojí ho k `CContainedWindowT` objektu.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
pro Popisovač roztříděné okna.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je okno úspěšně podtříd; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Okno podtříd teď používá [CContainedWindowT:: WindowProc](#windowproc). Původní procedura okna je uložena v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
>  Nevolejte `SubclassWindow` , pokud jste již volali [Create](#create).

##  <a name="switchmessagemap"></a>CContainedWindowT::SwitchMessageMap

Mění, která mapa zpráv bude použita ke zpracování zpráv obsažených oken.

```
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>Parametry

*dwMsgMapID*<br/>
pro Identifikátor mapy zpráv Chcete-li použít výchozí mapu zpráv deklarovanou pomocí [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), předejte nulu. Chcete-li použít alternativní mapu zpráv deklarovanou pomocí [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), předejte `msgMapID`.

### <a name="remarks"></a>Poznámky

Mapa zpráv musí být definována v objektu, který jej obsahuje.

Zpočátku určíte identifikátor mapování zpráv v konstruktoru.

##  <a name="unsubclasswindow"></a>CContainedWindowT::UnsubclassWindow

Odpojí okno podtřídy od `CContainedWindowT` objektu a obnoví původní proceduru okna uloženou v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>Parametry

*bForce*<br/>
pro Nastavte na hodnotu true, pokud chcete vynutit obnovení původní procedury okna i v případě, že procedura `CContainedWindowT` okna pro tento objekt není aktuálně aktivní. Pokud je *bForce* nastavené na false a procedura okna pro tento `CContainedWindowT` objekt není aktuálně aktivní, původní procedura okna se neobnoví.

### <a name="return-value"></a>Návratová hodnota

Popisovač pro dříve vytříděné okno. Pokud je *bForce* nastaveno na false a procedura okna pro tento `CContainedWindowT` objekt není aktuálně aktivní, vrátí hodnotu null.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze v případě, že chcete obnovit původní proceduru okna před zničením okna. V opačném případě [WindowProc](#windowproc) automaticky provede při zničení okna.

##  <a name="windowproc"></a>CContainedWindowT::WindowProc

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
pro Popisovač okna.

*uMsg*<br/>
pro Zpráva byla odeslána do okna.

*wParam*<br/>
pro Další informace specifické pro zprávy

*lParam*<br/>
pro Další informace specifické pro zprávy

### <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy

### <a name="remarks"></a>Poznámky

`WindowProc`směruje zprávy na mapu zpráv identifikovanou pomocí [m_dwMsgMapID](#m_dwmsgmapid). V případě potřeby `WindowProc` zavolá [DefWindowProc](#defwindowproc) pro další zpracování zpráv.

## <a name="see-also"></a>Viz také:

[CWindow – třída](../../atl/reference/cwindow-class.md)<br/>
[CWindowImpl – třída](../../atl/reference/cwindowimpl-class.md)<br/>
[CMessageMap – třída](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
