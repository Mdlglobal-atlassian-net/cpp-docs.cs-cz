---
title: Řízení aplikací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b06302d330ec8677a3de9b3ccaebf0b7b237b0e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053888"
---
# <a name="application-control"></a>Řízení aplikace

OLE vyžaduje podstatné kontrolu nad aplikacemi a objekty. OLE systémové knihovny DLL musí být možné spouštět a vydávejte verze aplikací automaticky, koordinovat jejich výrobu a úpravy objektů a tak dále. Funkce v tomto tématu splňovat tyto požadavky. Kromě volané OLE systémové knihovny DLL, tyto funkce musí být říká se jim také aplikace.

### <a name="application-control"></a>Řízení aplikace

|||
|-|-|
|[Afxolecanexitapp –](#afxolecanexitapp)|Určuje, zda lze ukončit aplikaci.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Načte aktuální filtr zpráv aplikace.|
|[Afxolegetuserctrl –](#afxolegetuserctrl)|Načte aktuální příznak uživatelského ovládacího prvku.|
|[Afxolesetuserctrl –](#afxolesetuserctrl)|Nastaví nebo vymaže příznak uživatelského ovládacího prvku.|
|[AfxOleLockApp](#afxolelockapp)|Zvýší počet globální v rámci počtu aktivních objektů v aplikaci.|
|[Afxolelockcontrol –](#afxolelockcontrol)| Zamkne objekt pro vytváření tříd zadaného prvku. |
|[Funkci AfxOleUnlockApp](#afxoleunlockapp)|Sníží počet rozhraní framework, které se počet aktivních objektů v aplikaci.|
|[Afxoleunlockcontrol –](#afxoleunlockcontrol)| Odemkne objekt pro vytváření tříd zadaného prvku. |
|[Afxoleregisterserverclass –](#afxoleregisterserverclass)|Zaregistruje server v registru systému OLE.|
|[Afxoleseteditmenu –](#afxoleseteditmenu)|Implementuje uživatelské rozhraní pro *typename* objekt příkazu.|

##  <a name="afxolecanexitapp"></a>  Afxolecanexitapp –

Určuje, zda lze ukončit aplikaci.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud můžete ukončit aplikace; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace by neměl ukončit, pokud existují zbývajících odkazů na objekty. Globální funkce `AfxOleLockApp` a `AfxOleUnlockApp` zvýší a sníží, čítač odkazů na objekty aplikaci. Aplikace by neměl ukončit, když tento čítač je nenulové. Pokud je čítač nenulovou hodnotu, když uživatel vybere zavření ze systémové nabídky nebo ukončit v nabídce Soubor je skrytý (nejsou zničeny) hlavního okna aplikace. Rozhraní volá tuto funkci `CFrameWnd::OnClose`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Požadavky

**Hlavička**: afxdisp.h

##  <a name="afxolegetmessagefilter"></a>  AfxOleGetMessageFilter

Načte aktuální filtr zpráv aplikace.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální filtr zpráv.

### <a name="remarks"></a>Poznámky

Voláním této funkce pro přístup k aktuálním `COleMessageFilter`-odvozenému objektu, stejně jako by volání `AfxGetApp` pro přístup k aktuálnímu objektu aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Požadavky

**Hlavička**: afxwin.h

##  <a name="afxolegetuserctrl"></a>  Afxolegetuserctrl –

Načte aktuální příznak uživatelského ovládacího prvku.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je uživatel v ovládacím prvku aplikace; jinak 0.

### <a name="remarks"></a>Poznámky

Uživatel je v ovládacím prvku aplikace, když uživatel explicitně otevřít nebo vytvořit nový dokument. Uživatel je také v ovládacím prvku v případě, že se aplikace spustí OLE systémové knihovny DLL – jinými slovy, pokud uživatel spustí aplikaci k prostředí systému.

### <a name="requirements"></a>Požadavky

**Hlavička**: afxdisp.h

##  <a name="afxolesetuserctrl"></a>  Afxolesetuserctrl –

Nastaví nebo vymaže příznak uživatelský ovládací prvek, který je vysvětlen v referenční dokumentaci pro `AfxOleGetUserCtrl`.

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Parametry

*bUserCtrl*<br/>
Určuje, zda je uživatelský ovládací prvek příznak nastavení nebo vymazat.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci Pokud uživatel vytvoří nebo načte dokument, ale ne v případě, že dokument je načtení nebo vytvoření prostřednictvím nepřímé akce, jako je načítání vloženého objektu z aplikace typu kontejner.

Voláním této funkce, když se další akce v aplikaci by měl uživatel v ovládacím prvku aplikace.

### <a name="requirements"></a>Požadavky

**Hlavička**: afxdisp.h

##  <a name="afxolelockapp"></a>  AfxOleLockApp

Zvýší počet globální v rámci počtu aktivních objektů v aplikaci.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Poznámky

Rozhraní framework udržuje počet objektů v aplikace aktivní. `AfxOleLockApp` a `AfxOleUnlockApp` funkce, v uvedeném pořadí, zvýší a sníží počet.

Když se uživatel pokusí o zavřít aplikaci, která má aktivní objekty – aplikaci, pro kterou je nenulový počet aktivních objektů, které – skryje rozhraní framework aplikace z pohledu uživatele místo úplné vypnutí. `AfxOleCanExitApp` Funkce určuje, zda lze ukončit aplikaci.

Volání `AfxOleLockApp` z libovolného objektu, který zpřístupňuje rozhraní OLE, pokud by nežádoucí pro daný objekt, který se má zničit stále používán klientské aplikace. Také volat `AfxOleUnlockApp` v destruktoru objektu, který volá `AfxOleLockApp` v konstruktoru. Ve výchozím nastavení `COleDocument` (a odvozené třídy) automaticky zamknutí a odemknutí aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Požadavky

**Hlavička**: afxdisp.h

##  <a name="afxoleunlockapp"></a>  Funkci AfxOleUnlockApp

Sníží počet rozhraní framework aktivních objektů v aplikaci.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Poznámky

Zobrazit `AfxOleLockApp` pro další informace.

Když počet objektů služby active dosáhne nuly, `AfxOleOnReleaseAllObjects` je volána.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [AfxOleLockApp](#afxolelockapp).

### <a name="requirements"></a>Požadavky

**Hlavička**: afxdisp.h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Zamkne objekt pro vytváření tříd zadaného ovládacího prvku tak, aby dynamicky generovaný přidružený k ovládacímu prvku data zůstanou v paměti.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parametry

*identifikátor CLSID*<br/>
Třída jedinečné ID ovládacího prvku.

*lpszProgID*<br/>
Jedinečný Identifikátor programu ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt pro vytváření tříd ovládacího prvku byla úspěšně uzamčena; jinak 0.

### <a name="remarks"></a>Poznámky

To může výrazně urychlit zobrazení ovládacích prvků. Například po vytvoření ovládacího prvku v dialogovém okně a uzamknout ovládací prvek s `AfxOleLockControl`, není potřeba vytvářet a ukončit znovu pokaždé, když v dialogovém okně je zobrazen nebo zničení. Pokud uživatel otevře a zavře dialogové okno opakovaně, uzamykání ovládacích prvků můžete výrazně zvýšit výkon. Až budete připravení ke zničení ovládacího prvku, volání `AfxOleUnlockControl`.

### <a name="example"></a>Příklad

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

### <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[Afxoleunlockcontrol –](#afxoleunlockcontrol)

##  <a name="afxoleregisterserverclass"></a>  Afxoleregisterserverclass –

Tato funkce umožňuje registraci serveru v registru systému OLE.

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

*identifikátor CLSID*<br/>
Odkaz na ID serveru OLE – třídy.

*lpszClassName*<br/>
Ukazatel na řetězec obsahující název třídy objektů serveru.

*lpszShortTypeName*<br/>
Ukazatel na řetězec, který obsahuje krátký název serveru typu objektu, například"."

*lpszLongTypeName*<br/>
Ukazatel na řetězec, který obsahuje dlouhý název typ objektu serveru, jako je například "Microsoft Excel 5.0 grafu."

*nAppType*<br/>
Hodnota z výčtu OLE_APPTYPE určení typu aplikace OLE. Možné hodnoty jsou následující:

- OAT_INPLACE_SERVER Server má plnou instalaci systému server uživatelského rozhraní.

- OAT_SERVER Server podporuje jenom vkládání.

- OAT_CONTAINER kontejner podporuje odkazy na vložené části.

- OAT_DISPATCH_OBJECT `IDispatch`-podporující objektu.

*rglpszRegister*<br/>
Pole ukazatelů na řetězce představující klíče a hodnoty, které mají být přidány do systémového registru OLE, pokud se nenajdou žádné existující hodnoty pro klíče.

*rglpszOverwrite*<br/>
Pole ukazatelů na řetězce představující klíče a hodnoty, které mají být přidány do systémového registru OLE, pokud obsahuje existující hodnoty pro daný klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud třída serveru je úspěšně zaregistrovaný; jinak 0.

### <a name="remarks"></a>Poznámky

Většina aplikací můžete použít `COleTemplateServer::Register` k registraci typů dokumentů aplikace. Pokud formát registru systému vaší aplikace se nevejde typický vzor, můžete použít `AfxOleRegisterServerClass` větší kontrolu.

V registru se skládá ze sady klíčů a hodnot. *RglpszRegister* a *rglpszOverwrite* argumenty jsou pole z ukazatele na řetězce, který se skládá z klíč a hodnotu oddělených **NULL** znak ( `'\0'`). Každý z těchto řetězců může mít nahraditelné parametry, jejichž místa jsou označené nástrojem znakové sekvence *%1* prostřednictvím *%5*.

Symboly jsou vyplněna následujícím způsobem:

|Symbol|Hodnota|
|------------|-----------|
|%1|ID třídy naformátovaná jako řetězec|
|%2|Název třídy|
|%3|Cesta ke spustitelnému souboru|
|%4|Zadejte krátký název|
|%5|Název typu Long|

### <a name="requirements"></a>Požadavky

**Hlavička**: afxdisp.h

##  <a name="afxoleseteditmenu"></a>  Afxoleseteditmenu –

Implementuje uživatelské rozhraní pro *typename* objekt příkazu.

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

*pClient*<br/>
Ukazatel na klienta položky OLE.

*pMenu*<br/>
Ukazatel na objekt nabídky, který chcete aktualizovat.

*iMenuItem*<br/>
Index položky nabídky aktualizace.

*nIDVerbMin*<br/>
ID příkazu, který odpovídá primární požadavek.

*nIDVerbMax*<br/>
ID příkazu, který odpovídá na poslední operaci.

*nIDConvert*<br/>
ID pro položku nabídky Convert.

### <a name="remarks"></a>Poznámky

Pokud server rozpozná pouze primární požadavek, položka nabídky stane "příkaz *typename* objektu" a *nIDVerbMin* příkazu se odešle, když uživatel vybere příkaz. Pokud server rozpoznal několik operací, a potom položku nabídky stane " *typename* objektu" a podnabídky výpis všechny akce se zobrazí, když uživatel vybere příkaz. Když uživatel vybere příkaz v podnabídce *nIDVerbMin* se odešle, pokud je vybrána první příkaz, *nIDVerbMin* + 1 se odešle, pokud je druhý příkaz zvolené a tak dále. Výchozí hodnota `COleDocument` implementace automaticky zpracovává tuto funkci.

Musíte mít následující příkaz ve skriptu prostředků aplikace vašeho klienta (. Soubor RC):

**#include \<afxolecl.rc >**

### <a name="requirements"></a>Požadavky

**Hlavička**: afxole.h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)

## <a name="afxoleunlockcontrol"></a> Afxoleunlockcontrol –

Odemkne objekt pro vytváření tříd zadaného prvku.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parametry

*identifikátor CLSID*<br/>
Třída jedinečné ID ovládacího prvku.

*lpszProgID*<br/>
Jedinečný Identifikátor programu ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt pro vytváření tříd ovládacího prvku se úspěšně odemkla; jinak 0.

### <a name="remarks"></a>Poznámky

Ovládací prvek je uzamčen s `AfxOleLockControl`tak, aby dynamicky generovaný přidružený k ovládacímu prvku data zůstanou v paměti. To může výrazně urychlit zobrazení ovládacího prvku vzhledem k tomu, že nemusí být vytvořeno a zničeno při pokaždé, když se zobrazí ovládací prvek. Až budete připravení ke zničení ovládacího prvku, volání `AfxOleUnlockControl`.

### <a name="example"></a>Příklad

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));

```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

### <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[Afxolelockcontrol –](#afxolelockcontrol)

