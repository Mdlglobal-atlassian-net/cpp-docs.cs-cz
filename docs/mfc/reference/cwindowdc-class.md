---
title: CWindowDC – třída
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
ms.openlocfilehash: 0ef9b4917dc834eb8335690f9b0d171245f5c170
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502157"
---
# <a name="cwindowdc-class"></a>CWindowDC – třída

Odvozeno `CDC`z.

## <a name="syntax"></a>Syntaxe

```
class CWindowDC : public CDC
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|`CWindowDC` Vytvoří objekt.|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|HWND, ke kterému `CWindowDC` je připojen.|

## <a name="remarks"></a>Poznámky

Zavolá funkci systému Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)v době vytváření a [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) v čase zničení. To znamená, že `CWindowDC` objekt přistupuje k celé oblasti obrazovky [CWnd](../../mfc/reference/cwnd-class.md) (klienta i neklientské oblasti).

Další informace o použití `CWindowDC`naleznete v tématu [Kontexty zařízení](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Požadavky

Záhlaví: afxwin. h

##  <a name="cwindowdc"></a>CWindowDC::CWindowDC

Vytvoří objekt, který přistupuje k celé oblasti obrazovky (klienta i neklientu) `CWnd` objektu, na který odkazuje *pWnd*. `CWindowDC`

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Okno, jehož klientská oblast bude mít přístup k objektu kontextu zařízení.

### <a name="remarks"></a>Poznámky

Konstruktor volá funkci systému Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc).

Pokud volání Windows `GetWindowDC` neproběhne `CResourceException`úspěšně, je vyvolána výjimka (typu). Kontext zařízení nemusí být k dispozici, pokud systém Windows již přidělil všechny své dostupné kontexty zařízení. Vaše aplikace soutěží o pět běžných kontextů zobrazení dostupných v daném čase v systému Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

##  <a name="m_hwnd"></a>CWindowDC::m_hWnd

HWND `CWnd` ukazatele se používá k `CWindowDC` vytvoření objektu.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Poznámky

`m_hWnd`je chráněná proměnná typu HWND.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CWindowDC:: CWindowDC](#cwindowdc).

## <a name="see-also"></a>Viz také:

[CDC – třída](../../mfc/reference/cdc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDC – třída](../../mfc/reference/cdc-class.md)
