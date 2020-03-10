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
ms.openlocfilehash: 89cb8ddcdd42643f52f755516e8845109163c57a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890821"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty – třída

Implementuje vlastnost ovládacího prvku OLE, která může být načtena asynchronně.

## <a name="syntax"></a>Syntaxe

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Vytvoří objekt `CDataPathProperty`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDataPathProperty:: GetControl](#getcontrol)|Načte asynchronní ovládací prvek OLE přidružený k objektu `CDataPathProperty`.|
|[CDataPathProperty:: GetPath](#getpath)|Načte cestu k vlastnosti.|
|[CDataPathProperty:: Open](#open)|Inicializuje načítání asynchronní vlastnosti pro přidružený ovládací prvek ActiveX (OLE).|
|[CDataPathProperty:: resetdata](#resetdata)|Volá `CAsyncMonikerFile::OnDataAvailable` pro oznámení kontejneru, že došlo ke změně vlastností ovládacího prvku.|
|[CDataPathProperty::SetControl](#setcontrol)|Nastaví asynchronní ovládací prvek ActiveX (OLE) přidružený k vlastnosti.|
|[CDataPathProperty::SetPath](#setpath)|Nastaví cestu k vlastnosti.|

## <a name="remarks"></a>Poznámky

Asynchronní vlastnosti jsou načteny po synchronním spuštění.

Třída `CDataPathProperty` je odvozena od `CAysncMonikerFile`. Chcete-li implementovat asynchronní vlastnosti v ovládacích prvcích OLE, odvodit třídu z `CDataPathProperty`a přepsat [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).

Další informace o použití asynchronních monikerů a ovládacích prvků ActiveX v internetových aplikacích naleznete v následujících článcích:

- [První kroky Internetu: ovládací prvky ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [První kroky pro Internet: asynchronní monikery](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CFile –](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXCTL. h

##  <a name="cdatapathproperty"></a>CDataPathProperty::CDataPathProperty

Vytvoří objekt `CDataPathProperty`.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
Ukazatel na objekt ovládacího prvku OLE, který má být přidružen k tomuto objektu `CDataPathProperty`.

*lpszPath*<br/>
Cesta, která může být absolutní nebo relativní, používaná k vytvoření asynchronního monikeru, který odkazuje na skutečné absolutní umístění vlastnosti. `CDataPathProperty` používá adresy URL, nikoli názvy souborů. Pokud chcete `CDataPathProperty` objekt pro soubor, přiřaďte k cestě `file://`.

### <a name="remarks"></a>Poznámky

Objekt `COleControl`, na který odkazuje *pControl* , je používán `Open` a načten odvozenými třídami. Pokud má *pControl* hodnotu null, ovládací prvek použitý u `Open` by měl být nastaven s `SetControl`. Pokud má *lpszPath* hodnotu null, můžete cestu předat pomocí `Open` nebo nastavit `SetPath`.

##  <a name="getcontrol"></a>CDataPathProperty:: GetControl

Voláním této členské funkce načtěte objekt `COleControl` přidružený k objektu `CDataPathProperty`.

```
COleControl* GetControl();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na ovládací prvek OLE přidružený k objektu `CDataPathProperty`. Hodnota NULL, pokud není ovládací prvek přidružen.

##  <a name="getpath"></a>CDataPathProperty:: GetPath

Voláním této členské funkce načtete cestu, nastavíte, kdy byl objekt `CDataPathProperty` vytvořen nebo zadán v `Open`nebo zadán v předchozím volání členské funkce `SetPath`.

```
CString GetPath() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí cestu k samotné vlastnosti. Může být prázdné, pokud nebyla zadána žádná cesta.

##  <a name="open"></a>CDataPathProperty:: Open

Zavolejte tuto členskou funkci pro zahájení načítání asynchronní vlastnosti pro přidružený ovládací prvek.

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
Ukazatel na objekt ovládacího prvku OLE, který má být přidružen k tomuto objektu `CDataPathProperty`.

*pError*<br/>
Ukazatel na výjimku souboru. V případě chyby bude nastavena na příčinu.

*lpszPath*<br/>
Cesta, která může být absolutní nebo relativní, používaná k vytvoření asynchronního monikeru, který odkazuje na skutečné absolutní umístění vlastnosti. `CDataPathProperty` používá adresy URL, nikoli názvy souborů. Pokud chcete `CDataPathProperty` objekt pro soubor, přiřaďte k cestě `file://`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Funkce se pokusí získat rozhraní `IBindHost` z ovládacího prvku.

Před voláním `Open` bez cesty musí být nastavena hodnota pro cestu vlastnosti. To lze provést, když je objekt vytvořen, nebo voláním členské funkce `SetPath`.

Před voláním `Open` bez ovládacího prvku může být k objektu přidružen ovládací prvek ActiveX (dříve označovaný jako ovládací prvek OLE). To lze provést, když je objekt vytvořen, nebo voláním `SetControl`.

Všechna přetížení [CAsyncMonikerFile:: Open](../../mfc/reference/casyncmonikerfile-class.md#open) jsou také k dispozici z `CDataPathProperty`.

##  <a name="resetdata"></a>CDataPathProperty:: resetdata

Voláním této funkce načtete `CAsyncMonikerFile::OnDataAvailable` pro oznamování kontejneru, že se změnily vlastnosti ovládacího prvku, a všechny informace načtené asynchronně již nejsou užitečné.

```
virtual void ResetData();
```

### <a name="remarks"></a>Poznámky

Otevření by mělo být restartováno. Odvozené třídy mohou tuto funkci přepsat pro různé výchozí hodnoty.

##  <a name="setcontrol"></a>CDataPathProperty::SetControl

Zavolejte tuto členskou funkci pro přidružení asynchronního ovládacího prvku OLE k objektu `CDataPathProperty`.

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
Ukazatel na asynchronní ovládací prvek OLE, který má být přidružen k vlastnosti.

##  <a name="setpath"></a>CDataPathProperty::SetPath

Chcete-li nastavit cestu vlastnosti, zavolejte tuto členskou funkci.

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
Cesta, která může být absolutní nebo relativní, na vlastnost, která je načítána asynchronně. `CDataPathProperty` používá adresy URL, nikoli názvy souborů. Pokud chcete `CDataPathProperty` objekt pro soubor, přiřaďte k cestě `file://`.

## <a name="see-also"></a>Viz také

[Ukázkový obrázek MFC](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile – třída](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile – třída](../../mfc/reference/casyncmonikerfile-class.md)
