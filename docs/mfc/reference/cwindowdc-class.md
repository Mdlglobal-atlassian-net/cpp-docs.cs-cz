---
title: Cwindowdc – třída
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
ms.openlocfilehash: eccea1893979c4491f7080d0d3dc980adaf19025
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553046"
---
# <a name="cwindowdc-class"></a>Cwindowdc – třída

Odvozené od `CDC`.

## <a name="syntax"></a>Syntaxe

```
class CWindowDC : public CDC
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|Vytvoří `CWindowDC` objektu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|HWND, ke kterému je tento `CWindowDC` je připojen.|

## <a name="remarks"></a>Poznámky

Volá funkci Windows [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc)v době konstrukce a [ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc) v době zničení. To znamená, že `CWindowDC` objektů přistupuje k oblasti celé obrazovky [CWnd](../../mfc/reference/cwnd-class.md) (klientská a neklientská oblast).

Další informace o používání `CWindowDC`, naleznete v tématu [kontexty zařízení](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Požadavky

Hlavička: afxwin.h

##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC

Vytvoří `CWindowDC` objekt, který přistupuje k oblasti celé obrazovky (klientská a neklientská) z `CWnd` objekt, který odkazuje *pWnd*.

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Okno, jehož klientské oblasti bude mít přístup k objektu kontextu zařízení.

### <a name="remarks"></a>Poznámky

Konstruktor zavolá funkci Windows [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc).

Výjimky (typu `CResourceException`) je vyvolána, pokud Windows `GetWindowDC` volání selže. Kontext zařízení nemusí být k dispozici, pokud Windows má již přiděleno všechny jeho kontexty zařízení k dispozici. Vaše aplikace bojuje pěti běžných zobrazení kontextů k dispozici v daném okamžiku v části Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd

HWND o HODNOTĚ `CWnd` ukazatele je použit pro vytvoření `CWindowDC` objektu.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Poznámky

`m_hWnd` je chráněný proměnné typu HWND.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CWindowDC::CWindowDC](#cwindowdc).

## <a name="see-also"></a>Viz také

[CDC – třída](../../mfc/reference/cdc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDC – třída](../../mfc/reference/cdc-class.md)
