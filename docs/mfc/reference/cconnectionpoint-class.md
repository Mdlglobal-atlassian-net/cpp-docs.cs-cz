---
title: Cconnectionpoint – třída
ms.date: 11/04/2016
f1_keywords:
- CConnectionPoint
- AFXDISP/CConnectionPoint
- AFXDISP/CConnectionPoint::CConnectionPoint
- AFXDISP/CConnectionPoint::GetConnections
- AFXDISP/CConnectionPoint::GetContainer
- AFXDISP/CConnectionPoint::GetIID
- AFXDISP/CConnectionPoint::GetMaxConnections
- AFXDISP/CConnectionPoint::GetNextConnection
- AFXDISP/CConnectionPoint::GetStartPosition
- AFXDISP/CConnectionPoint::OnAdvise
- AFXDISP/CConnectionPoint::QuerySinkInterface
helpviewer_keywords:
- CConnectionPoint [MFC], CConnectionPoint
- CConnectionPoint [MFC], GetConnections
- CConnectionPoint [MFC], GetContainer
- CConnectionPoint [MFC], GetIID
- CConnectionPoint [MFC], GetMaxConnections
- CConnectionPoint [MFC], GetNextConnection
- CConnectionPoint [MFC], GetStartPosition
- CConnectionPoint [MFC], OnAdvise
- CConnectionPoint [MFC], QuerySinkInterface
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
ms.openlocfilehash: efa8a7bf9e14bd93682fcc2d5802a84f1bdb1e96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629928"
---
# <a name="cconnectionpoint-class"></a>Cconnectionpoint – třída

Definuje speciální typ rozhraní, které slouží ke komunikaci s další objekty OLE, nazývaný "bod připojení".

## <a name="syntax"></a>Syntaxe

