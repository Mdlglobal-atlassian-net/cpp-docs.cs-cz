---
title: "Mapy připojení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros.maps
dev_langs: C++
helpviewer_keywords: connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 018f2f6c1cd57dc500d4161b02ccb5880a9889fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="connection-maps"></a>Mapy připojení
Ovládací prvky OLE dokážou vystavit rozhraní k ostatním aplikacím. Tato rozhraní pouze povolit přístup z kontejneru do ovládacího prvku. Pokud ovládací prvek OLE požaduje přístup k externí rozhraní jiných objektů OLE, je nutné vytvořit bod připojení. Tento spojovací bod umožňuje odchozí přístup k externí expediční mapy, jako je například mapy událostí nebo funkce oznámení ovládacího prvku.  
  
 Knihovny Microsoft Foundation Class nabízí programovací model, který podporuje spojovací body. V tomto modelu "připojení mapuje" se používá k určení rozhraní nebo body připojení pro ovládací prvek OLE. Mapy připojení obsahovat jeden makro pro každý bod připojení. Další informace o mapy připojení, najdete v článku [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) třídy.  
  
 Většinou ovládacího prvku se podporují jenom dvěma spojovacími body: jeden pro události a jeden pro vlastnost oznámení. Tyto jsou implementované `COleControl` základní třídy a vyžadovat další práci zapisovačem ovládacího prvku. Žádné další spojovací body, které chcete implementovat v třídě musí přidat ručně. K podpoře mapy připojení a bodů, MFC poskytuje následující makra:  
  
