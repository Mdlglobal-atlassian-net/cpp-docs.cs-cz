---
title: Třída CClientDC
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
ms.openlocfilehash: abe8a3220fd37a0375fcf37504c715edf4c6962e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352294"
---
# <a name="cclientdc-class"></a>Třída CClientDC

Postará se o volání funkcí systému Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) v době výstavby a [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) v době zničení.

## <a name="syntax"></a>Syntaxe

```
class CClientDC : public CDC
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CClientDC::CClientDC](#cclientdc)|Vytvoří `CClientDC` objekt připojený k `CWnd`.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CClientDC::m_hWnd](#m_hwnd)|HWND okna, pro které `CClientDC` je toplatné.|

## <a name="remarks"></a>Poznámky

To znamená, že kontext `CClientDC` zařízení přidružený k objektu je klientská oblast okna.

Další informace `CClientDC`naleznete v tématu [Kontexty zařízení](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cclientdccclientdc"></a><a name="cclientdc"></a>CClientDC::CClientDC

Vytvoří `CClientDC` objekt, který přistupuje k klientské oblasti [CWnd,](../../mfc/reference/cwnd-class.md) na kterou je odkazováno *pomocí pWnd*.

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Okno, jehož klientské oblasti objekt kontextu zařízení bude přistupovat.

### <a name="remarks"></a>Poznámky

Konstruktor volá funkci Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc).

Výjimka (typu) `CResourceException`je vyvolána, `GetDC` pokud se nezdaří volání systému Windows. Kontext zařízení nemusí být k dispozici, pokud systém Windows již přidělil všechny své dostupné kontexty zařízení. Vaše aplikace soutěží o pět běžných kontextů zobrazení, které jsou k dispozici v daném okamžiku v systému Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

## <a name="cclientdcm_hwnd"></a><a name="m_hwnd"></a>CClientDC::m_hWnd

Ukazatel použitý k vytvoření objektu. `CClientDC` `HWND` `CWnd`

```
HWND m_hWnd;
```

### <a name="remarks"></a>Poznámky

*m_hWnd* je chráněná proměnná.

### <a name="example"></a>Příklad

  Viz příklad [pro CClientDC::CClientDC](#cclientdc).

## <a name="see-also"></a>Viz také

[MDI vzorku knihovny MFc](../../overview/visual-cpp-samples.md)<br/>
[Třída CDC](../../mfc/reference/cdc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CDC](../../mfc/reference/cdc-class.md)
