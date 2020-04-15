---
title: Třída CConnectionPoint
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
ms.openlocfilehash: ce72c156ab31b742a42d2960923fc56afff656c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369433"
---
# <a name="cconnectionpoint-class"></a>Třída CConnectionPoint

Definuje speciální typ rozhraní používaného ke komunikaci s jinými objekty OLE, nazývaný "spojovací bod".

## <a name="syntax"></a>Syntaxe

```
class CConnectionPoint : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|Vytvoří `CConnectionPoint` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CConnectionPoint::GetConnections](#getconnections)|Načte všechny spojovací body v mapě připojení.|
|[CConnectionPoint::GetContainer](#getcontainer)|Načte kontejner ovládacího prvku, který vlastní mapu připojení.|
|[CConnectionPoint::GetIID](#getiid)|Načte ID rozhraní spojovacího bodu.|
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Načte maximální počet spojovacích bodů podporovaných ovládacím prvkem.|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|Načte ukazatel na prvek připojení na *pos*.|
|[CConnectionPoint::GetStartPosition](#getstartposition)|Spustí iteraci mapy vrácením hodnoty POSITION, `GetNextConnection` která může být předána volání.|
|[CConnectionPoint::OnAdvise](#onadvise)|Volat rámci při navazování nebo přerušení připojení.|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Načte ukazatel na požadované rozhraní jímky.|

## <a name="remarks"></a>Poznámky

Na rozdíl od běžných rozhraní OLE, které se používají k implementaci a vystavení funkcí ovládacího prvku OLE, spojovací bod implementuje odchozí rozhraní, které je schopno zahájit akce na jiné objekty, jako je například spouštění událostí a oznámení o změně.

Připojení se skládá ze dvou částí: objekt volající rozhraní, volal "zdroj", a objekt implementující rozhraní, volal "jímky.". Vystavením spojovacíbod, zdroj umožňuje jímky navázat připojení k sobě. Prostřednictvím mechanismu spojovacího bodu zdrojový objekt získá ukazatel na implementaci jímky sadu členských funkcí. Například k požáru události implementované jímky, zdroj může volat příslušnou metodu implementace jímky.

Ve výchozím `COleControl`nastavení odvozené třídy implementuje dva body připojení: jeden pro události a jeden pro oznámení změny vlastností. Tato připojení se používají, respektive pro spuštění událostí a pro upozornění jímky (například kontejner ovládacího prvku) při změně hodnoty vlastnosti. Podpora je také k dispozici pro ovládací prvky OLE k implementaci dalších spojovacích bodů. Pro každý další bod připojení implementovaný ve vaší třídě řízení je nutné deklarovat "součást připojení", která implementuje bod připojení. Pokud implementujete jeden nebo více spojovacích bodů, musíte také deklarovat jednu "mapu připojení" ve třídě řízení.

Následující příklad ukazuje jednoduchou mapu připojení a `Sample` jeden bod připojení pro ovládací prvek OLE, který se skládá ze dvou fragmentů kódu: první část deklaruje mapu připojení a bod; druhý implementuje tuto mapu a bod. První fragment je vložen do deklarace třídy ovládacích tříd pod **chráněným** oddílem:

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

BEGIN_CONNECTION_PART a END_CONNECTION_PART makra deklarují vloženou třídu `XSampleConnPt` (odvozenou z) `CConnectionPoint`která implementuje tento konkrétní bod připojení. Pokud chcete přepsat všechny `CConnectionPoint` členské funkce nebo přidat vlastní členské funkce, deklarujte je mezi těmito dvěma makry. Například CONNECTION_IID makro přepíše `CConnectionPoint::GetIID` členskou funkci při umístění mezi těmito dvěma makry.

Druhý fragment kódu je vložen do souboru implementace (. CPP) vaší kontrolní třídy. Tento kód implementuje mapu připojení, která `SampleConnPt`obsahuje další spojovací bod:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

Po vložení těchto fragmentů kódu ukázkový ovládací prvek OLE zpřístupní spojovací bod pro `ISampleSink` rozhraní.

Spojovací body obvykle podporují "multicasting", což je možnost vysílání do více jímek připojených ke stejnému rozhraní. Následující fragment kódu ukazuje, jak provést vícesměrové vysílání iterace přes každý jímky na spojovací bod:

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

Tento příklad načte aktuální sadu `SampleConnPt` připojení v bodě `CConnectionPoint::GetConnections`připojení s voláním . Potom iterem prostřednictvím `ISampleSink::SinkFunc` připojení a volání na každé aktivní připojení.

Další informace o `CConnectionPoint`použití naleznete v článku [Spojovací body](../../mfc/connection-points.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>CConnectionPoint::CConnectionPoint

Vytvoří `CConnectionPoint` objekt.

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a>CConnectionPoint::GetConnections

Volánítéto funkce načíst všechna aktivní připojení pro spojovací bod.

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole aktivních připojení (jímky). Některé ukazatele v poli může být NULL. Každý ukazatel bez hodnoty NULL v tomto poli lze bezpečně převést na ukazatel na rozhraní jímky pomocí operátoru přetypování.

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a>CConnectionPoint::GetContainer

Volat rámci načíst `IConnectionPointContainer` pro spojovací bod.

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel na kontejner; jinak NULL.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle implementována BEGIN_CONNECTION_PART makro.

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a>CConnectionPoint::GetIID

Volat rámci načíst ID rozhraní spojovacího bodu.

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na ID rozhraní spojovacího bodu.

### <a name="remarks"></a>Poznámky

Přepište tuto funkci a vraťte ID rozhraní pro tento spojovací bod.

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>CConnectionPoint::GetMaxConnections

Volat rámci načíst maximální počet připojení podporovaných spojovací bod.

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet připojení podporovaných ovládacím prvkem nebo -1, pokud není žádné omezení.

### <a name="remarks"></a>Poznámky

Výchozí implementace vrátí -1, označující žádné omezení.

Přepsat tuto funkci, pokud chcete omezit počet jímky, které lze připojit k ovládacímu prvku.

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>CConnectionPoint::GetNextConnection

Načte ukazatel na prvek připojení na *pos*.

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Určuje odkaz na hodnotu POSITION vrácenou předchozím `GetNextConnection` voláním nebo voláním [GetStartPosition.](#getstartposition)

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek připojení určený *pos*nebo NULL.

### <a name="remarks"></a>Poznámky

Tato funkce je nejužitečnější pro iterace přes všechny prvky v mapě připojení. Při iterace přeskočte všechny nulls vrácené z této funkce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a>CConnectionPoint::GetStartPosition

Spustí iteraci mapy vrácením hodnoty POSITION, která může být předána volání [GetNextConnection.](#getnextconnection)

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, která označuje počáteční pozici pro itace mapy; nebo NULL, pokud je mapa prázdná.

### <a name="remarks"></a>Poznámky

Pořadí iterace není předvídatelné; proto "první prvek v mapě" nemá žádný zvláštní význam.

### <a name="example"></a>Příklad

  Viz příklad [cconnectionpointu::GetNextConnection](#getnextconnection).

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a>CConnectionPoint::OnAdvise

Volat rámci při navazování nebo přerušené připojení.

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>Parametry

*bPoradit*<br/>
TRUE, pokud je navázáno připojení; jinak FALSE.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovede žádné provádění.

Přepsat tuto funkci, pokud chcete oznámení při jímky připojit nebo odpojit od spojovacího bodu.

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>CConnectionPoint::QuerySinkInterface

Načte ukazatel na požadované rozhraní jímky.

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>Parametry

*pUnkSink*<br/>
Identifikátor rozhraní jímky, které jsou požadovány.

*ppRozhraní*<br/>
Ukazatel rozhraní označený *pUnkSink*. Pokud objekt nepodporuje toto \* rozhraní, *je ppInterface* nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
