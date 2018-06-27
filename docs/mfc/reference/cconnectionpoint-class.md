---
title: Třída CConnectionPoint | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d892ea225e3b1c1089447587eb808e56370bbb69
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952219"
---
# <a name="cconnectionpoint-class"></a>CConnectionPoint – třída
Definuje speciální typ rozhraní používaný ke komunikaci s jinými objekty OLE, označovaný jako "bod připojení".  
  
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
|[CConnectionPoint::GetConnections](#getconnections)|Načte všechny body připojení v mapě připojení.|  
|[CConnectionPoint::GetContainer](#getcontainer)|Načte kontejneru ovládacího prvku, který vlastní mapy připojení.|  
|[CConnectionPoint::GetIID](#getiid)|Načte ID rozhraní bod připojení.|  
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Načte maximální počet bodů připojení ovládacím prvkem podporována.|  
|[CConnectionPoint::GetNextConnection](#getnextconnection)|Načte ukazatel element připojení v *pos*.|  
|[CConnectionPoint::GetStartPosition](#getstartposition)|Spuštění mapy iterace vrácením **pozice** hodnotu, která se dá předat do `GetNextConnection` volání.|  
|[CConnectionPoint::OnAdvise](#onadvise)|Voláno rámcem při vytvoření nebo porušením připojení.|  
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Načte ukazatel na požadovaný podřízený rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Na rozdíl od normální rozhraní OLE, které se používají k implementaci a vystavit funkcionalitu ovládacího prvku OLE, implementuje bod připojení odchozí rozhraní, které je možné zahájit akce na jiné objekty, například na aktivaci události a upozornění na změnu.  
  
 Připojení se skládá ze dvou částí: objekt volání rozhraní s názvem "zdroj" a objekt implementující rozhraní nazývá "podřízený". Díky zpřístupnění spojovací bod, umožňuje zdroj jímky ke zřízení spojení sama na sebe. Zdrojový objekt přes mechanismus bodu připojení, získá ukazatel na implementaci podřízený sadu členské funkce. Aktivovat událost implementované jímky, můžete v zdroji voláním vhodný způsob provádění jímky.  
  
 Ve výchozím nastavení `COleControl`-odvozená třída implementuje dvěma spojovacími body: jeden pro události a jeden pro vlastnost upozornění na změnu. Tato připojení používají, respektive pro spouštění událostí a upozornění podřízený (například kontejneru ovládacího prvku), pokud hodnotu vlastnosti se změnila. Podpora je k dispozici také pro ovládací prvky OLE implementovat další spojovací body. Pro každý další připojení bod implementována ve třídě ovládacího prvku je potřeba deklarovat "připojení část", který implementuje spojovacího bodu. Pokud budete implementovat jednu nebo více bodů připojení, musíte taky deklarovat jedné "připojení mapy" ve třídě ovládacího prvku.  
  
 Následující příklad ukazuje jednoduchý připojení mapy a jeden spojovací bod pro `Sample` OLE ovládací prvek, který se skládá z dva fragmenty kódu: první část deklaruje mapy připojení a bod; druhý implementuje tento mapy a bodu. První fragment se vloží do deklaraci třídy ovládacího prvku v části `protected` části:  
  
 [!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]  
  
 Begin_connection_part – a end_connection_part – makra deklarovat třídu embedded `XSampleConnPt` (odvozený z `CConnectionPoint`), která implementuje tuto konkrétní spojovacího bodu. Pokud chcete přepsat všechny `CConnectionPoint` členské funkce, nebo přidat členské funkce vlastní, deklarovat je mezi těmito dvěma makra. Příklad: přepsání connection_iid – makro `CConnectionPoint::GetIID` – členská funkce, když je umístěná mezi těmito dvěma makra.  
  
 Druhý fragment kódu je vložen do souboru implementace (. CPP) třídy ovládacího prvku. Tento kód implementuje mapy připojení, která obsahuje další spojovací bod, `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]  
  
 Po vložení tyto fragmenty kódu prvek OLE ukázka poskytuje bod připojení pro `ISampleSink` rozhraní.  
  
 Body připojení většinou podporují "vícesměrového vysílání", což je schopnost všesměrové vysílání pro více jímky připojené ke stejnému rozhraní. Následující fragment kódu ukazuje, jak provést vícesměrového vysílání pomocí iterace každý podřízený ve spojovacím bodě:  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
 Tento příklad načte aktuální sadu připojení na `SampleConnPt` spojovací bod pomocí volání `CConnectionPoint::GetConnections`. Ji pak iteruje v rámci připojení a volání `ISampleSink::SinkFunc` na všechny aktivní připojení.  
  
 Další informace o používání `CConnectionPoint`, najdete v článku [spojovací body](../../mfc/connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
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
 Volání této funkce pro načtení všech aktivních připojení pro bod připojení.  
  
```  
const CPtrArray* GetConnections();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na pole aktivních připojení (jímky). Některé z následující ukazatele v poli, může mít hodnotu NULL. Každý ukazatel jinou hodnotu než NULL v toto pole může bezpečně převeden na ukazatel na rozhraní podřízený pomocí operátor přetypování.  
  
##  <a name="getcontainer"></a>  CConnectionPoint::GetContainer  
 Voláno rámcem načíst **IConnectionPointContainer** pro spojovacího bodu.  
  
```  
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného ukazatel na kontejneru; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je obvykle implementované begin_connection_part – makro.  
  
##  <a name="getiid"></a>  CConnectionPoint::GetIID  
 Voláno rámcem načíst ID rozhraní spojovacího bodu.  
  
```  
virtual REFIID GetIID() = 0;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na ID spojovací bod rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkci vrátíte rozhraní ID pro tento bod připojení.  
  
##  <a name="getmaxconnections"></a>  CConnectionPoint::GetMaxConnections  
 Voláno rámcem načíst maximální počet připojení, které jsou podporované pomocí bodu připojení.  
  
```  
virtual int GetMaxConnections();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální počet připojení nepodporuje ovládací prvek nebo -1, pokud není nijak omezena.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace vrátí hodnotu -1, označující není nijak omezena.  
  
 Tato funkce přepsání, pokud chcete omezit počet jímky, které se můžou připojit k vaší kontrole.  
  
##  <a name="getnextconnection"></a>  CConnectionPoint::GetNextConnection  
 Načte ukazatel element připojení v *pos*.  
  
```  
LPUNKNOWN GetNextConnection(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Určuje odkaz na **pozice** hodnoty vrácené předchozí `GetNextConnection` nebo [GetStartPosition](#getstartposition) volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na element připojení určeného *pos*, nebo má hodnotu NULL.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je nejvhodnější pro iterace v rámci všechny elementy v mapě připojení. Během iterace, přeskočte všechny hodnoty Null vrácená této funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
##  <a name="getstartposition"></a>  CConnectionPoint::GetStartPosition  
 Spuštění mapy iterace vrácením **pozice** hodnotu, která se dá předat do [GetNextConnection](#getnextconnection) volání.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která určuje počáteční pozici pro iterace mapování, nebo **NULL** Pokud mapy je prázdný.  
  
### <a name="remarks"></a>Poznámky  
 Iterace pořadí není předvídatelný; "první prvek v mapě" má proto žádné zvláštní význam.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CConnectionPoint::GetNextConnection](#getnextconnection).  
  
##  <a name="onadvise"></a>  CConnectionPoint::OnAdvise  
 Voláno rámcem při připojení je právě navázat nebo poškozený.  
  
```  
virtual void OnAdvise(BOOL bAdvise);
```  
  
### <a name="parameters"></a>Parametry  
 *bAdvise*  
 **Hodnota TRUE,**, pokud je připojení navázáno; jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace neprovede žádnou akci.  
  
 Tato funkce přepsání, pokud chcete oznámení, když jímky připojení nebo odpojení ze spojovacího bodu.  
  
##  <a name="querysinkinterface"></a>  CConnectionPoint::QuerySinkInterface  
 Načte ukazatel na požadovaný podřízený rozhraní.  
  
```  
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,  
    void** ppInterface);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkSink*  
 Identifikátor rozhraní podřízený požadováno.  
  
 *ppInterface*  
 Ukazatel na ukazatel rozhraní identifikovaný *pUnkSink*. Pokud objekt nepodporuje toto rozhraní \* *ppInterface* je nastaven na **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)

