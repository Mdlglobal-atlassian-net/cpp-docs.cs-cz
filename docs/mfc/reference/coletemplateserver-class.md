---
title: COleTemplateServer – třída
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
ms.openlocfilehash: 4a1997497f3bddb405b712b5534f76e577dabfa8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503083"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer – třída

Používá se pro servery vizuálních úprav OLE, automatizační servery a kontejnery odkazů (aplikace, které podporují odkazy na vložení).

## <a name="syntax"></a>Syntaxe

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|`COleTemplateServer` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleTemplateServer:: ConnectTemplate](#connecttemplate)|Připojí šablonu dokumentu k základnímu `COleObjectFactory` objektu.|
|[COleTemplateServer::Unregister](#unregister)|Zruší registraci přidružené šablony dokumentu.|
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Registruje typ dokumentu pomocí systémového registru OLE.|

## <a name="remarks"></a>Poznámky

Tato třída je odvozena od třídy [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); obvykle můžete použít `COleTemplateServer` přímo místo odvozování vlastní třídy. `COleTemplateServer`ke správě dokumentů na serveru používá objekt [CDocTemplate –](../../mfc/reference/cdoctemplate-class.md) . Použijte `COleTemplateServer` při implementaci úplného serveru, tedy serveru, který lze spustit jako samostatnou aplikaci. Úplné servery jsou obvykle aplikace s více dokumenty (MDI), přestože jsou podporovány aplikace rozhraní SDI (Single Document Interface). Jeden `COleTemplateServer` objekt je potřeba pro každý typ dokumentu serveru, který podporuje aplikace. to znamená, že pokud vaše serverová aplikace podporuje listy i grafy, musíte mít dva `COleTemplateServer` objekty.

`COleTemplateServer`přepíše členskou funkci definovanou pomocí `COleObjectFactory`. `OnCreateInstance` Tato členská funkce je volána rozhraním pro vytvoření C++ objektu správného typu.

Další informace o serverech najdete v článku [servery: Implementace serveru](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

##  <a name="coletemplateserver"></a>COleTemplateServer:: COleTemplateServer

`COleTemplateServer` Vytvoří objekt.

```
COleTemplateServer();
```

### <a name="remarks"></a>Poznámky

Stručný popis použití `COleTemplateServer` třídy naleznete v přehledu třídy [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) .

##  <a name="connecttemplate"></a>COleTemplateServer:: ConnectTemplate

Připojí šablonu dokumentu, na kterou odkazuje *pDocTemplate* , na podkladový objekt [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) .

```
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>Parametry

*CLSID*<br/>
Odkaz na ID třídy OLE, kterou šablona požaduje

*pDocTemplate*<br/>
Ukazatel na šablonu dokumentu.

*bMultiInstance*<br/>
Označuje, zda jedna instance aplikace může podporovat více instancí. Při hodnotě TRUE se pro každý požadavek na vytvoření objektu spustí více instancí aplikace.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [klíč CLSID](/windows/win32/com/clsid-key-hklm) v Windows SDK.

##  <a name="unregister"></a>COleTemplateServer:: Unregister

Zruší registraci přidružené šablony dokumentu.

```
BOOL Unregister();
```

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

EnterRemarks

##  <a name="updateregistry"></a>COleTemplateServer:: UpdateRegistry

Načte informace o typu souboru z řetězce šablony dokumentu a umístí tyto informace do systémového registru OLE.

```
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parametry

*nAppType*<br/>
Hodnota z výčtu OLE_APPTYPE, která je definována v AFXDISP. Y. Může mít jednu z následujících hodnot:

- Server OAT_INPLACE_SERVER má úplné uživatelské rozhraní serveru.

- OAT_SERVER Server podporuje pouze vkládání.

- Kontejner OAT_CONTAINER podporuje odkazy na vložené objekty.

- Objekt OAT_DISPATCH_OBJECT je `IDispatch`schopný.

- Server OAT_DOC_OBJECT_SERVER podporuje vkládání i model komponent objektu dokumentu.

*rglpszRegister*<br/>
Seznam záznamů, které jsou zapsány do registru pouze v případě, že žádné položky neexistují.

*rglpszOverwrite*<br/>
Seznam záznamů, které jsou zapsány do registru bez ohledu na to, zda nějaké předchozí položky existují.

*bRegister*<br/>
Určuje, zda má být třída registrována. Pokud má *bRegister* hodnotu true, třída je zaregistrována v registru systému. V opačném případě zruší registraci třídy.

### <a name="remarks"></a>Poznámky

Informace o registraci jsou načteny prostřednictvím volání metody [CDocTemplate –:: GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Načtené podřetězce jsou ty, které jsou identifikovány `regFileTypeId`indexy `regFileTypeName`, a `fileNewName`, jak je popsáno `GetDocString` na odkazových stránkách.

Pokud je podřetězec prázdný nebo pokud se `GetDocString` volání nezdařilo z jiného důvodu, tato funkce se nezdařila a informace o souboru nejsou v registru zadány. `regFileTypeId`

Informace v argumentech *rglpszRegister* a *rglpszOverwrite* se zapisují do registru prostřednictvím volání [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass). Výchozí informace, které jsou registrovány v případě, že jsou dva argumenty NULL, jsou vhodné pro většinu aplikací. Informace o struktuře informací v těchto argumentech naleznete v tématu `AfxOleRegisterServerClass`.

Další informace naleznete v tématu [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

## <a name="see-also"></a>Viz také:

[HIERSVR Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory – třída](../../mfc/reference/coleobjectfactory-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc – třída](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)
