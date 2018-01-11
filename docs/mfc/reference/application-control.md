---
title: "Řízení aplikace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros
dev_langs: C++
helpviewer_keywords: application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c055f5489c7b85f5f974256709451426b614db47
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="application-control"></a>Řízení aplikace
OLE vyžaduje významné kontrolu nad aplikací a jejich objekty. OLE systémové knihovny DLL musí být možné spustit a verze aplikace automaticky, koordinaci jejich produkční a úpravy objektů a tak dále. Funkce v tomto tématu splňovat tyto požadavky. Kromě volané systémem OLE knihovny DLL, musí tyto funkce někdy nazývá také aplikace. 
  
### <a name="application-control"></a>Řízení aplikace  
  
|||  
|-|-|  
|[Afxolecanexitapp –](#afxolecanexitapp)|Určuje, zda můžete ukončit aplikaci.|  
|[Afxolegetmessagefilter –](#afxolegetmessagefilter)|Načte aktuální filtr zpráv aplikace.|  
|[Afxolegetuserctrl –](#afxolegetuserctrl)|Načte aktuální příznak uživatelského ovládacího prvku.|  
|[Afxolesetuserctrl –](#afxolesetuserctrl)|Nastaví nebo vymaže příznak uživatelského ovládacího prvku.|  
|[Afxolelockapp –](#afxolelockapp)|Zvětší počet globální rozhraní framework počtu aktivních objektů v aplikaci.|  
|[Afxolelockcontrol –](#afxolelockcontrol)| Zamkne objektu pro vytváření tříd zadaný ovládacího prvku. |
|[Afxoleunlockapp –](#afxoleunlockapp)|Snižuje počet rozhraní framework počtu aktivních objektů v aplikaci.| 
|[Afxoleunlockcontrol –](#afxoleunlockcontrol)| Odemkne objektu pro vytváření tříd zadaný ovládacího prvku. |
|[Afxoleregisterserverclass –](#afxoleregisterserverclass)|Zaregistruje server v registru systému OLE.|  
|[Afxoleseteditmenu –](#afxoleseteditmenu)|Implementuje uživatelské rozhraní pro *typename* objektu příkazu.|  

  
##  <a name="afxolecanexitapp"></a>Afxolecanexitapp –  
 Určuje, zda můžete ukončit aplikaci.  
  
```   
BOOL AFXAPI AfxOleCanExitApp(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud aplikace můžete ukončit; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace by neměl skončí, pokud existují nevyřízené odkazy na jeho objektů. Globální funkce `AfxOleLockApp` a `AfxOleUnlockApp` zvýší a sníží, čítač odkazy na objekty aplikace. Aplikace by neměl ukončit, pokud je toto počítadlo nenulové hodnoty. Pokud je čítač nenulové, hlavní okno aplikace je skrytý (ne zničení), když uživatel vybere ze systému nabídky nebo ukončení v nabídce Soubor zavřete. Tato funkce volá framework **CFrameWnd::OnClose**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]  

## <a name="requirements"></a>Požadavky  
 **Záhlaví**: afxdisp.h 

##  <a name="afxolegetmessagefilter"></a>Afxolegetmessagefilter –  
 Načte aktuální filtr zpráv aplikace.  
  
```   
COleMessageFilter* AFXAPI AfxOleGetMessageFilter(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuální filtr zpráv.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce pro přístup k aktuální `COleMessageFilter`-odvozené objekt, stejně, jako by volání `AfxGetApp` pro přístup k aktuálnímu objektu aplikace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví**: afxwin.h 

##  <a name="afxolegetuserctrl"></a>Afxolegetuserctrl –  
 Načte aktuální příznak uživatelského ovládacího prvku.  
  
```   
BOOL AFXAPI AfxOleGetUserCtrl(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je uživatel v ovládacím prvku aplikace; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Uživatel je v ovládacím prvku aplikace, když uživatel explicitně otevřít nebo vytvořit nový dokument. Uživatel je také v ovládacím prvku Pokud aplikaci nebyl spuštěn OLE systémové knihovny DLL – jinými slovy, pokud uživatel spustí aplikaci s prostředí systému.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví**: afxdisp.h

##  <a name="afxolesetuserctrl"></a>Afxolesetuserctrl –  
 Nastaví nebo vymaže příznak uživatelský ovládací prvek, který je vysvětleno v referenční informace pro `AfxOleGetUserCtrl`.  
  
```  
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl); 
```  
  
### <a name="parameters"></a>Parametry  
 *bUserCtrl*  
 Určuje, zda příznak řízení uživatelských nastavení nebo vymazat.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto funkci po uživatel vytvoří nebo načtení dokumentu, ale není v případě, že dokument je načíst nebo vytvořena prostřednictvím nepřímé akce, jako načítání vložený objekt z kontejneru aplikace.  
  
 Volání této funkce, pokud jiné akce v aplikaci by měla umístění uživatele v ovládacím prvku aplikace.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví**: afxdisp.h

##  <a name="afxolelockapp"></a>Afxolelockapp –  
 Zvětší počet globální rozhraní framework počtu aktivních objektů v aplikaci.  
  
```   
void AFXAPI AfxOleLockApp(); 
```  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework udržuje počet objektů v aplikaci aktivní. `AfxOleLockApp` a `AfxOleUnlockApp` funkcí, v uvedeném pořadí, zvýší a sníží tento počet.  
  
 Když se uživatel pokusí o zavřete aplikaci, která má aktivní objekty – aplikace, pro kterou je tento počet aktivních objektů nenulové hodnoty – rozhraní skryje aplikace ze zobrazení uživatele místo úplné vypnutí. `AfxOleCanExitApp` Funkce určuje, zda můžete ukončit aplikaci.  
  
 Volání `AfxOleLockApp` z libovolného objektu, která vystavuje rozhraní OLE, pokud je žádoucí pro tento objekt zničení při nadále používány klientskou aplikaci. Také zavolat `AfxOleUnlockApp` v destruktoru objektu, který volá `AfxOleLockApp` v konstruktoru. Ve výchozím nastavení `COleDocument` (a odvozených třídách) automaticky zamknutí a odemknutí aplikace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví**: afxdisp.h

##  <a name="afxoleunlockapp"></a>Afxoleunlockapp –  
 Snižuje počet rozhraní framework aktivních objektů v aplikaci.  
  
```   
void AFXAPI AfxOleUnlockApp(); 
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu `AfxOleLockApp` Další informace.  
  
 Pokud počet aktivních objektů hodnota nula, **AfxOleOnReleaseAllObjects** je volána.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [afxolelockapp –](#afxolelockapp).  

### <a name="requirements"></a>Požadavky  
 **Záhlaví**: afxdisp.h  

 ## <a name="afxolelockcontrol"></a>AfxOleLockControl
Zamkne objektu pro vytváření tříd zadaný ovládacího prvku tak, aby zůstal dynamicky vytvořený data související s ovládacím prvkem v paměti.  
   
### <a name="syntax"></a>Syntaxe    
```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );  
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );  
```
### <a name="parameters"></a>Parametry  
 `clsid`  
 ID jedinečný třídy ovládacího prvku.  
  
 `lpszProgID`  
 Jedinečný Identifikátor programu ovládacího prvku.  
   
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekt factory třídy ovládacího prvku byla úspěšně uzamčena; jinak 0.  
   
### <a name="remarks"></a>Poznámky  
 To výrazně urychlit zobrazení ovládacích prvků. Například po vytvoření ovládacího prvku v dialogovém okně a uzamčení ovládacího prvku s `AfxOleLockControl`, není potřeba vytvářet a znovu kill pokaždé, když je dialogové okno zobrazí nebo zničeno. Pokud uživatel otevře a zavře dialogové okno opakovaně, uzamčení vaše ovládací prvky můžete výrazně zvýšit výkon. Až budete připravení odstranění ovládacího prvku, volání `AfxOleUnlockControl`.  
   
### <a name="example"></a>Příklad  
```cpp
// Starts and locks control's (Microsoft Calendar) class factory. 
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** < afxwin.h >  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [Afxoleunlockcontrol –](#afxoleunlockcontrol)
 
##  <a name="afxoleregisterserverclass"></a>Afxoleregisterserverclass –  
 Tato funkce umožňuje zaregistrovat server v registru systému OLE.  
  
```   
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,  
    LPCTSTR lpszClassName,  
    LPCTSTR lpszShortTypeName,  
    LPCTSTR lpszLongTypeName,  
    OLE_APPTYPE nAppType = OAT_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 Odkaz na ID serveru OLE třídy.  
  
 `lpszClassName`  
 Ukazatel na řetězec obsahující název třídy objektů serveru.  
  
 *lpszShortTypeName*  
 Ukazatel na řetězec, který obsahuje krátký název serveru typ objektu, například "Grafu."  
  
 *lpszLongTypeName*  
 Ukazatel na řetězec obsahující dlouhý název serveru typ objektu, například "Microsoft Excel 5.0 grafu."  
  
 `nAppType`  
 Hodnotu převzaty z **OLE_APPTYPE** výčtu zadání typu aplikace OLE. Možné hodnoty jsou následující:  
  
- `OAT_INPLACE_SERVER`Server má celého serveru uživatelského rozhraní.  
  
- `OAT_SERVER`Server podporuje jenom vkládání.  
  
- `OAT_CONTAINER`Kontejner podporuje odkazy na vložené části.  
  
- `OAT_DISPATCH_OBJECT``IDispatch`-podporující objektu.  
  
 `rglpszRegister`  
 Pole ukazatele na řetězce představující klíče a hodnoty, které mají být přidány do registru systému OLE, pokud se nenajdou žádné existující hodnoty pro klíče.  
  
 `rglpszOverwrite`  
 Pole ukazatele na řetězce představující klíče a hodnoty, které mají být přidány do systémového registru OLE, pokud obsahuje existující hodnoty pro danou klíče registru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je třída serveru úspěšně registrován; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Většina aplikací můžete použít **COleTemplateServer::Register** k registraci typů dokumentů aplikace. Pokud formát systémového registru vaší aplikace nevejde typický vzor, můžete použít `AfxOleRegisterServerClass` větší kontrolu.  
  
 Registr obsahuje sadu klíčů a hodnot. `rglpszRegister` a `rglpszOverwrite` argumenty pole ukazatele na řetězce, každý se skládá z klíče a jeho hodnota oddělená **NULL** znak ( `'\0'`). Každý z těchto řetězců může mít nahraditelné parametry, jejichž místech jsou označené nástrojem sekvence znaků `%1` prostřednictvím `%5`.  
  
 Symboly jsou vyplněna takto:  
  
|Symbol|Hodnota|  
|------------|-----------|  
|%1|ID třídy, naformátovaná jako řetězec|  
|%2|Název třídy|  
|%3|Cesta ke spustitelnému souboru|  
|%4|Zadejte krátký název|  
|%5|Název typu Long|  

### <a name="requirements"></a>Požadavky  
 **Záhlaví**: afxdisp.h

##  <a name="afxoleseteditmenu"></a>Afxoleseteditmenu –  
 Implementuje uživatelské rozhraní pro *typename* objektu příkazu.  
  
```   
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,  
    CMenu* pMenu,  
    UINT iMenuItem,  
    UINT nIDVerbMin,  
    UINT nIDVerbMax = 0,  
    UINT nIDConvert = 0); 
```  
  
### <a name="parameters"></a>Parametry  
 `pClient`  
 Ukazatel na položce OLE klienta.  
  
 `pMenu`  
 Ukazatel na nabídky objekt, který chcete aktualizovat.  
  
 *iMenuItem*  
 Index položky nabídky aktualizovat.  
  
 `nIDVerbMin`  
 ID příkazu, která odpovídá primární požadavek.  
  
 *nIDVerbMax*  
 ID příkazu, která odpovídá na poslední operaci.  
  
 *nIDConvert*  
 ID pro položku nabídky převést.  
  
### <a name="remarks"></a>Poznámky  
 Pokud server rozpoznal primární požadavek, se změní na položku nabídky "operaci *typename* objektu" a `nIDVerbMin` je odeslání příkazu, když uživatel vybere příkaz. Pokud server rozpoznal několik příkazů, pak se změní na položku nabídky " *typename* objektu" a podnabídky výpis všechny operace se zobrazí, když uživatel vybere příkaz. Když uživatel vybere operaci v podnabídce `nIDVerbMin` se odesílají, pokud je zvoleno první sloveso, `nIDVerbMin` + 1 je odeslán, pokud druhý příkaz je zvolená a tak dále. Výchozí hodnota `COleDocument` implementace automaticky zpracovává tuto funkci.  
  
 Následující příkaz, musíte mít ve skriptu prostředků aplikace vašeho klienta (. Soubor RC):  
  
 **#include \<afxolecl.rc >**  

### <a name="requirements"></a>Požadavky  
 **Záhlaví**: afxole.h 

## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)

## <a name="afxoleunlockcontrol"></a>Afxoleunlockcontrol –
Odemkne objektu pro vytváření tříd zadaný ovládacího prvku.  
   
### <a name="syntax"></a>Syntaxe  
  ```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );  
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );  
```
### <a name="parameters"></a>Parametry  
 `clsid`  
 ID jedinečný třídy ovládacího prvku.  
  
 `lpszProgID`  
 Jedinečný Identifikátor programu ovládacího prvku.  
   
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekt factory třídy ovládacího prvku byla úspěšně odemčena; jinak 0.  
   
### <a name="remarks"></a>Poznámky  
 Ovládací prvek je uzamčen s `AfxOleLockControl`tak, aby dynamicky vytvořený data související s ovládacím prvkem zůstane v paměti. To výrazně urychlit zobrazení ovládacího prvku protože ovládací prvek nemusí být vytvořen a zničen pokaždé, když se zobrazí. Až budete připravení odstranění ovládacího prvku, volání `AfxOleUnlockControl`.  
   
### <a name="example"></a>Příklad  
 ```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));

```
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** < afxwin.h >  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)  
 [Afxolelockcontrol –](#afxolelockcontrol)

