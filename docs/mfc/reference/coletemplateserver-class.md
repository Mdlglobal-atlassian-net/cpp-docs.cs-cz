---
title: Coletemplateserver – třída
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
ms.openlocfilehash: bcc79f781be3a0292398e4f211ea55f5403b6b8f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302877"
---
# <a name="coletemplateserver-class"></a>Coletemplateserver – třída

Používá se pro OLE vizuálních úprav servery, automatizační servery a propojení kontejnerů (aplikace, které podporují odkazy na vložené části).

## <a name="syntax"></a>Syntaxe

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|Vytvoří `COleTemplateServer` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Šablona dokumentu se připojí k základní `COleObjectFactory` objektu.|
|[COleTemplateServer::Unregister](#unregister)|Zruší registraci přidružený dokument šablony.|
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Registruje typ dokumentu OLE systémového registru.|

## <a name="remarks"></a>Poznámky

Tato třída je odvozená od třídy [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); obvykle, můžete použít `COleTemplateServer` přímo, spíš než odvození vlastní třídy. `COleTemplateServer` používá [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objektu, který chcete spravovat dokumenty na serveru. Použití `COleTemplateServer` při implementaci plnou instalaci systému server, to znamená, že server, který může běžet jako samostatné aplikace. Úplných serverů jsou obvykle více dokumentů aplikace (MDI interface), i když jsou podporovány aplikací rozhraní (SDI) jednotlivý dokument. Jeden `COleTemplateServer` objekt je potřeba pro každý typ dokumentu serveru podporuje aplikace; to znamená, pokud vaše serverová aplikace podporuje listů a grafy, musíte mít dva `COleTemplateServer` objekty.

`COleTemplateServer` přepsání `OnCreateInstance` členské funkce definované `COleObjectFactory`. Tato členská funkce se volá se rozhraním, chcete-li vytvořit objekt jazyka C++ vhodný typ.

Další informace o serverech, najdete v článku [serverů: Implementace serveru](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

##  <a name="coletemplateserver"></a>  COleTemplateServer::COleTemplateServer

Vytvoří `COleTemplateServer` objektu.

```
COleTemplateServer();
```

### <a name="remarks"></a>Poznámky

Stručný popis použití `COleTemplateServer` najdete v tématu [colelinkingdoc –](../../mfc/reference/colelinkingdoc-class.md) přehledu třídy.

##  <a name="connecttemplate"></a>  COleTemplateServer::ConnectTemplate

Připojuje šablonu dokumentu, na které odkazuje *pDocTemplate* k podkladovým [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) objektu.

```
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>Parametry

*clsid*<br/>
Odkaz na ID třídy OLE, který požaduje šablony.

*pDocTemplate*<br/>
Ukazatel na dokument šablony.

*bMultiInstance*<br/>
Určuje, zda jednu instanci aplikace může podporovat víc instancí. Při hodnotě TRUE se více instancí aplikace jsou spouštěny pro každý požadavek na vytvoření objektu.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [klíč CLSID](/windows/desktop/com/clsid-key-hklm) v sadě Windows SDK.

##  <a name="unregister"></a>  COleTemplateServer::Unregister

Zruší registraci přidružený dokument šablony.

```
BOOL Unregister();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

EnterRemarks

##  <a name="updateregistry"></a>  COleTemplateServer::UpdateRegistry

Načte informace o souboru typu z řetězce šablony dokumentu a umístí tyto informace v systémovém registru OLE.

```
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parametry

*nAppType*<br/>
Hodnota z výčtu OLE_APPTYPE, která je definována v AFXDISP. H. Může mít některou z následujících hodnot:

- OAT_INPLACE_SERVER Server má plnou instalaci systému server uživatelského rozhraní.

- OAT_SERVER Server podporuje jenom vkládání.

- OAT_CONTAINER kontejner podporuje odkazy na vložené objekty.

- OAT_DISPATCH_OBJECT objekt `IDispatch`-podporuje.

- OAT_DOC_OBJECT_SERVER Server podporuje i vkládání a komponenta modelu objektu dokumentu.

*rglpszRegister*<br/>
Seznam položek, které zápisu do registru pouze v případě, že neexistují žádné položky.

*rglpszOverwrite*<br/>
Seznam položek, která jsou zapsána do registru bez ohledu na to, zda existují nějaké předchozí položky.

*bRegister*<br/>
Určuje, zda je třída má být zaregistrován. Pokud *bRegister* má hodnotu TRUE, třída je registrována s registrem systému. V opačném případě ji zruší registraci třídy.

### <a name="remarks"></a>Poznámky

Informace o registraci je načtena pomocí volání [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Podřetězce načíst jsou identifikované indexy `regFileTypeId`, `regFileTypeName`, a `fileNewName`, jak je popsáno v `GetDocString` odkazují na stránky.

Pokud `regFileTypeId` dílčí řetězec je prázdný nebo pokud volání `GetDocString` selže z jiného důvodu, tato funkce se nezdaří a informace o souboru není zadán v registru.

Informace v argumentech *rglpszRegister* a *rglpszOverwrite* jsou zapsána do registru pomocí volání [afxoleregisterserverclass –](application-control.md#afxoleregisterserverclass). Informace o výchozím nastavení, které se zaregistruje, když dva argumenty jsou NULL, je vhodný pro většinu aplikací. Informace o struktuře informace v těchto argumentech najdete v tématu `AfxOleRegisterServerClass`.

Další informace najdete v tématu [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC HIERSVR](../../visual-cpp-samples.md)<br/>
[COleObjectFactory – třída](../../mfc/reference/coleobjectfactory-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc – třída](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)