```
class CConnectionPoint : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|Vytvoří `CConnectionPoint` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CConnectionPoint::GetConnections](#getconnections)|Načte všechny spojovací body na mapě připojení.|
|[CConnectionPoint::GetContainer](#getcontainer)|Získá kontejner ovládacího prvku, který vlastní mapu připojení.|
|[CConnectionPoint::GetIID](#getiid)|Načte rozhraní ID bodu připojení.|
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Získá maximální počet bodů připojení ovládacím prvkem podporována.|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|Načte ukazatel na prvek připojení na *pos*.|
|[CConnectionPoint::GetStartPosition](#getstartposition)|Spuštění iterace mapování tak, že vrací hodnotu POZICI, která mohou být předány `GetNextConnection` volání.|
|[CConnectionPoint::OnAdvise](#onadvise)|Volá se rozhraním, když vytváří nebo přerušení připojení.|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Načte ukazatel na rozhraní požadovaný jímky.|

## <a name="remarks"></a>Poznámky

Na rozdíl od normální rozhraní OLE, které se používají k implementaci a vystavit funkčnost ovládacího prvku OLE, implementuje bod připojení odchozí rozhraní, které je možné spustit na jiných objektech, jako je například vyvolává události akcí a upozornění na změnu.

Připojení se skládá ze dvou částí: volání rozhraní s názvem "zdroj" a objekt implementující rozhraní, objekt nazývá "sink". Zveřejněním spojovací bod umožňuje zdroji jímky ke zřízení spojení sám na sebe. Zdrojový objekt prostřednictvím mechanismus bodu připojení získá ukazatel na implementaci jímky sadu členské funkce. Chcete-li vyvolat událost implementované jímka zdroji můžete volat, odpovídající metodu jímky implementace.

Ve výchozím nastavení `COleControl`-odvozená třída implementuje dvě spojovací body: jeden pro události a jeden pro vlastnost upozornění na změnu. Tato připojení se používají, v uvedeném pořadí, pro jeho události spuštění a pro jímku (například kontejneru ovládacího prvku) při oznamování hodnotu vlastnosti se změnila. Podpora se poskytuje také pro ovládací prvky OLE implementovat další spojovací body. Pro každý další spojovací bod implementována ve třídě ovládacího prvku je třeba deklarovat "připojení část", který implementuje bod připojení. Pokud se rozhodnete implementovat jeden nebo více bodů připojení, musíte také deklarovat jediného "mapy připojení" ve třídě ovládacího prvku.

Následující příklad ukazuje jednoduchý připojení mapy a jeden přípojný bod pro `Sample` ovládací prvek OLE, který se skládá z dva fragmenty kódu: první část deklaruje připojení mapy a bod; druhá implementuje toto mapování a bodu. První fragment je vložen do deklarace třídy ovládacího prvku, v části **chráněné** části:

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

Makra BEGIN_CONNECTION_PART a END_CONNECTION_PART deklarovat třídu vložený `XSampleConnPt` (odvozený od `CConnectionPoint`), který implementuje tento bod připojení. Pokud je zapotřebí přepsat některé `CConnectionPoint` členské funkce, nebo přidat vlastní členské funkce, je deklarovat mezi těmito dvěma makra. Příklad: přepsání CONNECTION_IID – makro `CConnectionPoint::GetIID` členské funkce při umístěny mezi těmito dvěma makra.

Druhý fragment kódu je vložen do implementace souboru (. CPP) třídy ovládacího prvku. Tento kód implementuje mapy připojení, která obsahuje další spojovací bod `SampleConnPt`:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

Jakmile tyto fragmenty kódu jste vložili, ovládacího prvku OLE ukázka poskytuje bod připojení pro `ISampleSink` rozhraní.

Obvykle spojovací body podporují "vícesměrové vysílání", což je možnost vysílání více připojené ke stejnému rozhraní jímky. Následující fragment kódu ukazuje, jak provádět vícesměrové vysílání podle iterace v rámci každé jímky najdete v bodě připojení:

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

Tento příklad načte aktuální sadu připojení na `SampleConnPt` spojovací bod voláním `CConnectionPoint::GetConnections`. Pak Iteruje přes připojení a volání `ISampleSink::SinkFunc` na každé aktivní připojení.

Další informace o používání `CConnectionPoint`, najdete v článku [spojovací body](../../mfc/connection-points.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

##  <a name="cconnectionpoint"></a>  CConnectionPoint::CConnectionPoint

Vytvoří `CConnectionPoint` objektu.

```
CConnectionPoint();
```

##  <a name="getconnections"></a>  CConnectionPoint::GetConnections

Voláním této funkce k načtení všech aktivních připojení pro bod připojení.

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na celou řadu aktivních připojení (jímky). Některé z ukazatele jako pole může mít hodnotu NULL. Každý NENULOVÝ ukazatel v tomto poli lze bezpečně převést na ukazatel na rozhraní stoku pomocí operátoru přetypování.

##  <a name="getcontainer"></a>  CConnectionPoint::GetContainer

Volá se rozhraním, aby načíst `IConnectionPointContainer` pro bod připojení.

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel na kontejneru; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle implementované BEGIN_CONNECTION_PART – makro.

##  <a name="getiid"></a>  CConnectionPoint::GetIID

Volá se rozhraním, aby se načetlo rozhraní ID bodu připojení.

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na ID bodu připojení rozhraní.

### <a name="remarks"></a>Poznámky

Přepsání této funkci vrátíte rozhraní ID pro tento bod připojení.

##  <a name="getmaxconnections"></a>  CConnectionPoint::GetMaxConnections

Volá se rozhraním, aby získal maximální počet připojení podporovaných bodem připojení.

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet připojení podporovaných ovládacího prvku nebo -1, pokud žádný limit.

### <a name="remarks"></a>Poznámky

Výchozí implementace vrací hodnotu -1, která bez omezení.

Tato funkce přepište, pokud chcete omezit počet jímky, které se můžete připojit k ovládacího prvku.

##  <a name="getnextconnection"></a>  CConnectionPoint::GetNextConnection

Načte ukazatel na prvek připojení na *pos*.

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Určuje referenci na POZICI hodnotu vrácenou předchozím `GetNextConnection` nebo [GetStartPosition](#getstartposition) volání.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek připojení určené *pos*, nebo má hodnotu NULL.

### <a name="remarks"></a>Poznámky

Tato funkce je zvláště užitečná pro procházení všech prvků v objektu map připojení. Během iterace, přeskočte všechny hodnoty Null vrácená touto funkcí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

##  <a name="getstartposition"></a>  CConnectionPoint::GetStartPosition

Spuštění iterace mapování tak, že vrací hodnotu POZICI, která mohou být předány [GetNextConnection](#getnextconnection) volání.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

POZICE určující počáteční pozice pro iterace v mapě. nebo hodnota NULL, pokud mapa je prázdný.

### <a name="remarks"></a>Poznámky

Iterace sekvence není předvídatelný; "první prvek v objektu map", proto nemá žádný speciální význam.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CConnectionPoint::GetNextConnection](#getnextconnection).

##  <a name="onadvise"></a>  CConnectionPoint::OnAdvise

Volá se rozhraním, když je vytvořeno nebo nefunkční.

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
Hodnota TRUE, pokud bude připojení navázáno; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Výchozí implementace nemá žádný účinek.

Tato funkce přepište, pokud chcete oznámení, když jímky připojení nebo odpojení z bodu připojení.

##  <a name="querysinkinterface"></a>  CConnectionPoint::QuerySinkInterface

Načte ukazatel na rozhraní požadovaný jímky.

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>Parametry

*pUnkSink*<br/>
Identifikátor rozhraní stoku žádá.

*ppInterface*<br/>
Ukazatel na ukazatel rozhraní, který je identifikován *pUnkSink*. Pokud objekt nepodporuje toto rozhraní \* *ppInterface* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

