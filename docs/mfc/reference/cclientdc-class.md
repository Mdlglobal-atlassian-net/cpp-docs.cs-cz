---
title: Cclientdc – třída
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
ms.openlocfilehash: 1c506e1fe3d36b9f356f8ef250e0310a10a917cc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284109"
---
# <a name="cclientdc-class"></a>Cclientdc – třída

Se postará o volání funkcí Windows [GetDC](/windows/desktop/api/winuser/nf-winuser-getdc) v době konstrukce a [ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc) v době zničení.

## <a name="syntax"></a>Syntaxe

```
class CClientDC : public CDC
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CClientDC::CClientDC](#cclientdc)|Vytvoří `CClientDC` připojen k objektu `CWnd`.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CClientDC::m_hWnd](#m_hwnd)|HWND okno, pro které bude tato `CClientDC` je platný.|

## <a name="remarks"></a>Poznámky

To znamená, že zařízení kontext přidružený k `CClientDC` objekt je klientské oblasti okna.

Další informace o `CClientDC`, naleznete v tématu [kontexty zařízení](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cclientdc"></a>  CClientDC::CClientDC

Vytvoří `CClientDC` objekt, který přistupuje ke klientské oblasti [CWnd](../../mfc/reference/cwnd-class.md) odkazované *pWnd*.

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Okno, jehož klientské oblasti bude mít přístup k objektu kontextu zařízení.

### <a name="remarks"></a>Poznámky

Konstruktor zavolá funkci Windows [GetDC](/windows/desktop/api/winuser/nf-winuser-getdc).

Výjimky (typu `CResourceException`) je vyvolána, pokud Windows `GetDC` volání selže. Kontext zařízení nemusí být k dispozici, pokud Windows má již přiděleno všechny jeho kontexty zařízení k dispozici. Vaše aplikace bojuje pěti běžných zobrazení kontextů k dispozici v daném okamžiku v části Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CClientDC::m_hWnd

`HWND` z `CWnd` použitý k vytvoření ukazatele `CClientDC` objektu.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Poznámky

*m_hWnd* je chráněná proměnná.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CClientDC::CClientDC](#cclientdc).

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC MDI](../../visual-cpp-samples.md)<br/>
[CDC – třída](../../mfc/reference/cdc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDC – třída](../../mfc/reference/cdc-class.md)
