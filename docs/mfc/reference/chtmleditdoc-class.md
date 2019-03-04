---
title: CHtmlEditDoc Class
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
helpviewer_keywords:
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
ms.openlocfilehash: f468de46cf6d8a8bfcd60521df8b1076a98f0735
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285331"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc Class

S [CHtmlEditView](../../mfc/reference/chtmleditview-class.md), poskytuje funkce úprav platformy WebBrowser v rámci kontextu architektury zobrazení dokumentu MFC.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|Vytvoří `CHtmlEditDoc` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHtmlEditDoc::GetView](#getview)|Načte `CHtmlEditView` objekt připojené k tomuto dokumentu.|
|[CHtmlEditDoc::IsModified](#ismodified)|Vrátí, zda ovládací prvek WebBrowser přidružené zobrazení obsahuje dokument, který byl změněn uživatelem.|
|[CHtmlEditDoc::OpenURL](#openurl)|Otevře adresu URL.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>Požadavky

**Header:** afxhtml.h

##  <a name="chtmleditdoc"></a>  CHtmlEditDoc::CHtmlEditDoc

Vytvoří `CHtmlEditDoc` objektu.

```
CHtmlEditDoc();
```

##  <a name="getview"></a>  CHtmlEditDoc::GetView

Načte [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) objekt připojené k tomuto dokumentu.

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na dokument `CHtmlEditView` objektu.

##  <a name="ismodified"></a>  CHtmlEditDoc::IsModified

Vrátí, zda ovládací prvek WebBrowser přidružené zobrazení obsahuje dokument, který byl změněn uživatelem.

```
virtual BOOL IsModified();
```

##  <a name="openurl"></a>  CHtmlEditDoc::OpenURL

Otevře adresu URL.

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
Chcete-li otevřít adresu URL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

## <a name="see-also"></a>Viz také:

[Ukázka HTMLEdit](../../visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
