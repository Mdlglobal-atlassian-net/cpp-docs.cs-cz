---
title: CDataPathProperty Class
ms.date: 11/04/2016
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
ms.openlocfilehash: 61c8dfa85363509ee09eaaccdb6d45d70390c344
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262763"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty Class

Implementuje ovládacího prvku OLE vlastnost, která lze načíst asynchronně.

## <a name="syntax"></a>Syntaxe

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Vytvoří `CDataPathProperty` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDataPathProperty::GetControl](#getcontrol)|Načte přidružený ovládací prvek asynchronní OLE `CDataPathProperty` objektu.|
|[CDataPathProperty::GetPath](#getpath)|Načte vlastnosti názvu cesty.|
|[CDataPathProperty::Open](#open)|Iniciuje asynchronní vlastnosti ovládacího prvku ActiveX (OLE) přidružené načítání.|
|[CDataPathProperty::ResetData](#resetdata)|Volání `CAsyncMonikerFile::OnDataAvailable` oznámit kontejneru, který jste změnili vlastnosti ovládacího prvku.|
|[CDataPathProperty::SetControl](#setcontrol)|Nastaví asynchronní ovládacího prvku ActiveX (OLE) přidružený k vlastnosti.|
|[CDataPathProperty::SetPath](#setpath)|Nastaví cestu vlastnosti.|

## <a name="remarks"></a>Poznámky

Asynchronní vlastnosti jsou načteny po zahájení synchronní.

Třída `CDataPathProperty` je odvozen z `CAysncMonikerFile`. K implementaci asynchronního vlastnosti v ovládací prvky OLE, odvoďte třídu z `CDataPathProperty`a přepsat [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).

Další informace o tom, jak použít asynchronní monikery a ovládací prvky ActiveX v internetových aplikací najdete v následujících článcích:

- [První kroky Internetu: Ovládací prvky ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [První kroky Internetu: Asynchronní Monikery](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

##  <a name="cdatapathproperty"></a>  CDataPathProperty::CDataPathProperty

Vytvoří `CDataPathProperty` objektu.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
Ukazatel na objekt ovládacího prvku OLE mají být spojeny s tímto `CDataPathProperty` objektu.

*lpszPath*<br/>
Cesty, která může být absolutní nebo relativní, je použít k vytvoření asynchronní monikeru, který odkazuje na aktuální absolutní umístění vlastnost. `CDataPathProperty` pomocí adresy URL, ne názvy souborů. Pokud chcete, aby `CDataPathProperty` objektu pro soubor, předřaďte `file://` k cestě.

### <a name="remarks"></a>Poznámky

`COleControl` Objekt, který odkazuje *pControl* používá `Open` a načíst z odvozených tříd. Pokud *pControl* má hodnotu NULL, ovládací prvek použitý s `Open` by měla být nastavena s `SetControl`. Pokud *lpszPath* má hodnotu NULL, můžete předat cestu prostřednictvím `Open` nebo ji nastavte `SetPath`.

##  <a name="getcontrol"></a>  CDataPathProperty::GetControl

Voláním této členské funkce k načtení `COleControl` objekt přidružený k `CDataPathProperty` objektu.

```
COleControl* GetControl();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí přidružený ukazatel na ovládací prvek OLE `CDataPathProperty` objektu. Hodnota NULL, pokud není ovládací prvek souvisí.

##  <a name="getpath"></a>  CDataPathProperty::GetPath

Zavolat tuto členskou funkci, chcete-li načíst cestu, nastavit, když `CDataPathProperty` objekt byl vytvořen nebo podle `Open`, zadané v předchozí volání nebo `SetPath` členskou funkci.

```
CString GetPath() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí cestu k samotné vlastnosti. Může být prázdný, pokud nebyla zadána žádná cesta.

##  <a name="open"></a>  CDataPathProperty::Open

Voláním této členské funkce k zahájení načítání asynchronní vlastnosti pro přidružený ovládací prvek.

```
virtual BOOL Open(
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    CFileException* pError = NULL);

virtual BOOL Open(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
Ukazatel na objekt ovládacího prvku OLE mají být spojeny s tímto `CDataPathProperty` objektu.

*pError*<br/>
Ukazatel na soubor výjimku. V případě chyby nastaví se na příčinu.

*lpszPath*<br/>
Cesty, která může být absolutní nebo relativní, je použít k vytvoření asynchronní monikeru, který odkazuje na aktuální absolutní umístění vlastnost. `CDataPathProperty` pomocí adresy URL, ne názvy souborů. Pokud chcete, aby `CDataPathProperty` objektu pro soubor, předřaďte `file://` k cestě.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Funkce se pokusí získat `IBindHost` rozhraní z ovládacího prvku.

Před voláním `Open` bez cesty, musí být nastavena hodnota pro cestu vlastnosti. To můžete udělat, když je objekt vytvořený, nebo pomocí volání `SetPath` členskou funkci.

Před voláním `Open` bez ovládací prvek může být přidružený k objektu ovládacího prvku ActiveX (dříve označované jako ovládací prvek OLE). To můžete udělat, když je objekt vytvořený, nebo pomocí volání `SetControl`.

Všechna přetížení [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) jsou dostupné i z `CDataPathProperty`.

##  <a name="resetdata"></a>  CDataPathProperty::ResetData

Voláním této funkce získáte `CAsyncMonikerFile::OnDataAvailable` kontejneru upozornit, že jste změnili vlastnosti ovládacích prvků a všechny informace, které jsou načítána asynchronně již není používána.

```
virtual void ResetData();
```

### <a name="remarks"></a>Poznámky

Otevření by měla být restartována. Odvozené třídy mohou přepsat tuto funkci pro různé výchozí hodnoty.

##  <a name="setcontrol"></a>  CDataPathProperty::SetControl

Voláním této členské funkce pro přidružení asynchronní ovládací prvek OLE se `CDataPathProperty` objektu.

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
Ukazatel na asynchronní ovládací prvek OLE má být přidružena k vlastnosti.

##  <a name="setpath"></a>  CDataPathProperty::SetPath

Voláním této členské funkce pro nastavení vlastnosti názvu cesty.

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
Cesta, která může být absolutní nebo relativní k vlastnosti načítán asynchronně. `CDataPathProperty` pomocí adresy URL, ne názvy souborů. Pokud chcete, aby `CDataPathProperty` objektu pro soubor, předřaďte `file://` k cestě.

## <a name="see-also"></a>Viz také:

[Obrázek ukázky knihovny MFC](../../visual-cpp-samples.md)<br/>
[CAsyncMonikerFile – třída](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile – třída](../../mfc/reference/casyncmonikerfile-class.md)
