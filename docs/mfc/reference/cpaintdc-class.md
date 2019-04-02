---
title: CPaintDC Class
ms.date: 11/04/2016
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
ms.openlocfilehash: df1db8a3e65d35f247df7d070119c66b02208815
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772056"
---
# <a name="cpaintdc-class"></a>CPaintDC Class

Kontext zařízení třída odvozená z [CDC](../../mfc/reference/cdc-class.md).

## <a name="syntax"></a>Syntaxe

```
class CPaintDC : public CDC
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|Vytvoří `CPaintDC` připojené k zadané [CWnd](../../mfc/reference/cwnd-class.md).|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Obsahuje [paintstruct –](/windows/desktop/api/winuser/ns-winuser-tagpaintstruct) použita k vyplnění klientské oblasti.|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|HWND, ke kterému je tento `CPaintDC` objekt připojen.|

## <a name="remarks"></a>Poznámky

Funguje [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) v době konstrukce a [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) v době zničení.

A `CPaintDC` objektu jde použít jenom při odpovídání na [WM_PAINT](/windows/desktop/gdi/wm-paint) zpráv, obvykle v vaše `OnPaint` obslužná rutina zprávy členskou funkci.

Další informace o používání `CPaintDC`, naleznete v tématu [kontexty zařízení](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC

Vytvoří `CPaintDC` připraví okna aplikace pro kreslení objektu a ukládá [paintstruct –](/windows/desktop/api/winuser/ns-winuser-tagpaintstruct) struktury v [m_ps](#m_ps) členské proměnné.

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na `CWnd` objekt, na který `CPaintDC` objekt patří.

### <a name="remarks"></a>Poznámky

Výjimky (typu `CResourceException`) je vyvolána, pokud Windows [GetDC](/windows/desktop/api/winuser/nf-winuser-getdc) volání selže. Kontext zařízení nemusí být k dispozici, pokud Windows má již přiděleno všechny jeho kontexty zařízení k dispozici. Vaše aplikace bojuje pěti běžných zobrazení kontextů k dispozici v daném okamžiku v části Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd

`HWND` Ke kterému je tento `CPaintDC` objekt připojen.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Poznámky

*m_hWnd* je chráněná proměnná typu HWND.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>  CPaintDC::m_ps

`m_ps` je veřejné členské proměnné typu [paintstruct –](/windows/desktop/api/winuser/ns-winuser-tagpaintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Poznámky

Je `PAINTSTRUCT` , který je předán a vyplňuje [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

`PAINTSTRUCT` Obsahuje informace, které aplikace používá k vyplnění klientské oblasti okna přidružené `CPaintDC` objektu.

Všimněte si, že dostanete popisovač kontextu zařízení prostřednictvím `PAINTSTRUCT`. Však můžete přistupovat k popisovač více přímo prostřednictvím `m_hDC` členské proměnné, která `CPaintDC` dědí z CSP.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPaintDC::m_hWnd](#m_hwnd).

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC – třída](../../mfc/reference/cdc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
