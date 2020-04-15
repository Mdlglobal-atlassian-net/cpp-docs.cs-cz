---
title: Třída CHtmlEditDoc
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
ms.openlocfilehash: 8b500f651da1a73040fdb0469f2f023babe25e85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352164"
---
# <a name="chtmleditdoc-class"></a>Třída CHtmlEditDoc

S [CHtmlEditView](../../mfc/reference/chtmleditview-class.md), poskytuje funkce platformy pro úpravy WebBrowser v kontextu architektury zobrazení dokumentu knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|Vytvoří `CHtmlEditDoc` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CHtmlEditDoc::GetView](#getview)|Načte `CHtmlEditView` objekt připojený k tomuto dokumentu.|
|[ChtmlEditDoc::IsModified](#ismodified)|Vrátí, zda ovládací prvek WebBrowser přidruženého zobrazení obsahuje dokument, který byl změněn uživatelem.|
|[CHtmlEditDoc::OpenURL](#openurl)|Otevře adresu URL.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[CDokument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxhtml.h

## <a name="chtmleditdocchtmleditdoc"></a><a name="chtmleditdoc"></a>CHtmlEditDoc::CHtmlEditDoc

Vytvoří `CHtmlEditDoc` objekt.

```
CHtmlEditDoc();
```

## <a name="chtmleditdocgetview"></a><a name="getview"></a>CHtmlEditDoc::GetView

Načte objekt [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) připojený k tomuto dokumentu.

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `CHtmlEditView` objekt dokumentu.

## <a name="chtmleditdocismodified"></a><a name="ismodified"></a>ChtmlEditDoc::IsModified

Vrátí, zda ovládací prvek WebBrowser přidruženého zobrazení obsahuje dokument, který byl změněn uživatelem.

```
virtual BOOL IsModified();
```

## <a name="chtmleditdocopenurl"></a><a name="openurl"></a>CHtmlEditDoc::OpenURL

Otevře adresu URL.

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
Adresa URL, kterou chcete otevřít.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="see-also"></a>Viz také

[HtmlEdit ukázka](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
