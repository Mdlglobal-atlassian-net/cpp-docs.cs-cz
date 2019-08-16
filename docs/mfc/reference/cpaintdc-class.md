---
title: CPaintDC – – třída
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
ms.openlocfilehash: d587f1cfa6ec38dd564da196da8130bffac11302
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503139"
---
# <a name="cpaintdc-class"></a>CPaintDC – – třída

Třída kontextu zařízení odvozená z [CDC](../../mfc/reference/cdc-class.md).

## <a name="syntax"></a>Syntaxe

```
class CPaintDC : public CDC
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|Vytvoří připojení k určenému CWnd. [](../../mfc/reference/cwnd-class.md) `CPaintDC`|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Obsahuje [PAINTSTRUCT –](/windows/win32/api/winuser/ns-winuser-paintstruct) , který se používá k vykreslování klientské oblasti.|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|HWND, ke kterému je `CPaintDC` tento objekt připojen.|

## <a name="remarks"></a>Poznámky

Provádí v době zničení [CWnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) v době vytváření a [CWnd:: EndPaint](../../mfc/reference/cwnd-class.md#endpaint) .

Objekt lze použít pouze při reakci na zprávu [WM_PAINT](/windows/win32/gdi/wm-paint) , obvykle ve vaší `OnPaint` členské funkci obslužné rutiny zpráv. `CPaintDC`

Další informace o použití `CPaintDC`naleznete v tématu [Kontexty zařízení](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cpaintdc"></a>CPaintDC –:: CPaintDC –

Sestaví [](/windows/win32/api/winuser/ns-winuser-paintstruct) [](#m_ps) objekt, připraví okno aplikace pro malování a ukládá strukturu PAINTSTRUCT – do členské proměnné m_ps. `CPaintDC`

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na `CWnd` objekt, ke `CPaintDC` kterému objekt patří.

### <a name="remarks"></a>Poznámky

Výjimka (typu `CResourceException`) je vyvolána, pokud se nezdařilo volání Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) . Kontext zařízení nemusí být k dispozici, pokud systém Windows již přidělil všechny své dostupné kontexty zařízení. Vaše aplikace soutěží o pět běžných kontextů zobrazení dostupných v daném čase v systému Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd

, `HWND` Ke kterému je `CPaintDC` tento objekt připojen.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Poznámky

*m_hWnd* je chráněná proměnná typu HWND.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>  CPaintDC::m_ps

`m_ps`je veřejnou členskou proměnnou typu [PAINTSTRUCT –](/windows/win32/api/winuser/ns-winuser-paintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Poznámky

Je `PAINTSTRUCT` to, který je předaný a vyplněn pomocí [CWnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

Obsahuje informace, které aplikace používá k vykreslování klientské oblasti okna přidruženého `CPaintDC` k objektu. `PAINTSTRUCT`

Všimněte si, že k popisovači kontextu zařízení můžete přistupovat prostřednictvím `PAINTSTRUCT`. K popisovači ale můžete přistupovat přímo prostřednictvím `m_hDC` členské proměnné, která `CPaintDC` dědí z operace CDC.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPaintDC –:: m_hWnd](#m_hwnd).

## <a name="see-also"></a>Viz také:

[Ukázka MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[CDC – třída](../../mfc/reference/cdc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
