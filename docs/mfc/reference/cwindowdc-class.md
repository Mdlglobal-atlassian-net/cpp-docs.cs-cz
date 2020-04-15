---
title: Třída CWindowDC
ms.date: 11/04/2016
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
ms.openlocfilehash: 89a822280ddebca942016f9a3a334a7128d8456a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371982"
---
# <a name="cwindowdc-class"></a>Třída CWindowDC

Odvozeno `CDC`od .

## <a name="syntax"></a>Syntaxe

```
class CWindowDC : public CDC
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|Vytvoří `CWindowDC` objekt.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|HWND, ke `CWindowDC` kterému je připojen.|

## <a name="remarks"></a>Poznámky

Volá funkci Systému Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)v době výstavby a [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) v době zničení. To znamená, `CWindowDC` že objekt přistupuje k celé oblasti obrazovky [CWnd](../../mfc/reference/cwnd-class.md) (klientské i neklientské oblasti).

Další informace o `CWindowDC`použití naleznete v [tématu Kontexty zařízení](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Požadavky

Záhlaví: afxwin.h

## <a name="cwindowdccwindowdc"></a><a name="cwindowdc"></a>CWindowDC::CWindowDC

Vytvoří `CWindowDC` objekt, který přistupuje k celé oblasti obrazovky `CWnd` (klient i neklient) objektu, na který se vztahuje *pWnd*.

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Okno, jehož klientské oblasti objekt kontextu zařízení bude přistupovat.

### <a name="remarks"></a>Poznámky

Konstruktor volá funkci Systému Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc).

Výjimka (typu) `CResourceException`je vyvolána, `GetWindowDC` pokud se nezdaří volání systému Windows. Kontext zařízení nemusí být k dispozici, pokud systém Windows již přidělil všechny své dostupné kontexty zařízení. Vaše aplikace soutěží o pět běžných kontextů zobrazení, které jsou k dispozici v daném okamžiku v systému Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

## <a name="cwindowdcm_hwnd"></a><a name="m_hwnd"></a>CWindowDC::m_hWnd

HWND `CWnd` ukazatele se používá k `CWindowDC` vytvoření objektu.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Poznámky

`m_hWnd`je chráněná proměnná typu HWND.

### <a name="example"></a>Příklad

  Viz příklad pro [CWindowDC::CWindowDC](#cwindowdc).

## <a name="see-also"></a>Viz také

[Třída CDC](../../mfc/reference/cdc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CDC](../../mfc/reference/cdc-class.md)
