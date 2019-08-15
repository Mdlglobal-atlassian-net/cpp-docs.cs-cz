---
title: CClientDC – – třída
ms.date: 11/04/2016
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
ms.openlocfilehash: 46428740d052c70218d4443395777428cdf3c3b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507340"
---
# <a name="cclientdc-class"></a>CClientDC – – třída

Postará o volání funkcí Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) v době konstrukce a [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) v době zničení.

## <a name="syntax"></a>Syntaxe

```
class CClientDC : public CDC
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CClientDC::CClientDC](#cclientdc)|Vytvoří objekt připojený k `CWnd`. `CClientDC`|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|[CClientDC::m_hWnd](#m_hwnd)|HWND okna, pro které je toto `CClientDC` platné.|

## <a name="remarks"></a>Poznámky

To znamená, že kontext zařízení přidružený `CClientDC` k objektu je klientská oblast okna.

Další informace o `CClientDC`najdete v tématu [Kontexty zařízení](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cclientdc"></a>CClientDC –:: CClientDC –

Vytvoří objekt, který přistupuje k oblasti klienta [CWnd](../../mfc/reference/cwnd-class.md) , na kterou odkazuje *pWnd.* `CClientDC`

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Okno, jehož klientská oblast bude přistupovat k objektu kontextu zařízení.

### <a name="remarks"></a>Poznámky

Konstruktor volá funkci systému Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc).

Pokud volání Windows `GetDC` neproběhne `CResourceException`úspěšně, je vyvolána výjimka (typu). Kontext zařízení nemusí být k dispozici, pokud systém Windows již přidělil všechny své dostupné kontexty zařízení. Vaše aplikace soutěží o pět běžných kontextů zobrazení dostupných v daném čase v systému Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

##  <a name="m_hwnd"></a>CClientDC –:: m_hWnd

Ukazatel, který slouží k vytvoření objektu.`CClientDC` `HWND` `CWnd`

```
HWND m_hWnd;
```

### <a name="remarks"></a>Poznámky

*m_hWnd* je chráněná proměnná.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CClientDC –:: CClientDC –](#cclientdc).

## <a name="see-also"></a>Viz také:

[Ukázka MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[CDC – třída](../../mfc/reference/cdc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDC – třída](../../mfc/reference/cdc-class.md)
