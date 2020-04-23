---
title: CDataPathProperty – třída
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
ms.openlocfilehash: 479f5d47d9cff72d36dbd25e434182af1ba01ef4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754648"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty – třída

Implementuje vlastnost ovládacího prvku OLE, kterou lze načíst asynchronně.

## <a name="syntax"></a>Syntaxe

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Vytvoří `CDataPathProperty` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDataPathProperty::Ovládací prvek GetControl](#getcontrol)|Načte asynchronní ovládací prvek OLE `CDataPathProperty` přidružený k objektu.|
|[CDataPathProperty::GetPath](#getpath)|Načte název cesty vlastnosti.|
|[CDataPathProperty::Otevřít](#open)|Zahájí načítání asynchronní vlastnosti pro přidružený ovládací prvek ActiveX (OLE).|
|[CDataPathProperty::Obnovit data](#resetdata)|Volání `CAsyncMonikerFile::OnDataAvailable` upozornit kontejneru, že vlastnosti ovládacího prvku byly změněny.|
|[CDataPathProperty::SetControl](#setcontrol)|Nastaví asynchronní ovládací prvek ActiveX (OLE) přidružený k vlastnosti.|
|[CDataPathProperty::SetPath](#setpath)|Nastaví název cesty vlastnosti.|

## <a name="remarks"></a>Poznámky

Asynchronní vlastnosti jsou načteny po synchronní iniciaci.

Třída `CDataPathProperty` je odvozena `CAysncMonikerFile`od . Chcete-li implementovat asynchronní vlastnosti v `CDataPathProperty`ovládacích prvcích OLE, odvoděte třídu z aplikace a přepište [onDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).

Další informace o použití asynchronních zástupných názvů a ovládacích prvků ActiveX v internetových aplikacích naleznete v následujících článcích:

- [První kroky Internetu: Ovládací prvky ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [První kroky internetu: Asynchronní přezdívky](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Soubor C](../../mfc/reference/cfile-class.md)

[Soubor COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[Soubor CMoniker](../../mfc/reference/cmonikerfile-class.md)

[Soubor CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="cdatapathpropertycdatapathproperty"></a><a name="cdatapathproperty"></a>CDataPathProperty::CDataPathProperty

Vytvoří `CDataPathProperty` objekt.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parametry

*pOvládací prvek*<br/>
Ukazatel na objekt ovládacího prvku OLE, který má být přidružen k tomuto `CDataPathProperty` objektu.

*lpszPath*<br/>
Cesta, která může být absolutní nebo relativní, slouží k vytvoření asynchronní zástupný název, který odkazuje na skutečné absolutní umístění vlastnosti. `CDataPathProperty`používá adresy URL, nikoli názvy souborů. Pokud chcete `CDataPathProperty` objekt pro soubor, `file://` předchlazený k cestě.

### <a name="remarks"></a>Poznámky

Objekt, `COleControl` na který *pControl* `Open` poukazuje, je používán a načten odvozenými třídami. Pokud *pControl* je NULL, `Open` ovládací prvek `SetControl`používaný s by měla být nastavena s . Pokud *lpszPath* je NULL, můžete předat `Open` cestu přes `SetPath`nebo nastavit pomocí .

## <a name="cdatapathpropertygetcontrol"></a><a name="getcontrol"></a>CDataPathProperty::Ovládací prvek GetControl

Volání této členské funkce `COleControl` načíst `CDataPathProperty` objekt přidružený k objektu.

```
COleControl* GetControl();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na ovládací prvek `CDataPathProperty` OLE přidružený k objektu. Null, pokud není přidružen ovládací prvek.

## <a name="cdatapathpropertygetpath"></a><a name="getpath"></a>CDataPathProperty::GetPath

Volání této členské funkce k načtení `CDataPathProperty` cesty, nastavit, kdy `Open`byl objekt vytvořen nebo `SetPath` zadán v aplikaci nebo zadán v předchozím volání členské funkce.

```
CString GetPath() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí název cesty k samotné vlastnosti. Může být prázdný, pokud nebyla zadána žádná cesta.

## <a name="cdatapathpropertyopen"></a><a name="open"></a>CDataPathProperty::Otevřít

Volání této členské funkce k zahájení načítání asynchronní vlastnosti pro přidružený ovládací prvek.

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

*pOvládací prvek*<br/>
Ukazatel na objekt ovládacího prvku OLE, který má být přidružen k tomuto `CDataPathProperty` objektu.

*chyba*<br/>
Ukazatel na výjimku souboru. V případě chyby, bude nastavena na příčinu.

*lpszPath*<br/>
Cesta, která může být absolutní nebo relativní, slouží k vytvoření asynchronní zástupný název, který odkazuje na skutečné absolutní umístění vlastnosti. `CDataPathProperty`používá adresy URL, nikoli názvy souborů. Pokud chcete `CDataPathProperty` objekt pro soubor, `file://` předchlazený k cestě.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Funkce se pokusí získat `IBindHost` rozhraní z ovládacího prvku.

Před `Open` voláním bez cesty musí být nastavena hodnota cesty vlastnosti. To lze provést při vytvoření objektu nebo `SetPath` voláním členské funkce.

Před `Open` voláním bez ovládacího prvku lze k objektu přidružit ovládací prvek ActiveX (dříve označovaný jako ovládací prvek OLE). To lze provést při vytvoření objektu nebo `SetControl`voláním .

Všechna přetížení [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) jsou také `CDataPathProperty`k dispozici od .

## <a name="cdatapathpropertyresetdata"></a><a name="resetdata"></a>CDataPathProperty::Obnovit data

Volání této funkce `CAsyncMonikerFile::OnDataAvailable` získat upozornit kontejneru, že vlastnosti ovládacího prvku se změnily a všechny informace načtené asynchronně již není užitečné.

```
virtual void ResetData();
```

### <a name="remarks"></a>Poznámky

Otevření by mělo být restartováno. Odvozené třídy můžete přepsat tuto funkci pro různé výchozí hodnoty.

## <a name="cdatapathpropertysetcontrol"></a><a name="setcontrol"></a>CDataPathProperty::SetControl

Volání této členské funkce přidružit asynchronní ovládací prvek OLE s objektem. `CDataPathProperty`

```cpp
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>Parametry

*pOvládací prvek*<br/>
Ukazatel na asynchronní ovládací prvek OLE, který má být přidružen k vlastnosti.

## <a name="cdatapathpropertysetpath"></a><a name="setpath"></a>CDataPathProperty::SetPath

Volání této členské funkce nastavit název cesty vlastnosti.

```cpp
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
Cesta, která může být absolutní nebo relativní, k vlastnosti načítají asynchronně. `CDataPathProperty`používá adresy URL, nikoli názvy souborů. Pokud chcete `CDataPathProperty` objekt pro soubor, `file://` předchlazený k cestě.

## <a name="see-also"></a>Viz také

[Ukázkový obrázek knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile – třída](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile – třída](../../mfc/reference/casyncmonikerfile-class.md)
