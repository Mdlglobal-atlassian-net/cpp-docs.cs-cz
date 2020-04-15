---
title: CPaintDC – třída
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
ms.openlocfilehash: 55342b03454a6dba07bc10ea5f0464c34e0e8db3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374780"
---
# <a name="cpaintdc-class"></a>CPaintDC – třída

Třída kontextu zařízení odvozená z [CDC](../../mfc/reference/cdc-class.md).

## <a name="syntax"></a>Syntaxe

```
class CPaintDC : public CDC
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|Vytvoří `CPaintDC` připojení k zadanému [CWnd](../../mfc/reference/cwnd-class.md).|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Obsahuje [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct) slouží k malování klientské oblasti.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|HWND, ke `CPaintDC` kterému je tento objekt připojen.|

## <a name="remarks"></a>Poznámky

Provádí [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) v době [výstavby a CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) v době zničení.

Objekt `CPaintDC` lze použít pouze při odpovědi na zprávu `OnPaint` [WM_PAINT,](/windows/win32/gdi/wm-paint) obvykle v členské funkce obslužné rutiny zprávy.

Další informace o `CPaintDC`použití naleznete v [tématu Kontexty zařízení](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cpaintdccpaintdc"></a><a name="cpaintdc"></a>CPaintDC::CPaintDC

Vytvoří `CPaintDC` objekt, připraví okno aplikace pro malování a uloží strukturu [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct) do proměnné [m_ps](#m_ps) člena.

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na `CWnd` objekt, `CPaintDC` ke kterému objekt patří.

### <a name="remarks"></a>Poznámky

Výjimka (typu) `CResourceException`je vyvolána, pokud se nezdaří volání [Windows GetDC.](/windows/win32/api/winuser/nf-winuser-getdc) Kontext zařízení nemusí být k dispozici, pokud systém Windows již přidělil všechny své dostupné kontexty zařízení. Vaše aplikace soutěží o pět běžných kontextů zobrazení, které jsou k dispozici v daném okamžiku v systému Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

## <a name="cpaintdcm_hwnd"></a><a name="m_hwnd"></a>CPaintDC::m_hWnd

Ke `HWND` kterému `CPaintDC` je tento objekt připojen.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Poznámky

*m_hWnd* je chráněná proměnná typu HWND.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

## <a name="cpaintdcm_ps"></a><a name="m_ps"></a>CPaintDC::m_ps

`m_ps`je proměnná veřejného člena typu [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Poznámky

Je `PAINTSTRUCT` to, že je předán a [vyplněncwnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

Obsahuje `PAINTSTRUCT` informace, které aplikace používá k malování klientské `CPaintDC` oblasti okna přidruženého k objektu.

Všimněte si, že můžete přistupovat `PAINTSTRUCT`popisovač kontextu zařízení prostřednictvím . Však můžete přistupovat k popisovači více přímo prostřednictvím `m_hDC` členské proměnné, která `CPaintDC` dědí z CDC.

### <a name="example"></a>Příklad

  Viz příklad [cpaintdc::m_hWnd](#m_hwnd).

## <a name="see-also"></a>Viz také

[MDI vzorku knihovny MFc](../../overview/visual-cpp-samples.md)<br/>
[Třída CDC](../../mfc/reference/cdc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
