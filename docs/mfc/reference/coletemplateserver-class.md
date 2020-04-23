---
title: Třída COleTemplateServer
ms.date: 11/04/2016
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
ms.openlocfilehash: 561da5060aae3c938dc3e55d0310718a881c1a3b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753723"
---
# <a name="coletemplateserver-class"></a>Třída COleTemplateServer

Používá se pro servery vizuální úpravy OLE, automatizační servery a kontejnery propojení (aplikace, které podporují odkazy na vkládání).

## <a name="syntax"></a>Syntaxe

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|Vytvoří `COleTemplateServer` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleTemplateServer::Šablona ConnectTemplate](#connecttemplate)|Připojí šablonu dokumentu k `COleObjectFactory` podkladovému objektu.|
|[COleTemplateServer::Zrušit registraci](#unregister)|Zruší registraci přidružené šablony dokumentu.|
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Zaregistruje typ dokumentu pomocí systémového registru OLE.|

## <a name="remarks"></a>Poznámky

Tato třída je odvozena z třídy [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); obvykle, můžete `COleTemplateServer` použít přímo, spíše než odvodit své vlastní třídy. `COleTemplateServer`ke správě dokumentů serveru používá objekt [CDocTemplate.](../../mfc/reference/cdoctemplate-class.md) Použití `COleTemplateServer` při implementaci úplného serveru, to znamená serveru, který lze spustit jako samostatnou aplikaci. Úplné servery jsou obvykle více aplikací rozhraní dokumentů (MDI), i když jsou podporovány aplikace rozhraní s jedním dokumentem (SDI). Jeden `COleTemplateServer` objekt je potřeba pro každý typ dokumentu serveru, který aplikace podporuje; To znamená, že pokud serverová aplikace podporuje listy `COleTemplateServer` i grafy, musíte mít dva objekty.

`COleTemplateServer`přepíše `OnCreateInstance` členská funkce `COleObjectFactory`definovaná . Tato členská funkce je volána rámci k vytvoření objektu Jazyka C++ správného typu.

Další informace o serverech naleznete v článku [Servery: Implementace serveru](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="coletemplateservercoletemplateserver"></a><a name="coletemplateserver"></a>COleTemplateServer::COleTemplateServer

Vytvoří `COleTemplateServer` objekt.

```
COleTemplateServer();
```

### <a name="remarks"></a>Poznámky

Stručný popis použití `COleTemplateServer` třídy naleznete v přehledu třídy [COleLinkingDoc.](../../mfc/reference/colelinkingdoc-class.md)

## <a name="coletemplateserverconnecttemplate"></a><a name="connecttemplate"></a>COleTemplateServer::Šablona ConnectTemplate

Připojí šablonu dokumentu, na kterou *pDocTemplate* ukazuje, k podkladovému objektu [COleObjectFactory.](../../mfc/reference/coleobjectfactory-class.md)

```cpp
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
Odkaz na ID třídy OLE, které šablona požaduje.

*pDocŠablona*<br/>
Ukazatel na šablonu dokumentu.

*bMultiInstance*<br/>
Označuje, zda jedna instance aplikace může podporovat více instancí. Pokud TRUE, více instancí aplikace jsou spuštěny pro každý požadavek na vytvoření objektu.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [KLÍČ CLSID](/windows/win32/com/clsid-key-hklm) v sadě Windows SDK.

## <a name="coletemplateserverunregister"></a><a name="unregister"></a>COleTemplateServer::Zrušit registraci

Zruší registraci přidružené šablony dokumentu.

```
BOOL Unregister();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

### <a name="remarks"></a>Poznámky

Zadejte poznámky

## <a name="coletemplateserverupdateregistry"></a><a name="updateregistry"></a>COleTemplateServer::UpdateRegistry

Načte informace o typu souboru z řetězce šablony dokumentu a umístí tyto informace do systémového registru OLE.

```cpp
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parametry

*nTyp aplikace*<br/>
Hodnota z OLE_APPTYPE výčtu, který je definován v AFXDISP. H. Může mít některou z následujících hodnot:

- OAT_INPLACE_SERVER Server má úplné uživatelské rozhraní serveru.

- OAT_SERVER Server podporuje pouze vkládání.

- OAT_CONTAINER Container podporuje odkazy na vložené objekty.

- OAT_DISPATCH_OBJECT Objekt `IDispatch`je schopen.

- OAT_DOC_OBJECT_SERVER Server podporuje vkládání i model komponenty Objekt dokumentu.

*rglpszRegistr*<br/>
Seznam položek, které jsou zapsány do registru pouze v případě, že neexistují žádné položky.

*rglpszOverwrite*<br/>
Seznam položek, které jsou zapsány do registru bez ohledu na to, zda existují některé předchozí položky.

*bRegistrovat*<br/>
Určuje, zda má být třída registrována. Pokud *bRegister* je TRUE, třída je registrována v systémovém registru. V opačném případě zruší registraci třídy.

### <a name="remarks"></a>Poznámky

Registrační informace se načítají voláním [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Načtené podřetězce jsou řetězce identifikované `regFileTypeId`indexy `regFileTypeName` `fileNewName`, a , `GetDocString` jak je popsáno v referenčních stránkách.

Pokud `regFileTypeId` je podřetězec prázdný nebo `GetDocString` volání nezdaří z jiného důvodu, tato funkce se nezdaří a informace o souboru není zadán do registru.

Informace v argumentech *rglpszRegister* a *rglpszOverwrite* jsou zapsány do registru prostřednictvím volání [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass). Výchozí informace, která je registrována, pokud jsou dva argumenty NULL, je vhodná pro většinu aplikací. Informace o struktuře informací v těchto argumentech naleznete v tématu `AfxOleRegisterServerClass`.

Další informace naleznete [v tématu Implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory – třída](../../mfc/reference/coleobjectfactory-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)