### <a name="connection-map-declaration-and-demarcation"></a>Připojení mapy deklarace a Rozhraničení  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_PART –](#begin_connection_part)|Deklaruje embedded třídu, která implementuje bod další připojení (musí používat v deklaraci třídy).|  
|[END_CONNECTION_PART –](#end_connection_part)|Ukončí deklaraci spojovací bod (musí používat v deklaraci třídy).|  
|[CONNECTION_IID –](#connection_iid)|Určuje ID rozhraní bodu připojení ovládacího prvku.|  
|[DECLARE_CONNECTION_MAP –](#declare_connection_map)|Deklaruje, že připojení mapu se použije v třídě (musí používat v deklaraci třídy).|  
|[BEGIN_CONNECTION_MAP –](#begin_connection_map)|Zahájí definici mapy připojení (musí používat v implementaci třídy).|  
|[END_CONNECTION_MAP –](#end_connection_map)|Ukončí definici mapy připojení (musí používat v implementaci třídy).|  
|[CONNECTION_PART –](#connection_part)|Určuje bod připojení v mapě připojení ovládacího prvku.|  
  
 Následující funkce pomáhá jímka při navazování a odpojení připojení pomocí spojovací body:  
  
### <a name="initializationtermination-of-connection-points"></a>Inicializace nebo ukončení body připojení  
  
|||  
|-|-|  
|[Afxconnectionadvise –](#afxconnectionadvise)|Naváže připojení mezi zdroj a jímka.|  
|[Afxconnectionunadvise –](#afxconnectionunadvise)|Dělí připojení mezi zdroj a jímka.|  
  
##  <a name="begin_connection_part"></a>BEGIN_CONNECTION_PART –  
 Použití `BEGIN_CONNECTION_PART` makro zahájíte definici další spojovací body nad rámec události a vlastnost oznámení spojovací body.  
  
```   
BEGIN_CONNECTION_PART(theClass, localClass)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Určuje, že je název třídy ovládacího prvku, jehož spojovací bod to.  
  
 *localClass*  
 Určuje název třídy místní, který implementuje spojovacího bodu.  
  
### <a name="remarks"></a>Poznámky  
 V souboru deklarace (.h), který definuje členské funkce pro třídu, počátečního bodu připojení s `BEGIN_CONNECTION_PART` makro, přidejte `CONNECTION_IID` makro a jiné členské funkce chcete implementovat a dokončete připojení bodu mapy pomocí `END_CONNECTION_PART` makro.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="end_connection_part"></a>END_CONNECTION_PART –  
 Ukončí deklaraci spojovacího bodu.  
  
```   
END_CONNECTION_PART(localClass)   
```  
  
### <a name="parameters"></a>Parametry  
 *localClass*  
 Určuje název třídy místní, který implementuje spojovacího bodu.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="connection_iid"></a>CONNECTION_IID –  
 Mezi použijte `BEGIN_CONNECTION_PART` a `END_CONNECTION_PART` makra zadat ID rozhraní pro bod připojení vaší OLE ovládacím prvkem podporována.  
  
```   
CONNECTION_IID(iid)   
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 ID rozhraní rozhraní volat pomocí bodu připojení.  
  
### <a name="remarks"></a>Poznámky  
 `iid` Argument je rozhraní ID sloužící k identifikaci rozhraní, které je spojovací bod zavolá na jeho připojené jímky. Příklad:  
  
 [!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]  
  
 Určuje spojovací bod, který volá `ISinkInterface` rozhraní.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="declare_connection_map"></a>DECLARE_CONNECTION_MAP –  
 Každý `COleControl`-odvozené třídy v programu můžete zadat mapu připojení k určení dalších spojovací body, které podporuje vlastní ovládací prvek.  
  
```   
DECLARE_CONNECTION_MAP() 
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše řízení podporuje další body, použijte `DECLARE_CONNECTION_MAP` makro na konci deklarace třídy. Potom v souboru sada, která definuje členské funkce pro třídu, použijte `BEGIN_CONNECTION_MAP` makro, `CONNECTION_PART` makra pro každý bod připojení ovládacího prvku a `END_CONNECTION_MAP` makro deklarovat konec mapy připojení.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="begin_connection_map"></a>BEGIN_CONNECTION_MAP –  
 Každý `COleControl`-odvozené třídy v programu můžete zadat mapu připojení k určení spojovací body, které budou podporovat vlastního ovládacího prvku.  
  
```   
BEGIN_CONNECTION_MAP(theClass, theBase)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Určuje, že je název třídy ovládacího prvku, jejichž připojení mapování těchto.  
  
 *theBase*  
 Určuje název základní třídu `theClass`.  
  
### <a name="remarks"></a>Poznámky  
 K implementaci (. Soubor CPP), který definuje členské funkce pro třídu, spusťte mapa připojení s `BEGIN_CONNECTION_MAP` makro, pak přidat makro položky pro každý bodů připojení pomocí [connection_part –](#connection_part) – makro. Nakonec dokončete mapa připojení s [end_connection_map –](#end_connection_map) makro.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="end_connection_map"></a>END_CONNECTION_MAP –  
 Ukončí definici mapy připojení.  
  
```   
END_CONNECTION_MAP()  
```  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="connection_part"></a>CONNECTION_PART –  
 Bod připojení pro ovládací prvek OLE se mapuje na ID konkrétní rozhraní.  
  
```   
CONNECTION_PART(theClass, iid, localClass)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Určuje, že je název třídy ovládacího prvku, jehož spojovací bod to.  
  
 `iid`  
 ID rozhraní rozhraní volat pomocí bodu připojení.  
  
 *localClass*  
 Určuje název třídy místní, který implementuje spojovacího bodu.  
  
### <a name="remarks"></a>Poznámky  
 Příklad:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]  
  
 implementuje připojení mapy, se spojovacím bodem, který volá `IID_ISinkInterface` rozhraní.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="afxconnectionadvise"></a>Afxconnectionadvise –  
 Volání této funkce k navázání připojení mezi zdroji, zadán pomocí `pUnkSrc`a jímka, určeného `pUnkSink`.  
  
```   
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD FAR* pdwCookie);
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkSrc`  
 Ukazatel na objekt, který volá rozhraní.  
  
 `pUnkSink`  
 Ukazatel na objekt, který implementuje rozhraní.  
  
 `iid`  
 Rozhraní ID připojení.  
  
 `bRefCount`  
 **Hodnota TRUE,** označuje, že vytváření připojení by způsobit počet odkazů `pUnkSink` k se zvýší. **FALSE** označuje, že by neměl se zvýší počet odkazů.  
  
 `pdwCookie`  
 Ukazatel na `DWORD` kde vrací identifikátor připojení. Tato hodnota mají být předány jako `dwCookie` parametru `AfxConnectionUnadvise` při odpojení připojení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo vytvořeno připojení; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h 

##  <a name="afxconnectionunadvise"></a>Afxconnectionunadvise –  
 Volání této funkce přerušit spojení mezi zdroji, zadán pomocí `pUnkSrc`a jímka, určeného `pUnkSink`.  
  
```   
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD dwCookie); 
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkSrc`  
 Ukazatel na objekt, který volá rozhraní.  
  
 `pUnkSink`  
 Ukazatel na objekt, který implementuje rozhraní.  
  
 `iid`  
 ID rozhraní bod připojení rozhraní.  
  
 `bRefCount`  
 **Hodnota TRUE,** označuje, že odpojení připojení by způsobit počet odkazů `pUnkSink` být odečte. **FALSE** označuje, že by neměl být odečte počet odkazů.  
  
 `dwCookie`  
 Identifikátor připojení vrácený `AfxConnectionAdvise`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo ukončeno připojení; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h 

## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
