---
title: CDocObjectServer – třída
ms.date: 09/12/2018
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
ms.openlocfilehash: f415df35b13e50eee092f87eca0627e5cf143720
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753293"
---
# <a name="cdocobjectserver-class"></a>CDocObjectServer – třída

Implementuje další rozhraní OLE potřebná `COleDocument` k vytvoření normálního `IOleDocument`serveru `IOleDocumentView` `IOleCommandTarget`do `IPrint`úplného serveru DocObject: , , a .

## <a name="syntax"></a>Syntaxe

```
class CDocObjectServer : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|Vytvoří `CDocObjectServer` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|Aktivuje server objektu dokumentu, ale nezobrazí jej.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CDocObjectServer::Zobrazení OnActivateView](#onactivateview)|Zobrazí zobrazení DocObject.|
|[CdocObjectServer::OnApplyViewState](#onapplyviewstate)|Obnoví stav zobrazení DocObject.|
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|Uloží stav zobrazení DocObject.|

## <a name="remarks"></a>Poznámky

`CDocObjectServer`je odvozen `CCmdTarget` z a `COleServerDoc` úzce spolupracuje s vystavit rozhraní.

Dokument serveru DocObject může obsahovat objekty [CDocObjectServerItem,](../../mfc/reference/cdocobjectserveritem-class.md) které představují rozhraní serveru pro položky DocObject.

Chcete-li přizpůsobit server DocObject, `CDocObjectServer` odvoděte vlastní třídu z funkcí nastavení zobrazení [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate)a [OnSaveViewState](#onsaveviewstate). Budete muset poskytnout novou instanci vaší třídy v reakci na volání rámci.

Další informace o docobjects naleznete v [tématu CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) a [COleCmdUI](../../mfc/reference/colecmdui-class.md) v *odkazu knihovny MFC*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdocob.h

## <a name="cdocobjectserveractivatedocobject"></a><a name="activatedocobject"></a>CDocObjectServer::ActivateDocObject

Volánítéto funkce pro aktivaci (ale nezobrazit) objektový server dokumentu.

```cpp
void ActivateDocObject();
```

### <a name="remarks"></a>Poznámky

`ActivateDocObject`volá `IOleDocumentSite`metodu ' s, `ActivateMe` ale nezobrazuje zobrazení, protože čeká na konkrétní pokyny, jak nastavit a zobrazit zobrazení uvedené ve volání [CDocObjectServer::OnActivateView](#onactivateview).

Společně `ActivateDocObject` a `OnActivateView` aktivujte a zobrazte zobrazení DocObject. DocObject aktivace se liší od jiných druhů aktivace OLE na místě. DocObject aktivace obchází zobrazení na místě šrafování hranice a objekt vylepšení (například nastavení velikosti úchyty), ignoruje funkce rozsahu objektu a kreslí posuvníky v obdélníku zobrazení na rozdíl od kreslení je mimo tento obdélník (jako v normálním místě aktivace).

## <a name="cdocobjectservercdocobjectserver"></a><a name="cdocobjectserver"></a>CDocObjectServer::CDocObjectServer

Vytvoří a inicializuje `CDocObjectServer` objekt.

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>Parametry

*pVlastník*<br/>
Ukazatel na dokument klientské lokality, který je klientem serveru DocObject.

*pDocSite*<br/>
Ukazatel na `IOleDocumentSite` rozhraní implementované kontejneru.

### <a name="remarks"></a>Poznámky

Když je aktivní DocObject, rozhraní OLE `IOleDocumentSite`klientské lokality ( ) umožňuje serveru DocObject komunikovat se svým klientem (kontejnerem). Když je aktivován server DocObject, nejprve zkontroluje, zda kontejner implementuje `IOleDocumentSite` rozhraní. Pokud ano, [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) je volána, aby zjistila, zda kontejner podporuje DocObjects. Ve výchozím `GetDocObjectServer` nastavení vrátí hodnotu NULL. Je nutné `COleServerDoc::GetDocObjectServer` přepsat vytvořit `CDocObjectServer` nový objekt nebo odvozený objekt vlastní, s `COleServerDoc` ukazateli `IOleDocumentSite` na kontejner a jeho rozhraní jako argumenty konstruktoru.

## <a name="cdocobjectserveronactivateview"></a><a name="onactivateview"></a>CDocObjectServer::Zobrazení OnActivateView

Voláním této funkce zobrazíte zobrazení DocObject.

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu chyby nebo upozornění. Ve výchozím nastavení vrátí funkce NOERROR, pokud je úspěšná; jinak E_FAIL.

### <a name="remarks"></a>Poznámky

Tato funkce vytvoří okno rámce na místě, nakreslí posuvníky v zobrazení, nastaví nabídky, které server sdílí se svým kontejnerem, přidá ovládací prvky snímků, nastaví aktivní objekt, nakonec zobrazí okno rámečku na místě a nastaví fokus.

## <a name="cdocobjectserveronapplyviewstate"></a><a name="onapplyviewstate"></a>CdocObjectServer::OnApplyViewState

Přepsáním této funkce obnovíte stav zobrazení DocObject.

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
Objekt, `CArchive` ze kterého serializovat stav zobrazení.

### <a name="remarks"></a>Poznámky

Tato funkce je volána při zobrazení poprvé po jeho vytvoření instance. `OnApplyViewState`instruuje zobrazení k opětovné inicializaci `CArchive` podle dat v objektu dříve uloženém pomocí [OnSaveViewState](#onsaveviewstate). Zobrazení musí ověřit data `CArchive` v objektu, protože kontejner se nepokouší interpretovat data stavu zobrazení žádným způsobem.

Můžete použít `OnSaveViewState` k ukládání trvalých informací specifických pro stav zobrazení. Pokud přepíšete `OnSaveViewState` ukládání informací, budete chtít `OnApplyViewState` přepsat číst tyto informace a použít je v zobrazení, když je nově aktivován.

## <a name="cdocobjectserveronsaveviewstate"></a><a name="onsaveviewstate"></a>CDocObjectServer::OnSaveViewState

Přepsáním této funkce uložíte další informace o stavu zobrazení DocObject.

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
Objekt, `CArchive` do kterého je serializován stav zobrazení.

### <a name="remarks"></a>Poznámky

Stav může zahrnovat vlastnosti, jako je typ zobrazení, faktor zvětšení, kurzor a bod výběru a tak dále. Kontejner obvykle volá tuto funkci před deaktivací zobrazení. Uložený stav lze později obnovit prostřednictvím [OnApplyViewState](#onapplyviewstate).

Můžete použít `OnSaveViewState` k ukládání trvalých informací specifických pro stav zobrazení. Pokud přepíšete `OnSaveViewState` ukládání informací, budete chtít `OnApplyViewState` přepsat číst tyto informace a použít je v zobrazení, když je nově aktivován.

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)
